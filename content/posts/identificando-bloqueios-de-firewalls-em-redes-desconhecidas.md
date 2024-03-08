---
title: 'Identificando bloqueios de firewalls em redes desconhecidas'
date: 2007-08-30T17:26:00.000-07:00
draft: false
url: /2007/08/identificando-bloqueios-de-firewalls-em.html
tags: 
- Tech Tip
- yourbase
- Ubuntu
- artigo
- Tech
---

Nem sempre é fácil para os administradores de redes identificar onde pacotes estão sendo bloqueados, principalmente em redes desconhecidas e com firewalls sob controle de terceiros. Este artigo explica uma das técnicas que podem ajudar nessa tarefa, explorando um recurso padrão do protocolo IP de forma semelhante ao funcionamento do _traceroute_.  
  
Recentemente um cliente reclamou que não conseguia conectar-se ao servidor dele, em nenhuma porta. O tempo da conexão sempre expirava (_timeout_) antes de conectar. Como eu conheço a rede onde ficam os servidores, de início achei improvável que houvesse algum problema 'do lado de cá'.  
  
Entretanto, já vi muita coisa estranha acontecendo, geralmente por culpa de firewalls mal configurados. Nunca cheguei a ver os problemas mais bizarros relatados web afora, como [detecção incorreta de path MTU](http://www.netheaven.com/pmtu.html), ou incompatibilidades com dispositivos antigos por causa de recursos 'novos' do TCP ([ECN](http://urchin.earth.li/ecn/) etc). Mas talvez fosse o caso. De qualquer forma, precisávamos diagnosticar onde essas conexões estavam parando.  

[![google-firewall](http://farm2.static.flickr.com/1341/1297485438_47dd54f42e_o.png "google-firewall")](http://www.flickr.com/photos/93543981@N00/1297485438/ "Photo Sharing")

  
[](http://www.flickr.com/photos/93543981@N00/1297721766/ "Photo Sharing")  
  

Diagrama hipotético - desenhado no [Dia (GNOME)  
](http://live.gnome.org/Dia)  
  
E então as ferramentas tracetcp, traceproto ou tcptraceroute vieram ajudar a salvar o dia. São ferramentas simples que podem ser usadas para se detectar firewalls . Há versões para Linux, Windows e, suponho, outros SOs. Para Windows, recomendo o [tracetcp](http://tracetcp.sourceforge.net/index.html). Em Linux, há vários sabores, mas costumo usar o [traceproto](http://traceproto.sourceforge.net/index.php). O funcinamento é parecido com o do traceroute: (continua abaixo) Como muita gente sabe, o traceroute funciona enviando pacotes UDP para o host de destino, mas com um valor baixo para o campo "TTL" (tempo de vida) do cabeçalho IP.  
  
Para evitar loops, todo roteador IP diminui o valor do TTL de todos pacotes que passem por ele. Se por acaso esse valor chegar em 0 enquanto trafega na rede, o roteador em questão emitirá uma mensagem ICMP informando ao host de origem que o tempo excedeu e descarta o pacote. Assim, o traceroute consegue identificar até onde o pacote passou, olhando a origem dessa mensagem ICMP. Depois repete o processo, porém com um TTL maior.  
  
Incrementar o TTL em um faz com que o roteador seguinte retorne o erro ICMP. Dessa forma, repetindo o processo, o traceroute consegue identificar salto-a-salto todos os roteadores envolvidos no caminho entre o host local e o remoto.  
  
O tracetcp/traceproto/tcptraceroute faz a mesma coisa, mas você escolhe qual porta e protocolo vai usar (UDP, TCP, etc). Assim, se suas conexões estiverem sendo bloqueadas em algum ponto desconhecido, mas isso acontece apenas em algums portas e outras não, usando essas ferramentas é possível dizer com certeza quais roteadores e redes **não bloquearam o pacote** - já que se o roteador retornou erro, significa que o pacote com certeza chegou até ele. Portanto o problema está dali pra frente :-).  
  
Vou detalhar um exemplo bizarro para ilustrar a questão. Suponha que você trabalhe no Google e tenha acesso direto via SSH ao **www.google.com** (e claro, acesso aos outros [450.000 servidores](http://en.wikipedia.org/wiki/Google_platform) também!!), mas ao tentar abrir uma conexão na porta TCP:22, dá _timeout_. Onde está o problema? Pode ser no modem/roteador da sua casa, no roteador da BrasilTelecom/Telemar/etc/etc... ou no próprio firewall do Google.  
  
Vamos usar o traceproto para identificar qual firewall/roteador provavelmente não está permitindo a sua conexão. (Estou usando -H 1 para simplificar o exemplo, mas lembre que a cada tentativa a rota pode mudar, isso é normal. Eu tive que repetir os testes várias vezes até conseguir uma rota semelhante para os dois casos. Portanto essa técnica funciona melhor para diagnosticar problemas em uma rede pequena sem múltiplos caminhos.)  
  
Primeiro, vejamos uma conexão que funciona (os comentários na segunda coluna são meus):  
  
[![gfirewall1](http://farm2.static.flickr.com/1086/1297721766_9eb70d104e_o.png)](http://www.flickr.com/photos/93543981@N00/1297721766/ "Photo Sharing")  
  

Tudo OK:  
conexão estabelecida com o host final.  

Na figura anterior, o código ITX significa "ICMP Time Exceeded". Quer dizer que o pacote chegou naquele roteador com TTL=0, portanto ocorreu um erro. Na última linha, vemos o código TSA - que significa "TCP SYN ACK" que podemos interpretar como "conexão pronta para ser estabelecida". Note que esses dois códigos não são de uso geral na área de redes, sendo usados pelo tracepoto apenas para mostrar mostrar uma relatório mais compacto.

  

Agora, vejam uma tentativa de conectar à porta 22:

  
  

[![gfirewall2](http://farm2.static.flickr.com/1053/1297721164_580e205240_o.png "gfirewall2")  
](http://www.flickr.com/photos/93543981@N00/1297721164/ "Photo Sharing")Sem resposta ao pedido.  
Último roteador respondendo: 4.68.16.3[  
](http://www.flickr.com/photos/93543981@N00/1282513976/ "Photo Sharing")  
  
Percebam que a requisição só recebe resposta (nesse caso, na verdade, uma mensagem ICMP de tempo excedido) de alguns roteadores. Depois disso, nosso pacote parece ser descartado (0.0.0.0 em diante).  
  
Além de verificarmos que há servidores do Google em Nova York (onde pelo que sei os custos de banda de rede são muito baixos), o que esse resultado nos diz? Com alguma imaginação, podemos **supor** que o próximo salto deveria ser o "4.71.172.86", com nome de "GOOGLE-INC.car1.NewYork1.Level3.net". Mas não recebemos resposta (na realidade, uma mensagem de erro) desse roteador. É possível que este host seja o firewall _dropando_ os pacotes, ou pode ser que o firewall esteja antes dele. Isso condiz, aliás, com o nome do roteador - que aparentemente é o "roteador de borda" do Google para conexões vindas da rede da Level3.  
  
A conclusão desse _troubleshooting_ é que agora você sabe pra quem deve ligar pra ter seu acesso ao SSH do Google liberado outra vez. :-)  
  
No caso do meu cliente que não conseguia se conectar ao servidor dele, o problema era mais simples. Ele usou o tracetcp no Windows e recebeu a seguinte mensagem:  

> **\> tracetcp.exe example.com:80** Socket::connect: Connection refused

  
Ou seja, não apareceu nenhum roteador respondendo. Conclusão: o firewall local da máquina ainda tinha uma regra "escondida" em algum lugar fazendo esses bloqueios, foi só desligar e problema resolvido.  
  
Quem dera eu soubesse essa técnica antes, quando o firewall mal configurado de uma prestadora de serviços de _data center_ do qual [éramos](http://planet.core.eti.br) clientes freqüentemente bloqueava tráfego de forma obscura e não solicitada. Poderia ter ajudado a resolver o empurra-empurra mais rapidamente.  
  
Espero que isso seja útil para outros colegas sysadmins.  
  
Outras referências:  

  
*   página de manual do traceroute
  
*   [site do tracetcp](http://tracetcp.sourceforge.net/)
  
*   [TCP/IP Illustrated, Volume 1: The Protocols](http://www.librarything.com/work/13011&book=20479144)
# Archived Comments
---
title: 'Identificando bloqueios de firewalls em redes desconhecidas'
date: 2007-08-30T17:26:00.000-07:00
draft: false
url: /2007/08/identificando-bloqueios-de-firewalls-em.html
tags: 
- Tech Tip
- yourbase
- Ubuntu
- artigo
- Tech
---

#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-08-31T01:59:00.000-07:00">Aug 5, 2007</time>

_Comment from [Alexandro Silva](http://penguim.wordpress.com):_  
  
Putz cara!!!  
  
Show de bola, excelente explicação.  
  
Já está rolando o aptitude install!!!
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-08-31T02:19:00.000-07:00">Aug 5, 2007</time>

_Comment from [Cesar Cardoso](http://fudeblog.zyakannazio.eti.br):_  
  
Opa, certamente é muito útil, particularmente na hora de comprovar que alguém fez m\* no roteamento e coisas do tipo.  
  
Valeu pela dica! :D
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-09-02T10:15:00.000-07:00">Sep 0, 2007</time>

_Comment from [Nelson Junior](http://warlinux.blogspot.com):_  
  
Realmente ferramentas excelentes, e irei usar bastante daqui pra frente para comprovar que fizeram o que disse acima m\*  
  
Pena que fui saber somente depois que ficamos quase dois dias sem e-mail por problemas de roteamento, hehhee  
  
Falow abraços
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-09-03T04:42:00.000-07:00">Sep 1, 2007</time>

_Comment from [jalexandre](http://www.midstorm.org/~jalexandre/blog):_  
  
\+ uma ferramenta de troubleshooting de redes na minha lista =)  
  
\[ \] 's
<hr />
#### _Comment from Marcelo Lemos:_ Muuuito útil...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-09-04T03:12:00.000-07:00">Sep 2, 2007</time>

_Comment from Marcelo Lemos:_  
  
Muuuito útil.. principalmente pra lidar com AQUELA prestadora de serviços de data center extremamente competente :)
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-09-04T13:35:00.000-07:00">Sep 2, 2007</time>

_Comment from [Wagner Elias - Think Security First » links for 2007-09-04](http://wagnerelias.com/2007/09/04/links-for-2007-09-04/):_  
  
\[...\] Identificando regras de firewall Post sobre técnicas para identificar/enumerar regras de firewall (tags: Firewall pentest) \[...\]
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-01-09T06:30:00.000-08:00">Jan 3, 2008</time>

_Comment from [la règle poker](http://www.lacoctelera.com/melvin8707/post/2008/01/03/business-card-credit-reward-travel-business-card-credit-free):_  
  
**polyphone klingeltöne polyphone klingeltöne panasonic polyphone klingeltöne samsung...**  
  
Similarly prepaid credit card canada klingelton...
<hr />
#### _Comment from [francsco ...](http://137494)_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-01-12T11:11:00.000-08:00">Jan 6, 2008</time>

_Comment from [francsco tourinho filho](http://137494):_  
  
meu emule esta bloquado queria saber como faço ele não está conectando o KAD
<hr />
#### _Comment from [fra...](javascript:void(0);)_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-01-12T11:12:00.000-08:00">Jan 6, 2008</time>

_Comment from [francsco tourinho filho](javascript:void(0);):_  
  
meu KAD do emule não está se conectando como faço pra conectalo
<hr />
#### The En Prison rule is much like the La Partage rul...
[Anonymous]( "noreply@blogger.com") - <time datetime="2022-12-08T00:04:42.548-08:00">Dec 4, 2022</time>

The En Prison rule is much like the La Partage rule, except that as an alternative of receiving half the bet back, the dealer will hold half of your bet in the identical spot for the following spin. You have discovered the fundamentals of the net sport roulette; now, you need to|you should|you have to} know the way to|tips on how to} start putting bets. Many bets may be placed, all of which carry different odds and affect on} your probabilities of winning and the amount [온라인카지노](https://bet.edu.kg/online-casino) of cash you can to|you presumably can} win. The sport is played on a roulette desk with a giant wheel on one aspect. There is a giant grid pattern on the desk with numbers, and the wheel has pockets with the identical corresponding numbers. Half of the numbers are black, and half are purple, however more about that in a second.
<hr />
