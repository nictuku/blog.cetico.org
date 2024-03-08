---
title: 'Ubuntu é a distro mais rápida em correções de segurança'
date: 2006-07-28T19:09:00.000-07:00
draft: false
url: /2006/07/ubuntu-distro-mais-rpida-em-correes-de.html
tags: 
- Debian
- Ubuntu-BR
- Ubuntu
---

Um [relatório](http://searchsecurity.techtarget.com/originalContent/0,289142,sid14_gci1202417,00.htm) publicado na searchsecurity.techtarget.com mostra que, numa pesquisa entre diversas distribuições Linux, mas incluindo também OpenBSD e FreeBSD, sobre o tempo de resposta na correção de um conjunto de 30 vulnerabilidades, o Ubuntu é distro que lança correções de segurança mais rapidamente, seguido pelo Fedora, RHCE e Debian. Slackware ficou em último entre a distros analisadas, atrás do OpenBSD e do SUSE.  
  
Apesar de ser um estudo simples e com uma amostra pequena (não científico, como apontado no texto), o resultado é importante para demonstrar a maturidade e a seriedade do projeto Ubuntu. Com esse tipo de boa notícia, usuários, gerentes de TI e sysadmins terão mais segurança em utilizar o Ubuntu e poderão considerar com base em mais argumentos técnicos a substituição dos desktops e servidores MS Windows ou, ainda, daqueles Red Hat 7.2 e 9 que tanto se vê por aí.  
  
Como esperado, não há relação direta entre a distribuição ser comercialmente suportada ou não e a velocidade no lançamento das correções - o Debian ficou muito bem colocado, considerando que contém a maior quantidade de pacotes administrados e a mais complexa infra-estrutura até onde se sabe.  
  
Por outro lado, como apontado pelo autor, é necessário cuidado ao analisar os números. Velocidade de reposta não é tudo, e pode inclusive causar regressões de funcionalidade se não houver o devido controle de qualidade nessas atualizações. Isso aconteceu [recentemente](https://lists.ubuntu.com/archives/ubuntu-security-announce/2006-July/000370.html) com o php4 no Ubuntu:  

>   
> ```
> USN-320-2 fixed several vulnerabilities in PHP. James Manning  
> discovered that the Ubuntu 5.04 update introduced a regression, the  
> function tempnam() caused a crash of the PHP interpreter in some  
> circumstances. The updated packages fix this.
> ```  
> ```
> We apologize for the inconvenience.
> ```  

  
Nada muito sério, felizmente.  
  
Dessa forma, distribuições como SuSE e Trustix ficaram mal colocados, possivelmente em vista de maior cuidado em suas atualizações. Seria útil comparar essa pequena pesquisa com um estudo da quantidade de regressões geradas por atualizações de segurança. No caso do Windows, sei que a porcentagem de regressões costumava ser "não desprezível" - pelo menos foi o que demonstrou minha experiência pessoal.  
  
A má performance do Slackware e do OpenBSD também devem ser melhor explicados. Há pelo menos duas possibilidades: a) as atualizações são cuidadosamente auditadas e testadas antes de serem disponibilizadas, mais do que nos demais; b) a estrutura desses projetos não facilitam, ou não priorizam, a velocidade no lançamento das correções dos bugs de segurança. Talvez quem conheça melhor esses projetos possa explicar isso direito, mas não é o meu caso.
# Archived Comments
---
title: 'Ubuntu é a distro mais rápida em correções de segurança'
date: 2006-07-28T19:09:00.000-07:00
draft: false
url: /2006/07/ubuntu-distro-mais-rpida-em-correes-de.html
tags: 
- Debian
- Ubuntu-BR
- Ubuntu
---

#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-07-30T04:39:00.000-07:00">Jul 0, 2006</time>

_Original comment from: [Fábio Nogueira](http://barraroumi.wordpress.com)_  
  
Que continuemos com esse grande trabalho!  
;)
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-06-09T18:16:00.000-07:00">Jun 0, 2007</time>

_Original comment from: [nun tenho](http://nuntenho)_  
  
esterco.  
  
bela bosta  
  
bom peido  
  
openbsd rula esta porra toda.
<hr />
