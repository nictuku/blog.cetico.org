---
title: 'Status NWU'
date: 2006-09-14T14:45:00.000-07:00
draft: false
url: /2006/09/status-nwu.html
tags: 
- Debian
- Ubuntu
- Nwu
---

O [NWU](http://cetico.org/nwu) está entrando na pré-adolescência, saindo da fase alpha pra beta. Tenho dedicado umas 3 horas por dia ao projeto, principalmente pro empacotamento. Ralei bastante pra adaptar o pacote pra [nova política](http://www.debian.org/doc/packaging-manuals/python-policy/) para pacotes python do Debian, talvez pela complexidade do pacote, que envolve:  
  
\- 3 pacotes "binários"  
\- instalação de módulos públicos  
\- compilação binária dos módulos usando python-support  
\- init scripts (que deve ser executado \*depois\* do dh\_pysupport)  
\- postinst scripts  
\- necessidade de manter um branch de empacotamento funcionando no Sarge (portanto, usando a política de pacotes python antiga)  
  
Pra um empacotador experiente, fazer isso deve levar algumas horinhas. No meu caso, tive que dedicar várias horas pra fazer tudo funcionar, mesmo com uma mãozona inicial do [Mario Meyer](http://blog.meyer.eti.br/), e depois outras várias pra adaptar tudo pra nova política. Abandonar o uso do CDBS foi o fator chave pra simplificar (sim, simplificar) o problema todo, porque eu não conseguia prever a execução dos scripts do cdbs, nem substituí-los com outros alvos make. Especificamente, eu precisava rodar o dh\_pysupport antes do dh\_installinit. É possível com CDBS, me disse o [kov](http://kov.eti.br), eu só não consegui fazê-lo :-).  
  
Algumas pequenas coisas precisam ser concluídas antes que o NWU fique ok para uso geral. Uma delas é o feedback ativo de resultados de ações disparadas pelo NWU, como uma atualização de pacotes. De vez em quando uma atualização falha ou apresenta avisos (culpa do admin da máquina, do Debian/Ubuntu Developer, ou dos dois). É essencial que o administrador receba alguma notificação.  
  
O plano é ter duas formas de notificação. A primeira é enviar um e-mail para o root local com o resultado de uma tarefa. É a forma mais correta, porque supõe-se que todo sysadmin leia os e-mails enviados para o root local - se você não lê, _shame on you_. A segunda é enviar para o web service do NWU-server essas mensagens ao administrador, que deve ler sob demanda, mas recebendo uma pequena notificaçãozinha quando utilizar o comando nwu ("\* You have new messages").  
  
Outra coisa pro futuro é implementar no NWU uma interface **interativa** de administração, em adição à interface atual baseada em linha de comando, inspirada no bconsole do [bacula](http://www.bacula.org/). Antes disso, porém, tenho que concluir algo ainda mais cool - a [interface em GTK](http://www.cetico.org/tech/2006/03/pygtk-em-acao-nwu-admin.html).  
  
Depois de quase abandonar o desenvolvimento da ferramenta, a **necessidade** me fez empolgar novamente com o projeto. No [trampo](http://planet.core.eti.br/), nós administramos dezenas de servidores, e é um custo manter tudo atualizado. Se o NWU é uma necessidade pra nós, imagine pra quem tem 100+ servidores. Pensando nisso, um dos objetivos mágicos do NWU é funcionar não só pra Debian/Ubuntu, mas pra outros sistemas, desde que tenham algo parecido com o APT. Pra isso vamos precisar de mais manpower, mas isso é problema de quem usa essas coisas toscas não-Debian. :-)
