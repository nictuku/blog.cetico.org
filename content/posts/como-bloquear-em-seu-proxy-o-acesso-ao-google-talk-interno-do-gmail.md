---
title: 'Como bloquear em seu proxy o acesso ao Google Talk interno do Gmail'
date: 2006-02-13T07:23:00.000-08:00
draft: false
url: /2006/02/como-bloquear-em-seu-proxy-o-acesso-ao.html
tags: 
- Tech Tip
- Ubuntu
---

Muitas organizações têm como política não permitir a utilização de softwares de "mensageria instantânea", ou _instant messaging_.  
  
Isso pode não ser uma abordagem muito eficiente, pois a tendência é que os usuários começem a utilizar o próprio e-mail como sistema de mensagem instantânea. A gerência deve ter consciência que esta provavelmente não é a melhor forma de se melhorar a produtividade da equipe.  
  
Por outro lado, já vi muitos gerentes experientes colocando rédeas curtas em sua equipe não por incompetência de liderança, mas em consequência da imaturidade de colaboradores. Além do mais, proibir o acesso direto no proxy de internet é bem mais simples :-).  
  
Com a disponibilização no Gmail de uma interface integrada de comunicação via Google Talk, surge a demanda por uma forma de bloquear o acesso a este recurso especificamente, sem bloquear o Gmail em si.  
  
Para isso, o acesso à seguinte URL específica deve ser bloqueado:  
  
http://mail.google.com/mail/channel/bind\*  
  
Para configurar o Squid para esse fim, o sysadmin deve alterar o squid.conf, incluindo as seguintes regras:  
  
`  
acl gtalk url_regex -i "mail\.google\.com/mail/channel/bind"`  
  
`  
http_access deny gtalk`  
  
**UPDATE**: para bloquear também os domínios pessoais com Gmail ativado, utilize "channel\\/bind" apenas.  
Acho uma pena que o Google Talk seja bloqueado, pois é um serviço muito bacana e bonitinho. Só estou mostrando como fazê-lo.  
  
Espero que tenha sido útil.
# Archived Comments

#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-02-13T07:38:00.000-08:00">Feb 1, 2006</time>

_Original comment from: [Cesar Cardoso](http://fudeblog.zyakannazio.eti.br)_  
  
Acabou a festa da galera, hehehehehe
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-02-14T13:31:00.000-08:00">Feb 2, 2006</time>

_Original comment from: [Leandro Santoro](http://whatever.blog.terra.com.br)_  
  
hahah ele é o cara mesmo... aposto que naum foi dormir enquanto naum criou a regra do squid né?  
  
Abr,  
Leandro Santoro.
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-03-19T05:39:00.000-08:00">Mar 0, 2006</time>

_Original comment from: [GustavoPaes.Net » Bloquar Gtalk](http://www.gustavopaes.net/blog/2006/03/19/bloquar-gtalk/)_  
  
\[...\] Só para corrigir um post meu, descobri que tem como bloquear o Gtalk sem bloquear o GMail. Veja neste blog a forma de se bloquear. \[...\]
<hr />
#### _Original comment from: Pedro_ Gostaria de...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-05-26T18:19:00.000-07:00">May 6, 2006</time>

_Original comment from: Pedro_  
  
Gostaria de saber como bloquear o acesso para as contas pop do GMail e outros...
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-08-17T07:38:00.000-07:00">Aug 4, 2006</time>

_Original comment from: [Turnit](http://turnit.com)_  
  
Esses caras que vivem bloqueando tudo e se acham os tais...devem ser os maiores nerds caretões
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-08-18T14:40:00.000-07:00">Aug 5, 2006</time>

_Original comment from: [cetico](javascript:void(0);)_  
  
Turnit, leia o texto do post antes de falar merda.
<hr />
#### _Original comment from: Mariano Revilla_ N...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-09-11T04:33:00.000-07:00">Sep 1, 2006</time>

_Original comment from: Mariano Revilla_  
  
No funciona !!! :-(
<hr />
#### _Original comment from: Renato_ A alegria ...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-01-22T01:02:00.000-08:00">Jan 1, 2007</time>

_Original comment from: Renato_  
  
A alegria dos administradores de rede e gerentes incompetentes.  
  
Depois reclamam qdo bloqueam o youtube.  
  
VIVA A INCOMPETENCIA !
<hr />
#### _Original comment from: possoni_ Pra galer...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-04-13T04:32:00.000-07:00">Apr 5, 2007</time>

_Original comment from: possoni_  
  
Pra galera que acha que não deve ter bloqueio, também concordo, mas em casa. Na empresa é lugar de trabalhar.  
  
Liberdade com oque é seu, e não com oque é dos outros.
<hr />
#### _Original comment from: fala serio_ quer v...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-06-12T11:08:00.000-07:00">Jun 2, 2007</time>

_Original comment from: fala serio_  
  
quer ver gmail, orkut...fica em casa!
<hr />
#### _Original comment from: fala serio_ A fila...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-06-12T11:09:00.000-07:00">Jun 2, 2007</time>

_Original comment from: fala serio_  
  
A fila do desemprego aumenta cada dia mais...Vão pedir emprego na google!
<hr />
#### _Original comment from: ricardo_ cara pra ...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-08-07T08:34:00.000-07:00">Aug 2, 2007</time>

_Original comment from: ricardo_  
  
cara pra windows tenho isa aqui obrigado
<hr />
#### _Original comment from: guilhermebjr_ Odei...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-08-28T14:20:00.000-07:00">Aug 2, 2007</time>

_Original comment from: guilhermebjr_  
  
Odeio Isa.  
Não vejo nada melhor que linux+squid.  
Minha opinião..  
Grato.
<hr />
#### _Original comment from: maykon_ Valeu pelo...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-12-25T08:28:00.000-08:00">Dec 2, 2007</time>

_Original comment from: maykon_  
  
Valeu pelo post, mais tenho uma duvida...  
tem uma galera que acessa o talk através de um gadget, não é necessário efetuar o download para acessar o talk, e está regra não funciona para evitar o uso do gadget...  
http://www.google.com/talk/intl/pt-BR/  
t+.....
<hr />
#### Oi Maykon, Não entendi. De qual gadget você está ...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-12-25T14:45:00.000-08:00">Dec 2, 2007</time>

Oi Maykon,  
  
Não entendi. De qual gadget você está falando? Ou vc quer dizer um 'widget'?
<hr />
#### _Original comment from: Lucas_ E como desb...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-04-23T01:52:00.000-07:00">Apr 3, 2008</time>

_Original comment from: Lucas_  
  
E como desbloquear??
<hr />
#### _Original comment from: Thiago_ só bloquea...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-05-05T09:32:00.000-07:00">May 1, 2008</time>

_Original comment from: Thiago_  
  
só bloquear o "chatenabled.mail.google.com" que você bloquia SOH o talk, e o gmail ainda rola ;\]
<hr />
#### Great post, you have pointed out some fantastic po...
[UsamaAk](https://www.blogger.com/profile/13967471967400289326 "noreply@blogger.com") - <time datetime="2020-02-13T03:21:01.721-08:00">Feb 4, 2020</time>

Great post, you have pointed out some fantastic points , I likewise think this s a very wonderful website. [1337x](https://www.latestgadget.co/internet/1337x-proxy-mirror-sites/)
<hr />
