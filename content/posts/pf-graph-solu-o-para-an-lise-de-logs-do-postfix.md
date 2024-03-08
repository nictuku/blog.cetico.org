---
title: 'PF-Graph - Solução para análise de logs do Postfix'
date: 2005-06-07T04:40:00.000-07:00
draft: false
url: /2005/06/pf-graph-soluo-para-anlise-de-logs-do.html
tags: 
- Tech Tip
---

Estou desenvolvendo uma ferramenta para análise de logs do Postfix. O PF-Graph, além de gerar relatórios com base em remetentes ou destinatários (incluíndo busca por domínios), cria gráficos coloridos sobre o status do serviço.  
  
Veja abaixo algumas screenshots:  
  
[![Free Image Hosting at www.ImageShack.us](http://img212.echo.cx/img212/2430/pfgraph9lj.th.png)PF-Graph, mostrando o sumário de gráficos.](http://img212.echo.cx/my.php?image=pfgraph9lj.png)  
  
[![Free Image Hosting at www.ImageShack.us](http://img279.echo.cx/img279/4962/pfgraph23dm.th.png)Resultado de busca](http://img279.echo.cx/my.php?image=pfgraph23dm.png)  
  
Entre os recursos do PF-Graph, incluem-se:  
  
\- Capacidade de auditar todas as mensagens recebidas e enviadas em um ou mais servidor de e-mail, em tempo real.  
  
\- Um daemon/agente rodando nos servidores de e-mail é responsável por coletar as informações em tempo real, e atualizar o banco de dados.  
  
\- Capacidade de mostrar total de bytes trafegados para um usuário, domínio ou qualquer termo de busca(exige Amavisd-new ou Suriproxy).  
  
\- Escrita em Perl, com integração nativa para MySQL, mas possível de se adaptar para outros bancos de dados, conforme a necessidade.  
  
Assim que eu der uma "limpada" no código do PF-Graph, o mesmo será disponibilizado sob a licença GPL. Caso esteja interessado nessa ferramenta, deixe um comentário!  
  
Até mais!
# Archived Comments
---
title: 'PF-Graph - Solução para análise de logs do Postfix'
date: 2005-06-07T04:40:00.000-07:00
draft: false
url: /2005/06/pf-graph-soluo-para-anlise-de-logs-do.html
tags: 
- Tech Tip
---

#### _Original comment from: Sérgio M. F. Caldeira_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2005-06-07T10:29:00.000-07:00">Jun 2, 2005</time>

_Original comment from: Sérgio M. F. Caldeira_  
  
Excelente a apresentação dos gráficos. Sem dúvida, não fica nada a dever a outras ferramentas de análise disponíveis (Isoqlog, mailpgraph, etc), muito pelo contrário.  
  
Parabéns Yves;  
  
PS: quando disponibilizar o programa, deixe um recado na lista do Postfix. Com certeza, vai ter muita gente interessada em testar.  
Inclusive eu. :-)
<hr />
#### _Original comment from: Anonymous_ Yves,
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2005-06-07T14:02:00.000-07:00">Jun 2, 2005</time>

_Original comment from: Anonymous_  
  
Yves,  
  
Parabéns!  
Pelos Screenshots dá para perceber  
que é "De Primeira".  
Não esqueca de avisar na Postfix-BR para agente testar!  
  
Abracos  
Ultra7
<hr />
#### _Original comment from: -Gurizito-_ Buenas...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2005-06-08T02:21:00.000-07:00">Jun 3, 2005</time>

_Original comment from: -Gurizito-_  
  
Buenas! Muito Bom o software, pelo que podemos verificar é ótimo. Espero que possas liberr logo para podermos usufruir do mesmo.  
  
Abraços
<hr />
#### _Original comment from: victor_ qual o end...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-04-04T17:29:00.000-07:00">Apr 4, 2007</time>

_Original comment from: victor_  
  
qual o endereco para download?
<hr />
