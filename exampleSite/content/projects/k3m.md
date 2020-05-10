+++
date = "2020-05-10"
title = "k3m"
slug = "k3m"
+++

Simplicity of k3s and the speed of multipass, brings you k3m

<img width="992" alt="image" src="https://user-images.githubusercontent.com/567298/81488380-3c0d9a80-9268-11ea-93b7-9b2e5b5b6c13.png">

## About

I really like [Multipass](https://multipass.run) from Canonical and [k3s](https://github.com/rancher/k3s) from Rancher and wanted a one-liner to combine the two together, so that I have a kubernetes development environment running on multipass.

Rancher already makes it so easy to run k3s on its own, and **so many amazing community-developed tools** such as [k3d](https://github.com/rancher/k3d), [kind](https://github.com/kubernetes-sigs/kind), [k3sup](https://github.com/alexellis/k3sup) (and the list goes on) that makes it super easy to get a environment up and running.

But since I use multipass heavily, I wanted to create k3m.

## What does it do?

Get a k3s cluster on multipass with:

```
$ curl -sfL get.k3m.run | bash
```
```
$ export KUBECONFIG=~/.k3m/kubeconfig
$ kubectl get nodes -o wide
NAME   STATUS   ROLES    AGE   VERSION        INTERNAL-IP     EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
k3m    Ready    master   29s   v1.17.4+k3s1   192.168.64.15   <none>        Ubuntu 18.04.4 LTS   4.15.0-99-generic   containerd://1.3.3-k3s2
```

## More info

More info can be found on [github.com/ruanbekker/k3m](https://github.com/ruanbekker/k3m)
