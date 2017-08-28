---
layout: post
title: Windows Docker Slave unusable (Low disk space)
date: 2017-08-28 10:00:00 +0800
---

```
Agent WindowsDockerSlave-1

Disk space is too low. Only 0.938GB left on C:\Jenkins.

Connected via JNLP agent.
```


http://btburnett.com/2017/03/remove-untagged-images-from-docker-for-windows.html


Here’s a quick note for Docker for Windows users. This is based on Jim Hoskin’s post Remove Untagged Images From Docker. (http://jimhoskins.com/2013/07/27/remove-untagged-docker-images.html)

I’ve simply reformatted his two scripts for use on Docker for Windows via Powershell. To delete all stopped containers:

```
docker ps -a -q | % { docker rm $_ }
```
To delete all untagged local images:

```
docker images | ConvertFrom-String | where {$_.P2 -eq "<none>"} | % { docker rmi $_.P3 }
```