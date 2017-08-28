---
layout: post
title: VSphere client unable to connect to MKS.
date: 2017-08-28 10:15:00 +0800
---

# Problem
I was attempting to login to a windows VM via vsphere client. However, it reported one error. The message is *Unable to connect to MKS*.

# Fix
Power off the virtual machine. Remove from inventory and Re-add it then power on.