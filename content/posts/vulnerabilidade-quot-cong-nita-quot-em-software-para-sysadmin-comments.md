---
title: 'Vulnerabilidade &quot;congênita&quot; em software para sysadmin'
date: 2006-02-21T17:44:00.000-08:00
draft: false
url: /2006/02/vulnerabilidade-em-software-para.html
tags: 
- Ubuntu
---

#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-02-22T15:11:00.000-08:00">Feb 3, 2006</time>

_Original comment from: [Cesar Cardoso](http://fudeblog.zyakannazio.eti.br)_  
  
Risco é algo que se corre ao colocar um programa qualquer em uma máquina, afinal os bugs, os exploits e os exploiters estão sempre correndo à nossa frente. O que podemos fazer é, sim, minimizar esses riscos, por exemplo, evitando AO MÁXIMO rodar como root ou precisar de suid root, ou banindo qualquer tentativa de acesso via root remoto.  
  
O webmin já teve seu tempo. Foi útil para administração local antes das ferramentas desktop como o gnome-system-tools, para administração remota sempre teve problemas sérios de arquitetura.
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-02-22T17:59:00.000-08:00">Feb 4, 2006</time>

_Original comment from: [Fudeblog by Cesar Cardoso » Aqui e ali](http://zyakannazio.eti.br/fudeblog/?p=767)_  
  
\[...\] O Espírito que Anda fala sobre vulnerabilidades em softwares de administração de sistemas. Interessante para iniciar discussão, eu comentei lá \[...\]
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-02-24T03:04:00.000-08:00">Feb 5, 2006</time>

_Original comment from: [RJP](http://estudiodaintrospeccao.blogspot.com)_  
  
Well, eu acho o webmin... Legal. Mas tive problemas p/ mexer c/ ele c/ LDAP, por exemplo. E ainda sou antiquado, do tipo q nada melhor do q um SSH+joe (vi não)+Google+livros+sagacidade para salvar o dia.  
  
É, acho q vou logar lá no meu último serviço e desinstalar o webmin. Pelo menos economiza um espaço.
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-06-14T14:56:00.000-07:00">Jun 4, 2007</time>

_Original comment from: [» Virtualmin \_pode\_ ajudar sua vida cetico.org: Eu, Sysadmin - Yves Junqueira](http://cetico.org/tech/2007/06/virtualmin-_pode_-ajudar-sua-vida.html)_  
  
\[...\] Tudo lindo, mas qual é o problema? O problema é que o Webmin (do qual Virtualmin é um módulo) tem um passado extenso de problemas de segurança. É um sistema extremamente complexo, com módulos pra se administrar de tudo, e com zilhões de controles de segurança necessários para manter a sanidade dos privilégios dos usuários do sistema, e de usuários “anônimos”. Alguém sente cheiro de exploit remoto? Pois é, e em parte por causa disso o webmin foi removido do Debian a partir do Etch (e consequentemente do Ubuntu). Já falei disso aqui. \[...\]
<hr />
