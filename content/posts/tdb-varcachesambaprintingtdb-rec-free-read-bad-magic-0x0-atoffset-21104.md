---
title: 'tdb(/var/cache/samba/printing.tdb): rec_free_read bad magic 0x0 at
offset=21104'
date: 2005-06-15T13:47:00.000-07:00
draft: false
url: /2005/06/tdbvarcachesambaprintingtdb-recfreeread.html
tags: 
- Ubuntu
---

\[2005/06/15 20:33:36, 0\] tdb/tdbutil.c:tdb\_log(531) tdb(/var/cache/samba/printing.tdb): rec\_free\_read bad magic 0x0 at offset=21104  
  
If you find something like this in your logs, and you can't print, just remove the file and restart samba.  
  
Visit my sponsors if you find this information and their ads useful hehe.
