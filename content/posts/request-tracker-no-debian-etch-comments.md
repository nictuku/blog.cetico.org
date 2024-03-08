---
title: 'Request Tracker no Debian Etch'
date: 2007-04-08T09:56:00.000-07:00
draft: false
url: /2007/04/request-tracker-no-debian-etch.html
tags: 
- Tech Tip
---

#### _Comment from Luciano:_ os pacote rt3.6-ap...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-09-17T04:59:00.000-07:00">Sep 1, 2007</time>

_Comment from Luciano:_  
  
os pacote rt3.6-apache, não é mais encontrado pelo apt-get
<hr />
#### Luciano, provavelmente você está usando o Lenny, e...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-09-17T06:57:00.000-07:00">Sep 1, 2007</time>

Luciano, provavelmente você está usando o Lenny, então. No Etch existe, sim, o rt3.6-apache2:  
  
$ apt-cache search request tracker apache  
rt3.4-apache - Apache 1 specific files for request-tracker3.4  
rt3.4-apache2 - Apache 2 specific files for request-tracker3.4  
rt3.6-apache - Apache 1 specific files for request-tracker3.6  
rt3.6-apache2 - Apache 2 specific files for request-tracker3.6  
  
\[\]s
<hr />
#### _Comment from Luke:_ Cara, Meu apache esta...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-03-17T07:18:00.000-07:00">Mar 1, 2008</time>

_Comment from Luke:_  
  
Cara,  
Meu apache esta dando erro no nódulo RewriteEngine.  
  
Forcing reload of web server (apache2)...Syntax error on line 26 of /etc/request-tracker3.6/apache2-modperl2.conf:  
Invalid command 'RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration
<hr />
#### _Comment from Luke:_ Cara. ja consegui sub...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-03-17T08:06:00.000-07:00">Mar 1, 2008</time>

_Comment from Luke:_  
  
Cara. ja consegui subir o módulo...  
  
Desculpa pelo incomodo!!!
<hr />
#### _Comment from magel:_ Que modulo Subistes....
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-04-19T02:23:00.000-07:00">Apr 6, 2008</time>

_Comment from magel:_  
  
Que modulo Subistes.?  
Como lo subistes?  
Gracias
<hr />
#### _Comment from Daniel Santiago:_ Olá amigo,...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-06-02T03:56:00.000-07:00">Jun 1, 2008</time>

_Comment from Daniel Santiago:_  
  
Olá amigo, ñ sei o que está acontecendo, mas quando coloco meu ip/rt nao dá nada... o rt tem que aparecer no /var/www?
<hr />
