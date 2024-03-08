---
title: 'Novidade no edgy: UUID no fstab e menu.lst do grub'
date: 2006-08-21T14:34:00.000-07:00
draft: false
url: /2006/08/novidade-no-edgy-uuid-no-fstab-e.html
tags: 
- Ubuntu
---

#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-08-24T08:08:00.000-07:00">Aug 4, 2006</time>

_Original comment from: [Cesar Cardoso](http://fudeblog.zyakannazio.eti.br)_  
  
A utilização do UUID é uma boa em termos de portabilidade do sistema - fica fácil, por exemplo, trocar um HD de "via" IDE ou, mesmo, tirá-lo de IDE para uma USB da vida.
<hr />
#### _Original comment from: Manuel Portugal Pires_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-11-14T07:43:00.000-08:00">Nov 2, 2006</time>

_Original comment from: Manuel Portugal Pires_  
  
Contudo, se a gente tiver umas partições num disco, e tiver instalado o UBUNTU noutro e modificar as partições no primeiro com o Windows, o UUID fica errado no fstab. Como então determinar o UUID das novas partições para modificar o fstab?! ...  
Nas versões anteriores, incluindo o UBUNTU 06.06.1 era muito fácil.  
  
E agora?! ... fico a chuchar por um dedo, sem saber que fazer ! ...
<hr />
#### _Original comment from: Manuel Portugal Pires_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-11-15T22:30:00.000-08:00">Nov 4, 2006</time>

_Original comment from: Manuel Portugal Pires_  
  
Eu depois de instalar o UBUNTU num 2º disco externo, modifiquei as partições do 1º disco e fiquei sem acesso automático a ela pelo Ubuntu.  
No entanto descobri na internet comandos que me ajudaram a resolver o problema:  
1) sudo vol\_id -u /dev/ (Exemplo: sudo vol\_id -u /dev/hda3) serve para descobrir qual o UUID dessa partição.  
2) editei o ficheiro /etc/fstab e colei lá o respectivo UUID de cada uma das novas partições em substituição dos UUID anteriores.  
3) montei as partições manualmente nos respectivos pontos de montagem e tudo correcto.  
4) quando saí e voltei a entrar no linux (UBUNTU) as respectivas partições foram montadas automaticamente e tudo bem.
<hr />
#### _Original comment from: Manuel Portugal Pires_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-11-15T23:13:00.000-08:00">Nov 4, 2006</time>

_Original comment from: Manuel Portugal Pires_  
  
Em relação ao UUID ponho agora uma questão:  
Será possível haver no mesmo disco duas partições com o mesmo UUID?! ...  
  
Eu fiz uma imagem do Windows que tinha no meu disco interno e estava na 2ª partição primária.  
Depois instalei esssa imagem num aterceira partição primária.  
Fiquei com a impressão que ambas as partições têm o mesmo UUID, mas não estou completamente certo.  
  
Mesmo assim, eu não tenho problemas quando quero montar automáticamente uma dessas partições.  
É que escondo uma e monto apenas a outra partição e assimnão tenho conflito.  
Desta forma se esconder a 2ª partição consigo executar o Windows-XP que está na 3ª partição a partir do Grub e fica com o drive C:  
Se não ocultar a 2ª partição é nessa que consigo executar o Windows-XP (a partir do Grub do Ubunto) e fica do drive C:. Se não ocultar a 3ª partição; esta fica no primeiro drive livre (Exemplo D:). Também tenho acesso à execução do windows que está na terceira partição a partir duma opção no boot.ini que está super-oculto na raiz no windows-XP que está na 2ª partição. Desta forma o Windows que está na terceira partição toma o nome de C: e o que esta na 2ª partição toma o nome da partição livre seguinte. Obs. Atribuí a cada partição do Windows-XP label diferente.  
Tanto posso fazer o boot pelo disco interno como pelo disco externo.  
Para fazer o boot pelo disco externo tenho que configurar o boot no setup do computador de forma a ser o disco USB o 1º a arrancar.
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-03-23T09:12:00.000-07:00">Mar 0, 2008</time>

_Original comment from: [Dario](http://www.diversidades.com.br)_  
  
Valeu pela dica, ajudou bastante!!!  
  
Inté!
<hr />
#### Dario, disponha, valeu pela visita :-).
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-03-25T16:00:00.000-07:00">Mar 2, 2008</time>

Dario, disponha, valeu pela visita :-).
<hr />
#### Agora nas novas versões do UBUNTU, há a possibilid...
[Unknown](https://www.blogger.com/profile/02528262034883173393 "noreply@blogger.com") - <time datetime="2010-09-06T08:58:48.608-07:00">Sep 1, 2010</time>

Agora nas novas versões do UBUNTU, há a possibilidade de o próprio UBUNTU de actualizar o novo UUID que foi criado na outra partição.
<hr />
