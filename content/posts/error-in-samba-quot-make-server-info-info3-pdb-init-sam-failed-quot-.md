---
title: 'Error in samba: &quot;make_server_info_info3: pdb_init_sam failed!&quot;'
date: 2005-11-01T02:23:00.000-08:00
draft: false
url: /2005/11/error-in-samba-pdbinitsam-failed.html
tags: 
- Ubuntu
---

"**make\_server\_info\_info3: pdb\_init\_sam failed!**"  
  
If this error is appearing in your logs when trying to authenticate samba users to Active Directory with winbind, change your /etc/nsswitch.conf:  
  
passwd: files winbind  
group: files winbind