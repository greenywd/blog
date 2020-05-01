---
layout: post
title:  "Powershell Printer Woes"
date:   2020-04-28 20:00:00 +0930
categories: [work, powershell]
---
Recently at work I was tasked to add printers from our print server to a VM using Powershell, without any user interaction. Seems simple right? Well, it should be! I assumed that I'd just need to pass `-Credentials` to `Add-Printer` or something similar to that. Much to my surprise I couldn't do that, and therefore I searched for a different way to go about my task. Unforuntately, I couldn't find anything on the internet that would help me, or at least point me in the right direction.

Some Googling led me to the discovery of `net use`, which can be used to "[connect to and disconnect from a network resource][ms-net-use]". You can use this command to connect to a network printer, however it maps the printer to an LPT port and doesn't show in the Control Panel/Windows 10 GUI (which is required for users). In the same [StackExchange][se-net-use] post, a user suggested using [Rundll32 printui.dll,PrintUIEntry][printuientry-doc] which I'm sure would work, if credentials didn't have to be provided.

Luckily, it wasn't back to square one. As the `net use` documentation says, a username and password can be passed which gave me an idea. `net use` creates a connection to a network resource (in my case, a printer) but despite the printer not showing, the connection is still made (verified with `net use` with no arguments). What if we could somehow create a printer visible in the Windows GUI that uses the connection we just made?

Fortunately, the solution I came up with was better than just that. I found out through sheer trial and error that after using `net use` with a username and password to create the connection to the printer located on the print server, Powershell's `Add-Printer` would work with little to no issue. The only issue that I've found sometimes occurs is when `Add-Printer` fails, but often works on subsequent tries. 

[ms-net-use]: https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/gg651155(v=ws.11)
[se-net-use]: https://serverfault.com/questions/339135/how-does-net-use-work-in-windows-7-for-printer-connection
[printuientry-doc]: http://technet.microsoft.com/en-us/library/ee624057%28WS.10%29.aspx