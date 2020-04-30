---
layout: post
title:  "Powershell Printer Woes"
date:   2020-04-28 20:00:00 +0930
categories: [work, powershell]
---
Recently at work I was tasked to add printers from our print server to a VM using Powershell. Seems simple right? Well, it should be! I assumed that I'd just need to pass `-Credentials` to `Add-Printer` or something similar to that. Much to my surprise I couldn't do that, and therefore I searched for a different way to go about my task.