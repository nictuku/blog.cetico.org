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
