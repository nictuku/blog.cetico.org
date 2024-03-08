---
title: 'nwu, lancada versao - 0.1.6'
date: 2007-02-25T10:31:00.000-08:00
draft: false
url: /2007/02/nwu-lancada-versao-016.html
tags: 
- Debian
- Ubuntu
- Nwu
---

Lancei hoje a versão 0.1.6 do [Nwu](http://cetico.org/nwu).  
  
**O que é o Nwu?**  
  
Nwu é um sistema que permite a um administrador manter todos os  
computadores Debian e Ubuntu da rede atualizados de forma apropriada,  
a partir de um ponto central, utilizando uma ferramenta de linha de  
comando simples.  
  
O admin pode instalar pacotes nos computadores remotos, aplicar  
atualizações de segurança e atualizar o cache de pacotes APT nas  
máquinas remotas.  
  
Ao invés de utilizar acesso root via SSH, um privilégio exagerado, a comunicação entre agentes e servidor é feita utilizando um web service, de forma segura.  
  
Para ver as máquinas com atualizações pendentes, execute por exemplo:  
  
\# nwu list outdated  
  
Para atualizar o cache do APT num servidor:  
  
\# nwu update <servidor>  
  
Para aplicar atualizações de segurança:  
  
\# nwu upgrade <servidor>  
  
**  
O que há de novo na versão 0.1.6?**  
  
A descrição das mudanças recentes está no Changelog. Destaco a melhoria da instalação. A partir de agora, para instalar o Nwu, basta instalar o pacote e responder às perguntas do debconf. Instale o nwu-server em um local, e o nwu-agent em todos computadores, depois utilize a ferramenta de linha de comando "nwu" para gerenciar o APT de seus servidores.  
  
Veja o Changelog detalhado:  

> This version is a great leap towards 0.2.0. I've decided to officially  
> support only SQLite for persistence, to ease installation and  
> development, but MySQL and PostgreSQL usage should still be possible.  
> Also, thanks to improvements in the deb package, installing nwu-server  
> is as simple as running "dpkg -i". After the administrator answers a  
> few debconf questions, Nwu will be ready for use. Version 0.1.6 also  
> includes many bug fixes.
# Archived Comments
---
title: 'nwu, lancada versao - 0.1.6'
date: 2007-02-25T10:31:00.000-08:00
draft: false
url: /2007/02/nwu-lancada-versao-016.html
tags: 
- Debian
- Ubuntu
- Nwu
---

#### wee
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-02-26T01:30:00.000-08:00">Feb 1, 2007</time>

wee
<hr />
