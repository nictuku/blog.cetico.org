---
title: 'python subprocess.Popen - instant (unbuffered) command output'
date: 2007-02-22T17:26:00.000-08:00
draft: false
url: /2007/02/python-subprocesspopen-instant.html
tags: 
- Tech Tip
---

Did you ever wanted to know how to call a process from Python and get the output instantly, instead of waiting for the execution to finish?  
  
Try this:  

> import os  
> import sys  
> import subprocess  
>   
> s = subprocess.Popen(\["tail", "/tmp/wee", "-f"\],  
> stdout=subprocess.PIPE,  
> stderr=subprocess.STDOUT)  
> follow = s.stdout  
> while s.poll() == None:  
> mess = follow.readline()  
> if mess:  
> print mess.strip()  
>   
> ret = s.wait()  
> sys.exit(0)

  
Now go ahead and type in another terminal: echo PRINTME >> /tmp/wee  
  
And then go weeee!
# Archived Comments

#### _Comment from [...](http://cetico.org/tech)_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-03-25T19:07:00.000-07:00">Mar 1, 2007</time>

_Comment from [Teste](http://cetico.org/tech):_  
  
Testando.
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-05-07T16:23:00.000-07:00">May 2, 2007</time>

_Comment from [Colin Walters](http://cgwalters.livejournal.com):_  
  
I dug into this problem and it turns out that Python's internal implementation of the readlines() iteration has an internal 8192 character buffer, even if you specify unbuffered I/O.  
  
So yeah, the fix to do unbuffered line reading in Python is:  
  
def readlines\_unbuffered(stream):  
line = stream.readline()  
while line:  
yield line  
line = stream.readline()
<hr />
#### _Comment from Tal Einat:_ It's worth n...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-07-19T10:18:00.000-07:00">Jul 4, 2007</time>

_Comment from Tal Einat:_  
  
It's worth noting that for some programs, the output may be buffered internally, so the above won't avoid all buffering.  
  
For example, C's stdio library doesn't buffer output when it is started from a tty (a terminal), but does buffer otherwise. In this specific case, you can avoid buffering by fooling the process into thinking it was run in a terminal using pexpect (doesn't work on windows).  
  
This post has more details:  
http://groups.google.com/group/comp.lang.python/tree/browse\_frm/thread/8abcc616d0ce419d/4981ae9dd98f9166?rnum=1&\_done=%2Fgroup%2Fcomp.lang.python%2Fbrowse\_frm%2Fthread%2F8abcc616d0ce419d%2F4981ae9dd98f9166%3F#doc\_82e72b4babce0c7a
<hr />
