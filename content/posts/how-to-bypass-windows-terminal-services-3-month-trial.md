---
title: 'How to bypass Windows Terminal Services 3 month trial'
date: 2005-06-06T19:18:00.000-07:00
draft: false
url: /2005/06/how-to-bypass-windows-terminal-services.html
tags: 
- Ubuntu
---

HOW TO RESET WINDOWS TERMINAL SERVICES 3 MONTH TRIAL  
Warning: greyhat content.  
  
Thanks to a Microsoft article, I've found out that it is very easy to extend your Windows Terminal Services 3-month trial or experience time. It's so easy that I'm sure many administrators have done this in their own systems, while waiting for their managers or financial staff to buy the definitive licenses (not being hypocrite here).  
  
Following these instructions, you don't have to crack Windows Terminal Services. You won't mess with your system. The magic is to only delete the licenses databases both in the server and the clients, and let windows re-create them for you.  
  
  
\----  
  
Make sure you've installed "Terminal Services Licensing". By the way, this method only makes sense if you need to use Terminal Services in Application Mode, which is the one that requires licensing.  
  
The idea is quite simple.  
  
First, disconnect all users from the terminal. If you need to do this remotely, you can also disconnect yourself, and access the files remotely.  
  
Go to %WINDIR%\\system32\\lserver  
  
Notice the file TSLIC.edb. Rename it to tslic.old  
  
In every client computer, remove the CAL TS registry keys, located at:  
  
HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSLicensing  
  
Restart your server.  
  
  
Finally, if you need more information about how to crack terminal services, [go check at Microsoft's web site.](http://support.microsoft.com/?id=839878) See the "Cause 2" steps. :-)  
  
Shouldn't MS improve the security for TS Licensing in the next versions of Windows (2003 with SP1 is also easy to "crack")?  
  
PS> I am definitely against software piracy. I strongly believe that Microsoft should strength their anti-piracy policy. Only then they could theoretically lower their licensing prices. The biggest result, though, would be a huge increase of free software popularity. Only then we, FOSS proponents, would have the opportunity to prove our paradigm is superior (now I'm being hypocrite, I guess).
# Archived Comments

#### _Original comment from: Anonymous_ "By the...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2005-07-26T16:58:00.000-07:00">Jul 3, 2005</time>

_Original comment from: Anonymous_  
  
"By the way, this method only makes sense if you need to use Terminal Services in Application Mode, which is the one that requires licensing."  
  
Dude, there's only one terminal services installation now, on windows 2003. You no longer have the choice of app or admin. Duh!
<hr />
#### "Dude", at least you recognized that's windows 200...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2005-07-26T18:01:00.000-07:00">Jul 3, 2005</time>

"Dude", at least you recognized that's windows 2003 specific.  
  
In windows 2000, you do have that coice. "Duh!"
<hr />
#### Realmente nao consegui encontrar tal aqruivo. Sera...
[kawik](https://www.blogger.com/profile/10971700741046734422 "noreply@blogger.com") - <time datetime="2009-01-14T12:21:00.000-08:00">Jan 3, 2009</time>

Realmente nao consegui encontrar tal aqruivo. Sera q \[e hein? Se puder me ajudar, agradeco!
<hr />
