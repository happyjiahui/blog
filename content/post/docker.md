---
title: "Docker 常用命令"
date: 2019-12-02T11:02:40+08:00
draft: false
tags: ["docker", "linux"]
---
```shell
sudo docker run -d -p 9000:9000 -p 8000:8000 --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
```

## 列出容器

```shell
docker ps -a
```

## 重启容器

```shelll
sudo docker restart 容器id
```

## 进入bash

```shell
docker exec -it 容器id /bin/sh
```
