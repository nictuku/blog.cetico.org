---
title: 'Python + Eclipse in Ubuntu'
date: 2005-11-25T01:58:00.000-08:00
draft: false
url: /2005/11/python-eclipse-in-ubuntu.html
tags: 
- Ubuntu
---

Upgrade to at least Ubuntu 5.10 (Breezy), then  
  
\# apt-get install java-gcj-compat eclipse-pde-gcj eclipse-jdt-gcj  
Then, based on the [PyDev FAQ](http://pydev.sourceforge.net/faq.html):  
  
  

> \* Run eclipse, **as root for the first time to install PyDEV: sudo eclispe  
> \* Set default workspace where you want it.  
> \* Close Welcome splash pane.  
> \* Select Resource perspective: Window\\Open Perspective\\Other...\\Select Perspective\\Resource.  
> \* Click OK.  
> \* Select Window\\Preferences\\PyDev\\Interpreter - Python.  
> \* Click top New... button and enter Python path, e.g., /usr/bin/python24  
> \* Click OK.  
> \* Click File\\New\\Project...  
> \* Select Simple\\Project Wizard  
> \* Click Next.  
> \* Enter Project Name, e.g. SimpleProj1.  
> \* Click Finish.  
> \* Click File\\New...\\File.  
> \* Enter File Name, e.g. Py1.py.  
> \* Click Finish.  
> \* Right-click SimpleProj1 in Navigator pane and select Properties.  
> \* Click PyDev-PYTHONPATH.  
> \* Click top pane "Add source folder" button.  
> \* /SimpleProj1 should already be selected. Click OK.  
> \* Click top pane "Add source folder" button.  
> \* Add path to source folder on disk, e.g., /home/user/workspace/pyproject  
> \* Click OK.  
> \* Add some Python code to Py1.py: print 'Hello world!'  
> \* Save.  
> \* Right-click on Py1.py in Navigator pane.  
> \* Select Run as\\Python run.  
> \* A console window should appear showing output from the Python program.**