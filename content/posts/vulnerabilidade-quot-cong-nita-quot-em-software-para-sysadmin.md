---
title: 'Vulnerabilidade &quot;congênita&quot; em software para sysadmin'
date: 2006-02-21T17:44:00.000-08:00
draft: false
url: /2006/02/vulnerabilidade-em-software-para.html
tags: 
- Ubuntu
---

Há uma intensa e inacabável discussão sobre softwares que facilitem a administração de serviços e servidores, debate esse que fica ainda mais acalorado quando se menciona administradores em interface web.  
  
O ponto principal do debate é que, para que se dê acesso limitado da administração de serviços a um usuário, o software vai precisar _enjaular_ esse usuário muito bem, fazendo um controle de acesso muito complexo e com diversos possíveis pontos de falha.  
  
No caso do Webmin, por exemplo, o daemon roda com usuário **root** e é necessário gerenciar não só a autenticação do usuário, como também controlar seu acesso. Para quem não conhece, o webmin permite delegar a um usuário o controle de apenas um serviço X, ou ainda apenas a componentes específicos de X (como controlar sistemas de arquivo, porém modificar os dados apenas do diretório /var/www/usuario/).  
  
O histórico do webmin mostra que a complexidade dos seus mecanismos de controle de acesso e o potencial impacto ("root remoto", direto) da descoberta de vulnerabilidade no programa levaram à descoberta de diversas vulnerabilidade, algumas, se não me falha a memória, ainda na fase pré-autenticação(!!).  
[Recentemente o webmin foi retirado do Debian-sid](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343897), depois que o mantenedor compreensivelmente jogou a toalha, culpando inclusive a qualidade dos pacotes do webmin:  
```
It is better to drop them now rather than perpetrate the cruel joke  
that these are Debian-quality packages; especially because newbies often  
rely on webmin to administer their systems and keep them secure.  And we owe  
it to Jamie Cameron, the author of webmin, not to besmirch his name and product  
with buggy crap.
```  
Mesmo que todos saibam do riscos que essas interfaces de gerenciamento possam representar, a oferta de ferramentas semelhantes só aumenta. Recentemente ouvi falar de outras duas: o [ebox](http://ebox-platform.com/) e o [gosa](http://gosa.gonicus.de/).  
  
Sistemas para facilitar a administração de servidores são ferramentas essenciais para os iniciantes e, considerando-se nessa categoria aqueles softwares de grande porte como o cpanel, há milhares de empresas cuja continuidade e segurança dos negócios dependem de interfaces de administração de serviços (penso numa empresa de hosting).  
  
Eu mesmo me confesso simpático e reconhecedor da utilidade dessas ferramentas, desde que muito bem desenhadas e implementadas. Estou tendo uma grande preocupação com o desenvolvimento do meu [nwu](https://opensvn.csie.org/traccgi/nwu/trac.cgi/), visto que envolve a execução de tarefas como root nas máquinas gerenciadas.  
  
Minha estratégia para tentar garantir um nível razoável de segurança passa por: utilizar criptografia na transmissão (HTTPS) e na autenticação (HMAC) das mensagens; não supor que o cliente seja confiável, mesmo que autenticado e; principalmente, mapear todos os possíveis pontos de risco da aplicação e auditá-los sempre.  
  
Não tenho dúvida que fazer software seguro exige muito esforço e, tcha-na-nãs, tempo livre. Afinal de contas, só consideram questões de segurança quando não há prazo a ser cumprido :-).
# Archived Comments

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
