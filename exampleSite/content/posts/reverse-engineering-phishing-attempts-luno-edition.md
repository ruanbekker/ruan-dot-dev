+++
date = "2021-09-08"
title = "Reverse Engineering Phishing Attempts - LUNO Edition"
slug = "reverse-engineering-phishing-attempts-luno-edition"
tags = [
    "phishing",
    "security",
    "luno"
]
categories = [
    "security",
]
series = ["security"]
featured_image = "https://ruan.dev/images/new-post-ruan-dev.png"
+++

In this post I will demonstrate how I **reversed engineered a phishing attempt** from a SMS pretending to be [LUNO](https://luno.com) and trying to steal my personal details, inspecting the SMS, under a controlled environment, inspect the fake website and **see what they are trying to accomplish** in order for us to learn what the risks are and how to avoid them.

## The Suspicious Text Message

So I received a phishing attempt via SMS, pretending to be LUNO (twice), with their hopes, of making me update my account details:

![image](https://user-images.githubusercontent.com/567298/132591811-fedc2a2c-1321-4792-8950-40489e96bf67.png)

## What is Phishing

[Phishing](https://en.wikipedia.org/wiki/Phishing) is a social engineering attack to steal your personal data, pretending to be someone that they are not.

So reading this message, is similar to some stranger knocking on your door, asking you for your online banking details, because someone "from the bank" said they will freeze your account if you don't update it via them. But let me explain. 

## About the SMS

So what this text message is trying to tell me, is that I should click on that link and update my Luno account.

So let's back up one step, step 1. **NEVER** follow any emails or sms messages instructing you to change or update or login to your account to make changes.

## Legal Pages at LUNO

If we head over to Luno's legal section of their website and browse to their [Avoid having your account compromised](https://www.luno.com/en/legal/safe) page, you will see that they mention that **you should never follow SMS messages** (as one example) to "update your account, as this is a phishing attack where you are being tricked into a attempt of the attackers trying to steal your personal information, in order to gain access to your account":

<img width="935" alt="image" src="https://user-images.githubusercontent.com/567298/132592360-e9ea2956-8f9a-423a-9aff-0e454dff6103.png">

## Red Flags on the SMS

So let's review this SMS message and try and point out the red flags:

![image](https://user-images.githubusercontent.com/567298/132591811-fedc2a2c-1321-4792-8950-40489e96bf67.png)

1. A lot of websites can't stress enough that they will never ask you to update your details. If you are unsure, logon to the website directly and look for notices.
2. The link: bitly is a url shortener that anyone can use, which hides the original url, as for Luno, their website is https://luno.com. 
3. Sense of urgency / steps to action: This is how a lot of people are tricked, they want you to feel that you must take action, as you can see `to avoid deactivation ... if not updated`
4. I've removed the number, but usually with emails you can inspect where the email comes from. With marketing messages, a lot of businesses use random numbers, and this might be where they think that people will assume its from a automated system (my opinion)

## Reverse Engineering their Process

So let's decipher this message and see where this link is taking us and what are they trying to accomplish, we know by now this is a **phishing attack**. I cannot stress this enough, do not click on unknown links, as your information about your source IP and browser are also captured.

But for this demonstration, I am using a environment without leaking our source address, we can try and figure out what they are trying to do, essentially using a virtual desktop via a VPN.

Let's start with the link, I have used a VPN connection to hide my source address, and making a curl request with following the location flag, to see what the shortened URL translates us to:

```
$ curl -IL https://bit.ly/3xxxxzt
HTTP/2 301
server: nginx
date: Wed, 08 Sep 2021 22:28:44 GMT
content-type: text/html; charset=utf-8
content-length: 118
cache-control: private, max-age=90
content-security-policy: referrer always;
location: https://hxxxxxxxxxxxxxxt.org/2915/LUNO/
referrer-policy: unsafe-url
via: 1.1 google
alt-svc: clear
```

So we can see that when we go to `https://bit.ly/3xxxxzt` it redirects the request the the target URL, which is `location: https://hxxxxxxxxxxxxxxt.org/2915/LUNO/`, and not `https://luno.com`.

Note: I've added the `x's` intentionally as I don't want people to click on the links.

## Inspecting the fake website

So I was curious to know how this website looks like and what they are trying to do, so I used a project [dorowu/ubuntu-desktop-lxde-vnc](https://hub.docker.com/r/dorowu/ubuntu-desktop-lxde-vnc/) for accessing a desktop environment accessible via vnc in your browser which runs on a container, and the reason for container requirement, is that I can use it in conjunction with the [dperson/openvpn-client](https://hub.docker.com/r/dperson/openvpn-client) container so that I can use the openvpn container's network for this desktop container, so that my traffic is masqueraded behind the VPN.

If you would like to skip the technical details, you can skip the following part.

This is the `docker-compose.yml` for having a linux desktop in the browser behind a VPN:

```yaml
version: "3.8"

services:
  vpn:
    container_name: vpn
    image: dperson/openvpn-client:latest
    cap_add:
      - net_admin
    sysctls:
      - net.ipv6.conf.all.disable_ipv6=0
    restart: unless-stopped
    volumes:
      - /dev/net:/dev/net:z # tun device
      - ./desktop-vpn/config:/vpn 
    tmpfs:
      - /run
      - /tmp
    security_opt:
      - label:disable
    dns:
      - 1.1.1.1
    ports:
      - 6080:80
    command: '-f "" -r 192.168.0.0/24' # enables fw and routes local traffic
    healthcheck:
      test: ["CMD", "curl", "-Ss", "ifconfig.co"]
      interval: 300s
      timeout: 15s

  desktop:
    container_name: desktop
    image: dorowu/ubuntu-desktop-lxde-vnc
    restart: unless-stopped
    network_mode: service:vpn
    environment:
      - USER=${DESKTOP_USER}
      - PASSWORD=${DESKTOP_PASSWORD}
      - HTTP_PASSWORD=${DESKTOP_HTTP_PASSWORD}
    volumes:
      - /dev/shm:/dev/shm
```

Booting the services above, and accessing our desktop to verify that we are running behind a VPN:

![image](https://user-images.githubusercontent.com/567298/132595555-b9da0304-2a07-4ffc-94ff-7b193d85a681.png)

As we can see we are being routed via Netherlands, which is the same OpenVPN config that I am using.

## Inspecting the Website

After entering the unsafe URL into my container browser, we can see that we are being prompted with a login, so we know that the attacker wants to capture our account information, as we can see except for the URL, it looks very similar to LUNO's website:

![image](https://user-images.githubusercontent.com/567298/132595836-02b239f0-980f-48ef-99a1-2b538d7b8b58.png)

After inspecting the elements of the login form:

![image](https://user-images.githubusercontent.com/567298/132596021-3b9cd85f-8180-4cd8-a363-f2f7597f4c90.png)

we can see that theres a php file on their server called `ver1.php`, and what the html is showing us, is that its capturing the following fields:

* email address
* password
* mobile number

And when you click "Next" it will submit those form fields to their `ver1.php` file, assuming that its a server side script, that captures those fields and stores them to a database, and perhaps notifies them that someone submitted the form (assuming - as we don't have access to that file)

So let's fill some dummy data into the form:

![image](https://user-images.githubusercontent.com/567298/132596392-2d658523-9d5e-4a29-b3d5-c706a3aaf4dd.png)

After we submitted the form data and we inspect the network tab on the right, we can see that a POST request was being made (meaning, submitting data to the server) to the `ver1.php` file and the scary part is, that we can see the form data was sent to them in plain text:

![image](https://user-images.githubusercontent.com/567298/132596787-4c3e45e5-0fcd-474c-a51f-47c9af8092c0.png)

So now they have:

* email: `adamjones@localhost.net`
* password: `Ab00000000`
* contact: `+27000000000`

Which is dummy data that I generated until it met their acceptance criteria.

## What does this mean for us

The even more scarier part is that they prompt you for your Multi Factor Authentication (MFA/2FA) pin, so if you have MFA associated to your LUNO account (which you should), only you have access to this pin that is being generated. So let's take a scenario where you open up your MFA device, and enter this pin into this form, and press submit. This essentially means, that they now have your sign in details as well as your MFA pin (which only lasts for 15-30 seconds.

So taken the fact that **they have the details** mentioned above, in near-realtime, **they can use the captured information**, and use that to **sign into your account**, then they **change your password**, or even worse, **transfer all your funds** as an example.

## In Summary

Always ignore and delete messages telling you to "do this or else", "update account settings", or anything that instructs you to click on unknown links or let you use your confidential information on unknown sites. Always make sure you read and understand the security tips of the websites you register to.

## Thank You

Thanks for reading, if you like my content, check out my **[website](https://ruan.dev)** or follow me at **[@ruanbekker](https://twitter.com/ruanbekker)** on Twitter.
