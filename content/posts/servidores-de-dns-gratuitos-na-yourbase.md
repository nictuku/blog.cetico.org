---
title: 'Servidores de DNS gratuitos na YourBase'
date: 2007-08-22T19:37:00.000-07:00
draft: false
url: /2007/08/servidores-de-dns-gratuitos-na-yourbase.html
tags: 
- yourbase
- Tech
---

**Weblog da YourBase**  
  
Começarei a usar esta seção do meu blog (categoria "yourbase") como repositório de notícias _oficiais_ sobre a [YourBase](http://www.yourbase.com.br/).  
  
Aos clientes atuais, será útil como central de notícias sobre nossos serviços, incluindo anúncio de novas funcionalidades, avisos de manutenção, etc. Aos _clientes prospectivos_, espero que seja uma amostra sobre nosso "jeitão" de prestar um bom serviço. Aos demais (improváveis) leitores do blog, espero que não se incomodem com o novo conteúdo. Se for o caso, reclamem nos comentários.  
  
Para acompanhar os posts daqui pra frente, aponte seu leitor RSS para o endereço do nosso [feed](http://feed.feedburdner.com/CeticoorgYourbase), ou assine o [feed geral do cetico.org](http://cetico.org/tech/feed).  
**Novo Painel DNS _em testes_**  
  
O termo _beta_ está tão banalizado pelos serviços "web 2.0" ultimamente que prefiro dizer que o status da nova funcionalidade de gerenciamento de zonas DNS do painel de controle da [YB](http://www.yourbase.com.br) é _"em testes_".  
  
O serviço é gratuito e você pode configurar quantos domínios desejar, desde que numa quantidade razoável. (_Quem não é cliente e quiser usar nossos servidores de DNS, basta preencher o [cadastro de usuários](https://www.yourbase.com.br/novousuario) e seguir para o [painel de controle](https://www.yourbase.com.br/painel/)._)  
  
Durante a criação da zona do seu domínio, você tem a opção de escolher um IP padrão para o qual serão criados automaticamente registros como "www.dominio.com.br", "dominio.com.br" e uma entrada MX para o servidor de e-mail. Depois disso, é claro, você pode customizar a zona do seu domínio da forma que quiser. Finalmente, é só configurar o domínio no Registro.BR ou outro _registrar_, definindo NS1.YOURBASE.COM.BR e NS2.YOURBASE.COM.BR como servidores de nomes primário e secundário, respectivamente.  
  
É preciso notar que, apesar de flexível, a ferramenta ainda não é muito amigável para iniciantes, mas estamos trabalhando para melhorar a usabilidade. Em caso de dúvidas, entre em [contato](http://www.yourbase.com.br/sobre/#contato).  
  
**Infra-estrutura DNS**  
  
Para os geeks interessados, utilizamos o [PowerDNS](http://www.powerdns.com/) como servidor de DNS. É uma alternativa moderna se comparado ao bom e velho BIND. A vantagem do PowerDNS é que ele permite que sejam utilizados diversos back-ends diferentes para armazenar o "arquivo de zonas". No nosso caso, as zonas estão armazenadas em modo "NATIVE" em servidores MySQL com replicação automática. Em cima de tudo isso, uma interface escrita em Python com [TurboGears](http://www.turbogears.org) permite a administração de cada domínio de forma segura por cada usuário.  
  
Se quiser verificar nossa configuração padrão, consulte por exemplo o domínio "yvesjunqueira.com". Serviços recomendados: [Pingability.com](http://pingability.com) e [DNSReport.com](http://member.dnsstuff.com/pages/dnsreport.php).  
  
Os próximos passos são tornar a interface mais amigável e permitir a utilização de servidores secundários externos, mas ainda não há previsão de quando isso deve ficar pronto.  
  
**Sobre a Yourbase**A YourBase é uma empresa de hospedagem de servidores Linux com **acesso root**. Utilizamos Xen como tecnologia de virtualização e suportamos diversas aplicações e linguagens, como Ruby on Rails, TurboGears, Django, Drupal, Java, Python, PHP e Perl. Oferecemos [planos](https://www.yourbase.com.br/planos/) a partir de R$49.05.
# Archived Comments

#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-10-16T02:37:00.000-07:00">Oct 2, 2007</time>

_Comment from [Juliana](http://www.comerciodeubatuba.com.br):_  
  
Por gentileza estou precsando de uma hospedagem gratuíta para dois web sites  
  
www.comerciodeubatuba.com.br  
www.comerciodecaragua.com.br
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-06-25T08:52:00.000-07:00">Jun 3, 2008</time>

_Comment from [Fernando Correa](http://www.cordobel.com.br):_  
  
Que maravilha. Estou a dias procurando por um serviço de DNS gratuito e que o nome do servidor fosse aceito pela fapesp. O melhor de tudo é que achei muito fácil de configurar. Bom, já tenho uma certa experiência com hospedagem e estou familiarizado com configuração de dns, conheço os termos e tal.  
Para Juliana que procura por hospedagem gratuita, leia sobre o Google Apps em googgle.com.br/a.  
Foi conhecendo essa ferramenta do Google que me levou a comprar um domínio e procurar por um serviço de dns gratuito. Espero que continue sem gerar custo. mas se for preciso me disponho a contribuir anualmente.
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-06-25T08:55:00.000-07:00">Jun 3, 2008</time>

_Comment from [Fernando Correa](http://www.cordobel.com.br):_  
  
Aaa queria comentar mais uma coisa que me deixou muito contente com a YourBase.com.br. Painel em português e intuitivo.
<hr />
