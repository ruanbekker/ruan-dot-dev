+++
date = "2020-12-23"
title = "Notes #02"
slug = "notes-02"
tags = [
    "notes",
    "vagrant",
    "terraform",
    "ssh",
    "kvm",
    "docker",
    "aws",
    "promtail",
    "devops",
    "kubernetes",
    "drone",
    "loki",
    "ansible"
]
categories = [
    "notes",
]
series = ["notes"]
featured_image = "https://user-images.githubusercontent.com/30043398/94394485-bed2bb80-015d-11eb-827e-74d536f0bf1d.png"
+++

I'm quite curious so I do a lot of research and end up making a lot of notes with lots of useful resources. So this space is used to save all of them for future references, and hopefully get traffic directed to the authors content.

## My Favorite Post

I really enjoyed this post from lambda.grofers.com :

- [Learnings From Two Years of Kubernetes in Production](https://lambda.grofers.com/learnings-from-two-years-of-kubernetes-in-production-b0ec21aa2814)

## My Blog Posts

- [Using the Local-exec Provisioner With Terraform](https://blog.ruanbekker.com/blog/2020/09/27/using-the-local-exec-provisioner-with-terraform/)
- [Setup a KVM Host for Virtualization on OneProvider](https://blog.ruanbekker.com/blog/2020/10/07/setup-a-kvm-host-for-virtualization-on-oneprovider/)
- [Using the Libvirt Provisioner With Terraform for KVM](https://blog.ruanbekker.com/blog/2020/10/08/using-the-libvirt-provisioner-with-terraform-for-kvm/)
- [Basic Ping Role With Ansible in a Playbook](https://blog.ruanbekker.com/blog/2020/10/23/basic-ping-role-with-ansible-in-a-playbook/)
- [Use a SSH Jump Host With Ansible](https://blog.ruanbekker.com/blog/2020/10/26/use-a-ssh-jump-host-with-ansible/)
- [Easy Ad-Hoc VPNs With Sshuttle](https://blog.ruanbekker.com/blog/2020/10/26/easy-ad-hoc-vpns-with-sshuttle/)
- [Upload Public SSH Keys Using Ansible](https://blog.ruanbekker.com/blog/2020/10/26/upload-public-ssh-keys-using-ansible/)
- [Running Loki Behind Nginx Reverse Proxy](https://blog.ruanbekker.com/blog/2020/10/29/running-loki-behind-nginx-reverse-proxy/)
- [Running SSH Commands on AWS EC2 Instances With Python](https://blog.ruanbekker.com/blog/2020/11/02/running-ssh-commands-on-aws-ec2-instances-with-python/)
- [Sending Slack Messages With Python](https://blog.ruanbekker.com/blog/2020/11/06/sending-slack-messages-with-python/)
- [How to Setup Alerting With Loki](https://blog.ruanbekker.com/blog/2020/11/06/how-to-setup-alerting-with-loki/)
- [Deploy Loki on Multipass](https://blog.ruanbekker.com/blog/2020/11/11/deploy-loki-on-multipass/)
- [Encrypt and Decrypt Files With Ccrypt](https://blog.ruanbekker.com/blog/2020/11/20/encrypt-and-decrypt-files-with-ccrypt/)
- [Harden Your SSH Security on Linux Servers](https://blog.ruanbekker.com/blog/2020/12/18/harden-your-ssh-security-on-linux-servers/)
- [HTTPS for Local Development With MiniCA](https://blog.ruanbekker.com/blog/2020/12/23/https-for-local-development-with-minica/)
- [Reduce Docker Log Size on Disk](https://blog.ruanbekker.com/blog/2020/12/23/reduce-docker-log-size-on-disk/)

## Curated Content

The curated content from the posts I stumbled upon from August to December 2020:

### Ansible

- [Upload SSH Keys](https://www.cyberciti.biz/faq/how-to-upload-ssh-public-key-to-as-authorized_key-using-ansible/)
- [Ansible Cheatsheet](https://medium.com/edureka/ansible-cheat-sheet-guide-5fe615ad65c0)
- [Setup AWS Dynamic Inventory](https://devopscube.com/setup-ansible-aws-dynamic-inventory/)
- [Deploying Docker Compose Applications With Ansible and GitHub Actions](https://medium.com/swlh/deploying-docker-compose-applications-with-ansible-and-github-actions-7f1740392507)
- [Using Ansible with Github Actions](https://misfra.me/2019/10/using-ansible-with-github-actions/)

### DevOps

- [The Right Way to DevOps with Terraform and Ansible](https://www.cloudjourney.io/articles/devops/the_right_way_to_devops_with_terraform_and_ansible_su/)

### Docker

- [Docker SSH](https://hub.docker.com/r/jeroenpeeters/docker-ssh/)
- [Wetty](https://github.com/butlerx/wetty) + [Wetty Blog Post](https://pacroy.medium.com/setup-web-terminal-using-wetty-docker-image-dcb1ea75bfaf)
- [Docker, Traefik, mkcert and Wordpress](https://www.armandphilippot.com/docker-compose-traefik-wordpress/)
- [Letsencrypt for Local Development](https://github.com/zaherg/letsencrypt-for-local-development)
- [Docker Homelab: @cbirkenbeul](https://github.com/cbirkenbeul/docker-homelab)

### Golang

- [Deploy Golang on Docker](https://semaphoreci.com/community/tutorials/how-to-deploy-a-go-web-application-with-docker)
- [Using Go Modules](https://blog.golang.org/using-go-modules)
- [Learn Go with Tests](https://github.com/quii/learn-go-with-tests/blob/master/README.md)

### Kubernetes:

- [Learnings From Two Years of Kubernetes in Production](https://lambda.grofers.com/learnings-from-two-years-of-kubernetes-in-production-b0ec21aa2814)
- [NFS Provisioner with Kubernetes](https://opensource.com/article/20/6/kubernetes-nfs-client-provisioning)
- [Kubernetes Secrets](https://www.magalix.com/blog/kubernetes-secrets-101)
- [Serverless on Kubernetes using Fission](https://medium.com/@andrew_18142/serverless-on-kubernetes-93dd40b6bbb6)
- [CICD on Kubernetes with Drone and Go](https://medium.com/leboncoin-engineering-blog/ci-cd-with-drone-kubernetes-and-helm-part-2-cd8e3e3d30da)
- [Virtualization API for Kubernetes](https://kubevirt.io/)
- [Kubernetes 101 with Jeff Geerling](https://kube101.jeffgeerling.com/)
- [Logging in Kubernetes with Loki and the PLG Stack](https://codersociety.com/blog/articles/loki-kubernetes-logging)
- [How to Setup a CICD Pipeline in Kubernetes](https://dzone.com/articles/blog-how-to-setup-a-cicd-pipeline-with-kubernetes)
- [Install and Configure Traefik with Helm](https://traefik.io/blog/install-and-configure-traefik-with-helm/?utm_campaign=ContainerooPost&utm_content=141819331&utm_medium=social&utm_source=linkedin&hss_channel=lcp-17887475)


### Monitoring and Alerting

- [Alerta with Prometheus](https://github.com/alerta/prometheus-config)
- [Custom Notifications with Alertmanager Webhook Receiver in Kubernetes](https://medium.com/@zhimin.wen/custom-notifications-with-alert-managers-webhook-receiver-in-kubernetes-8e1152ba2c31)
- [Slack Notifications in Alertmanager](https://infinityworks.com/insights/slack-prometheus-alertmanager/)
- [Continue Routes in Alertmanager](https://stackoverflow.com/a/62725594)
- [Statping Status Page](https://github.com/statping/statping)
- [Use Loki 2.0 as a Alert Source](https://www.scylladb.com/2020/11/11/using-grafana-loki-2-0-as-an-alert-source/)
- [RabbitMQ Monitoring on Kubernetes](https://piotrminkowski.com/2020/09/29/rabbitmq-monitoring-on-kubernetes/)
- [Log Monitoring and Alerting with Grafana Loki](https://www.infracloud.io/blogs/grafana-loki-log-monitoring-alerting/)

### New Tooling

- [Continuous Profiling with conprof](https://github.com/conprof/conprof)
- [Host your HTML for one hour](https://hosthtml.live/)
- [k0s - Kubernetes](https://github.com/k0sproject/k0s)
- [ISP Checker - Blame your ISP with Evidence](https://github.com/fmdlc/ISP-Checker)

### Nginx

- [Nginx: Route based on country code using GeoIP](https://gist.github.com/kmjones1979/fcabb4731bbf85b9c50189e90d76b1c1)

### Productivity

- [JazzAndRain.com | Background Music](http://jazzandrain.com/)
- [Noises.online | Background Sounds](https://noises.online/)

### Terraform

- [Create a Dynamic ECS Cluster with Terraform](https://medium.com/javascript-in-plain-english/how-to-create-a-dynamic-ecs-cluster-with-terraform-86d6b11d0db9)

### Waypoint

- [Waypoint: Will it replace your CICD Pipeline](https://tekanaid.com/posts/hashicorp-waypoint-will-it-replace-your-ci-cd/)

## More Info

You will find all my tech blogs under [projects](https://ruan.dev/projects/#blogging). As some of you may know, I am super passionate helping others and if you need assistance or just want to chat head over to [support](https://ruan.dev/projects/#community-support) and chat to me on slack.

## Thank You

Thank you, say hi on [Twitter: @ruanbekker](https://twitter.com/ruanbekker) and until next time. Cheers! 
