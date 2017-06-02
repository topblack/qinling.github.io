---
layout: post
title: Build a windows docker image with chocolatey installed
date: 2017-06-02 11:47:00 +0800
---

https://chocolatey.org/

# Overview
Package management solutions for windows.

# Installation (with Powershell)
1. Set-ExecutionPolicy Allsigned
- Or Set-ExecutionPolicy Bypass
2. iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

*Refer to https://chocolatey.org/docs/uninstallation for uninstallation.*

# Find the packages
https://chocolatey.org/packages

# Samples
*After the installation, the environment variable is not effective immediately. use refreshenv command.*
## Windows SDK for Windows 7 and .NET Framework 4
choco install -y windows-sdk-7.1
## JDK8
choco install -y jdk8
## Git
choco install -y git

# Issues
## Could not be resolved: 'chocolatey.org'
This happens when I tried to install choco in a windows docker container by following the official instruction (with cmd).

https://github.com/Microsoft/Virtualization-Documentation/issues/318

Fixed this issue by setting the DNS server address

```
RUN @powershell -NoProfile -ExecutionPolicy Bypass -Command "Set-DNSClientServerAddress -interfaceindex 16 -ServerAddresses ('165.88.73.215', '165.88.73.10', '8.8.8.8')"
```

### Find out interfaceindex
```
Get-DNSClientServerAddress
```

### Find out DNS addresses
#### Windows
ipconfig /all
#### Linux
cat /etc/resolv.conf

### Building docker images with Choco
Within a docker container, it seems interfaceindex keeps change. I have no idea now about how it is generated.
So using the interfacealias with wildcard, because the alias of the interface is not the same in every container.
```
Set-DNSClientServerAddress vEthernet* -ServerAddresses ('165.88.73.215', '165.88.73.10', '8.8.8.8')
```

And unfortunately, in writing Dockfile, for each step using choco, the DNS should be set again. Because the DNS settings will not be persisted in the images.

https://github.com/moby/moby/issues/25537

A sample dockerfile below.

```
FROM microsoft/windowsservercore

RUN @powershell -NoProfile -ExecutionPolicy Bypass -Command "Set-DNSClientServerAddress vEthernet* -ServerAddresses ('8.8.8.8'); iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
RUN @powershell Set-DNSClientServerAddress vEthernet* -ServerAddresses ('8.8.8.8'); choco install -y git 
```