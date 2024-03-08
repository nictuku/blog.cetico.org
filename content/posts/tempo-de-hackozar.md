---
title: 'Tempo de hackozar'
date: 2006-05-08T15:32:00.000-07:00
draft: false
url: /2006/05/tempo-de-hackozar.html
tags: 
- Pessoal
---

O [nwu](https://dev.ubuntubrasil.org/trac/nwu) está há semanas na UTI. Culpa de um daqueles bugs difíceis de se resolver, que podem inviabilizar projetos de desenvolvimento voluntário. O problema pode até não ser complicado, mas dá uma preguiça enorme de sentar para trabalhar nisso.É frustrante. Em um projeto desenvolvido em tempo livre, dá uma broxada você sentar vários dias pra resolver um problema, mas não sair nada.  
  
O problema no \[tag\]nwu\[/tag\] é uso de memória. Eu não sou um desenvolvedor muito experiente, daí ainda me embanano em projetos grandes. Nesse caso, apesar de todos os meus esforços para fazer um [código](https://dev.ubuntubrasil.org/trac/nwu/browser/trunk/) organizado e bem estruturado, todos os requests XML-RPC estão sendo mantidos em um mesmo escopo do sistema. Mesmo seguindo a sugestão do [coredump](http://core.eti.br/ "coredump") e usando threads, o problema persiste, isto é, o SQLObject faz cache de requests e o daemon não desfaz as referências aos objetos, como deveria (quer dizer, como eu gostaria).  
  
A solução é fazer conexões do sqlobject para cada thread. O desafio é fazer isso sem utilizar o ConnectionHub, disponível apenas no sqlobject 0.7 - que não está disponível no \[tag\]Debian\[/tag\] 3.1, uma das distribuições-alvo (junto com \[tag\]Ubuntu\[/tag\] 6.06). Acredito que usar um dicionário e manter nele as conexões de cada thread. Vamos ver :-). Ainda estou devendo também fazer a estrutura de unittest pro nwu, como sugerido pelo Otavio Salvador, melhoria essencial pra ferramenta ser confiável.  
  
A novidade do dia é que recebi um convite do Google para hospedar os e-mails do cetico.org no Gmail. Eu havia me inscrito como beta tester do programa há alguns meses - é o chamado \[tag\]gmail hosted\[/tag\].  
É impecável. Além de poder utilizar a interface do Gmail nos e-mails de seu próprio domínio, cujas contas você pode administrar por meio de uma interface googliana, ele permite algum nível de [personalização](http://mail.google.com/hosted/cetico.org/), disponibiliza \[tag\]jabber\[/tag\] com syndication, além de todas as funcionalidades do gmail, como POP, anti-spam. Isso tudo com a vantagem de utilizar seu próprio domínio personalizado.  
  
Não sei se o serviço continuará a ser gratuito, mas pelo modelo de negócios do Google, tudo indica que sim. Os adwords continuam lá, mas não incomodam. É duca.
# Archived Comments
---
title: 'Tempo de hackozar'
date: 2006-05-08T15:32:00.000-07:00
draft: false
url: /2006/05/tempo-de-hackozar.html
tags: 
- Pessoal
---

#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-05-17T19:17:00.000-07:00">May 4, 2006</time>

_Original comment from: [cetico.org » Blog Archive » nwu saindo do atoleiro](http://www.cetico.org/tech/2006/05/nwu-saindo-do-atoleiro.html)_  
  
\[...\] Oba. O nwu saiu do seu atoleiro emocional e começou uma nova vida. Finalmente fechei o ticket #56, que relatei noutro post. Era só uma questão de manualmente criar e fechar cada conexão necessária por thread/request. Isso pode ser óbvio pra você, mas pra mim não era. Na lata eu ganhei também um boost invejável de performance, por passar a utilizar transações. O bug do momento é que, após um upgrade, a lista de update candidates do cliente é zerada, mas às vezes o diff dessa modificação é enviada errada pro servidor. É um problema importante, mas nada que cause perda de dados ou instabilidade na máquina. Prova disso é que estou usando o nwu em semi-produção, com 7 clientes, com relativo sucesso. \[...\]
<hr />
