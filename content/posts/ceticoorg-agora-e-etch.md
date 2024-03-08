---
title: 'cetico.org agora e Etch'
date: 2007-02-17T18:58:00.000-08:00
draft: false
url: /2007/02/ceticoorg-agora-e-etch.html
tags: 
- Tech Tip
- Debian
---

Atualizei o cetico.org pra Etch. Meu SVN tava meio esquisito, então aproveitar pra atualizar tudo. A atualização foi tranquila.  
  
Sobre o erro do SVN, a solução que acabei achando talvez seja útil para alguém. A mensagem que tava dando era:  
  
\[Sun Feb 18 03:42:36 2007\] \[error\] \[client 200.140.85.205\] (20014)Internal error: Berkeley DB error for filesystem '/var/svn/nwu/db' while opening environment:\\n  
\[Sun Feb 18 03:42:36 2007\] \[error\] \[client 200.140.85.205\] Could not fetch resource information.  \[500, #0\]  
\[Sun Feb 18 03:42:36 2007\] \[error\] \[client 200.140.85.205\] Could not open the requested SVN filesystem  \[500, #160029\]  
\[Sun Feb 18 03:42:36 2007\] \[error\] \[client 200.140.85.205\] Could not open the requested SVN filesystem  \[500, #160029\]  
  
Dai nada resolveu. O que funcionou foi fazer um dumpload e migrar os dados pro format FSFS. [Veja aqui como](http://subversion.tigris.org/faq.html#bdb-fsfs-convert). Aí deu tudo certo =\]
