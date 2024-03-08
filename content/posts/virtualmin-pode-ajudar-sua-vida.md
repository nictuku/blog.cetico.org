---
title: 'Virtualmin _pode_ ajudar sua vida'
date: 2007-06-02T20:57:00.000-07:00
draft: false
url: /2007/06/virtualmin-pode-ajudar-sua-vida.html
tags: 
- Tech Tip
- Debian
- Ubuntu
- Postfix
- sysadmin
---

Até que sou um sysadmin bem organizado, mas confesso que meu servidor pessoal (cetico.org, um "MiroVPS2" com 160Mb de RAM) é uma bagunça. Melhor dizendo, era.  
  
Dois amigos estavam precisando de um lugar pra hospedar temporariamente seus respectivos sites e domínios de e-mail e me pediram ajuda. Argh. "Isso vai dar trabalho", pensei. A não ser que eu delegasse a trabalheira pra eles :-).  
  
Como hospedar sites num servidor sem ter o trabalho de configurar na mão o DNS, o Postfix e os virtualhosts do Apache pra que cada usuário mantenha seu próprio ambiente ? É preciso que cada responsável possa criar caixas e aliases de e-mail para seu domínio, defina configurações extras no Apache específicas pra o seu VirtualHost, além dos bancos de dados. Portanto, como criar meu próprio servidor de "hosting"?  
  
Há algumas formas de se fazer isso. Os chamados "Painéis de controle" (control panel, CP) ajudam a delegar elementos de configuração para o usuário. Os mais conhecidos são os comerciais [Cpanel](http://www.cpanel.net/), [Plesk](http://www.swsoft.com/plesk/) e os livres [Webmin](http://www.webmin.com/)/[Virtualmin](http://www.virtualmin.com/) (GPL) e [ISPConfig](http://www.ispconfig.org/index.htm) (BSD). Há ainda painéis de controle mais específicos como o [PostfixAdmin](http://postfixadmin.com/) (Postfix + MySQL) e o [JeguePanel](http://www.jeguepanel.net/) (brasileiro, Postfix + LDAP).  
  
Para o que eu preciso, só o Virtualmin e o ISPConfig atenderiam. E pelo menos dessa vez decidi utilizar o Virtualmin. A instalação é muito simples. Primeiro [instale o Webmin](http://www.webmin.com/download.html). De dentro do própro Webmin (que aliás está com um tema **muito** melhor do que antes) dá pra [instalar o módulo](http://www.webmin.com/vdownload.html) novo e [adaptar todos os sistemas para que funcionem com o Virtualmin](http://www.swelltech.com/support/virtual-servers/index.html).  
  
Depois disso, é só criar usuários e domínios, de acordo com templates definidos por você (sei lá, usuários "premium", "gold", "badecos"), que poderão ter os recursos e funcionalidades limitadas de acordo com os perfis. No meu caso, configurei um só template padrão com quotas ilimitadas e tá bom demais. Gostei também da possibilidade de importar "domínios" atuais para seguir o padrãozão dele.  
  
Ou seja, criei um usuário 'yvesjmt' e importei o virtualhost "cetico.org" que estava definido no Apache, e os bancos de dados referentes a esse domínio no MySQL. Ou seja, o "cetico.org" virou só mais um domínio no meu mini servidor de hosting. Bem mais organizado e, principalmente, mais fácil de fazer backup ou mover futuramente. Meu VPS agora é um servidor de hosting compartilhado amador :-).  
  
Essa abordagem pode funcionar bem, acredito, em organizações de desenvolvimento de software. O administrador de sistemas pode criar um espaço no servidor para cada sistema/projeto, e delegar todo o controle para os analistas ou programadores. Querem ativar o register\_globals no PHP? Eles mesmo podem fazer isso - e apenas no seus respectivos virtual hosts. Ou quem sabe ficaram trabalhando no fim de semana e querem ver como ficou o sistema no servidor de testes - é só mandar via SCP ou FTP e pronto - sem trabalheira para os pobres sysadmins.  
  
Algumas organizações seguem essa lógica para ambientes de desenvolvimento de softwares, mas vão mais além - disponibilizam uma máquina virtual inteira para cada programador ou projeto, que passam a serem usadas como parques de diversão particulares. Fácil trocar de Python 2.4 para 2.5, PHP4 para PHP5, RHEL para Gentoo. O custo pode ser baixo, tendo em vista a provável diminuição dos problemas na sustentação do ambiente.  
  
Tudo lindo, mas qual é o problema? O problema é que o Webmin (do qual Virtualmin é um módulo) tem um passado extenso de problemas de segurança. É um sistema extremamente complexo, com módulos pra se administrar de tudo, e com zilhões de controles de segurança necessários para manter a sanidade dos privilégios dos usuários do sistema, e de usuários "anônimos". Alguém sente cheiro de exploit remoto? Pois é, e em parte por causa disso o [webmin foi removido do Debian a partir do Etch](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343897) (e consequentemente do Ubuntu). [Já falei disso aqui](http://cetico.org/tech/2006/02/vulnerabilidade-congenita-em-software-para-sysadmin.html).  
  
Assim, o Webmin/Virtualmin é uma mão na roda, mas é preciso estar ciente dos riscos, ou a conveniência vira uma grande dor de cabeça. Se quiser entender o que estou falando, visite [http://www.securityfocus.com/bid](http://www.securityfocus.com/bid) e escolha o Vendor "Webmin".  
  
Aliás, eu posso depois traduzir as instruções de instalação e configuração do webmin e do virtualmin que eu linkei caso alguém tenha interesse.  
  
\[\]s
# Archived Comments
---
title: 'Virtualmin _pode_ ajudar sua vida'
date: 2007-06-02T20:57:00.000-07:00
draft: false
url: /2007/06/virtualmin-pode-ajudar-sua-vida.html
tags: 
- Tech Tip
- Debian
- Ubuntu
- Postfix
- sysadmin
---

#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-06-03T05:12:00.000-07:00">Jun 0, 2007</time>

_Comment from [Alexandro Silva](http://penguim.wordpress.com):_  
  
Olá Yves,  
  
Show de bola este artigo. Realmente o webmin é e sempre foi uma bomba relógio. raras foram as vezes que utilizei ele.  
Aproveitando o ensejo peço permissão para linkar a seção Now Reading no meu blog.  
  
Sds,  
  
Alex
<hr />
