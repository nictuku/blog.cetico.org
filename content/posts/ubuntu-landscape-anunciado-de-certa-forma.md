---
title: 'Ubuntu Landscape anunciado - de certa forma'
date: 2006-05-28T17:44:00.000-07:00
draft: false
url: /2006/05/ubuntu-landscape-anunciado-de-certa.html
tags: 
- Debian
- Ubuntu
- Nwu
---

Mark Shuttleworth mencionou numa entrevista recente que a Canonical está trabalhando num serviço que irá provavelmente chocar com o [NWU](http://www.cetico.org/nwu):  

> There is, additionally, a team that’s working on management infrastructure, so providing people with a comprehensive framework to manage large deployments of servers. That won’t be released for Dapper, but all the foundations of it will be there so that Dapper will be manageable just as people have come to expect a Red Hat Enterprise deployment to be managed, through the web. We’ll deliver that same level of functionality with Dapper as soon as the other pieces of that solution are in place.

  
Aparentemente, será um serviço pago, parecido com o Red Hat Network. Já foi incluído recentemente no Dapper um pacote que ocupa um espaço que será provavelmente substituído por uma ferramenta parecida com o nwu-agent, chamado [landscape-client](http://packages.ubuntu.com/dapper/admin/landscape-client).  
  
Essa ferramenta torna o Ubuntu atrativo para o mercado que prefere produtos ditos "Enteprise". Ela também nos ajuda a entender que a Canonical não é uma estranha organização humanitária, mas uma empresa voltada ao mercado (apesar de ter uma filosofia de conduta). Projetos secretos são esperados nesse contexto.  
  
Acho que eles deveriam ter trazido isso a público antes, apesar de que eu teria trabalhado no NWU de qualquer forma. Eu ainda estou trabalhando duro nele, por três razões: 1) aparentemente esse landscape não será livre ou gratuito; 3) O Debian ainda irá precisar (acredito) de uma ferramenta assim e; 3) Eu dediquei [meses](https://dev.ubuntubrasil.org/trac/nwu/timeline?from=05%2F29%2F06&daysback=360&milestone=on&ticket=on&changeset=on&wiki=on&update=Update) do meu tempo livre desenvolvendo uma implementação daquele spec e está quase pronta.  
  
Tenho esperança que esse software não irá substituir o NWU inteiramente, portanto não vejo muitos problemas. Acho apenas que eles deveriam tê-lo mencionado - talvez na especificação do [NetworkWideUpdates](https://wiki.ubuntu.com/NetworkWideUpdates).  
  
Esse comportamento pode não quebrar as políticas de "ser sempre livre" ou "nunca ter licenças restritivas associadas ao Ubuntu", mas torna menos atraente para a comunidade contribuir com o Ubuntu, disso estou certo.
# Archived Comments
---
title: 'Ubuntu Landscape anunciado - de certa forma'
date: 2006-05-28T17:44:00.000-07:00
draft: false
url: /2006/05/ubuntu-landscape-anunciado-de-certa.html
tags: 
- Debian
- Ubuntu
- Nwu
---

#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-05-31T16:45:00.000-07:00">Jun 4, 2006</time>

_Original comment from: [Cesar Cardoso](http://fudeblog.zyakannazio.eti.br)_  
  
Só uma observação...  
  
Da mesma maneira que o RedHat Network não substitui o yum (\*), o Canonical Landscape certamente não vai substituir o NWU.  
  
Primeiro, como você mesmo disse, o Landscape está restrito a um produto (Ubuntu), enquanto o NWU, tem como alvos, potencialmente, qualquer distribuição que use APT. Uma idéia, inclusive, seja separar o backend APT do front-end, com isso tornando potencialmente possível que o NWU seja usado junto ao yum, urpmi, o troço que a Novell/Suse usa (red-carpet? yast?) e por aí vai.  
  
Segundo, nem todo mundo que tem grandes instalações de Ubuntu vai querer o Landscape embora queira ter um gerenciamento centralizado de pacotes, seja por necessidades específicas (ex. pacotes customizados), seja por política da empresa, seja por, sei lá, o sysadmin acha o nome Canonical horroroso. Essa gente, que não é pouca, precisa de alguma maneira de manter seus sistemas atualizados.  
  
O negócio é continuar no trabalho, o NWU tá ficando legal :)  
  
(\*) o yum pode 'emular' a funcionalidade do NWU, só que funciona ao contrário; o cliente vai toda noite e baixa as atualizações. Quem quiser inverter o fluxo pode usar o YAM (http://dag.wieers.com/home-made/yam/).
<hr />
