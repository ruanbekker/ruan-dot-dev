+++
date = "2021-07-14"
title = "Speed up Maven Docker builds with Cache"
slug = "speed-up-maven-docker-builds-with-cache"
tags = [
    "docker",
    "java",
    "maven",
    "performance"
]
categories = [
    "ext-blog-posts",
]
series = ["ext-blog-posts"]
featured_image = "https://ruan.dev/images/new-post-ruan-dev.png"
+++

A blog post has been published on [containers.fan](https://containers.fan)

## Caching with Docker

I've run into a issue where maven based docker builds takes quite some time due to maven requires to pull down the dependencies during each build, and in the post below, I demonstrate how I use buildkit to cache the `~/.m2` directory inside the container to reduce builds from 220s to 8s.

To read more, check out this post:
- https://containers.fan/posts/speed-up-maven-docker-builds-with-cache/

## Thank You

Thanks for reading, if you like my content, check out my **[website](https://ruan.dev)** or follow me at **[@ruanbekker](https://twitter.com/ruanbekker)** on Twitter.
