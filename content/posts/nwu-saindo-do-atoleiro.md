---
title: 'nwu saindo do atoleiro'
date: 2006-05-17T19:17:00.000-07:00
draft: false
url: /2006/05/nwu-saindo-do-atoleiro.html
tags: 
- Nwu
- Pessoal
---

Oba. O nwu saiu do seu atoleiro emocional e começou uma nova vida. Finalmente fechei o [ticket #56](https://dev.ubuntubrasil.org/trac/nwu/ticket/56), que relatei [noutro post](http://www.cetico.org/tech/2006/05/tempo-de-hackozar.html). Era só uma questão de manualmente criar e fechar cada conexão necessária por thread/request. Isso pode ser óbvio pra você, mas pra mim não era. Na lata eu ganhei também um boost invejável de performance, por passar a utilizar transações.  
O bug do momento é que, após um upgrade, a lista de update candidates do cliente é zerada, mas às vezes o diff dessa modificação é enviada errada pro servidor. É um problema importante, mas nada que cause perda de dados ou instabilidade na máquina. Prova disso é que estou usando o nwu em semi-produção, com 7 clientes, com relativo sucesso.  
  
Vai ser divertido matar isso, porque pela primeira vez no projeto, o bug será primeiro tratado com um teste de unidade e, só depois, corrigido. Graças à grata insistência do Otávio Salvador, me convenci de que uma boa estrutura de [unittest](http://docs.python.org/lib/module-unittest.html) vai ser de fato essencial à estabilidade da ferramenta, que é crítica e, espero, deve ser usada em servidores por outras pessoas além de mim :-).  
Falando em unittest, pela metodologia XP ([XP Programming](http://en.wikipedia.org/wiki/Extreme_Programming)) os testes de unidade devem ser formulados antes mesmo de se escrever o código. Isso é curioso e, IMO, discutível - mas não tão discutível, como me lembrou o [coredump](http://core.eti.br/), que o princípio de [Pair Programming](http://en.wikipedia.org/wiki/Pair_Programming), também proposto pela XP. Gosto da XP, principalmente se compara às alternativas burocratizantes como CMMI e ISO.  
  
No mundo FOSS ainda impera o Bazaar entre as metodologias de desenvolvimento de software, mas hei de concordar, no caso do nwu, em abrir mão de uma das premissas, a de que cabe aos usuários fazer todos os testes. Sendo o nwu crítico para estabilidade e segurança das máquina, não posso correr esse risco.  
  
PS: Uma grande salva de palmas ao Fluminense do Welsey, que precisava ganhar e fez merda. Agora, Pirralho, você aguenta o [César](http://zyakannazio.eti.br/fudeblog/2006/05/18/pra-manter-o-coracao-em-dia/) amanhã.