---
title: 'Desenvolvimento de sites rápidos e err, &quot;poderosos&quot;, com Catalyst'
date: 2006-07-29T18:30:00.000-07:00
draft: false
url: /2006/07/desenvolvimento-de-sites-rpidos-e-err.html
tags: 
- Ubuntu
- Catalyst
---

O [Catalyst](http://www.catalystframework.org/) é um "Web Framework" em Perl. Você pode entendê-lo como um concorrente do Ruby on Rails e do TurboGears - baseados em Ruby e em Python, respectivamente. Apesar de novo, ele é robusto e confiável, e deve disputar as atenções daqui pra frente. Nesse artigo, mostrarei como montar um site com controle de banco de dados em alguns minutos, usando Catalyst. Veja o resultado após alguns minutos de trabalho, e sem escrever nenhuma linha de código:  

![cetico-catalyst1.png](http://www.cetico.org/tech/wp-content/uploads/2006/07/cetico-catalyst1.png)

  
Veja abaixo o tutorial, com apenas 2 passos a seguir.  
  
  
**INTRODUÇÃO** (pule se estiver com pressa)  
  
O Catalyst é uma bela solução, com qualidades típicas do Perl: flexibilidade e agilidade. Iniciantes podem se sentir intimidados com as diversas formas de fazer a mesma coisa ([TMTOWTDI](http://catb.org/jargon/html/T/TMTOWTDI.html)), ou com a monstruosa quantidade de módulos do Perl e de Plugins do Catalyst disponíveis. A tendência é que a curva de aprendizado do Catalyst seja um pouco mais acentuada que a dos concorrentes, mas o resultado final é a um poder maior sobre a ferramenta e, especialmente, mais produtividade.  
  
O Catalyst disponibiliza uma infra-estrutura básica, e lhe é dado o poder de mexer e desmontar o que você precisar. Se quiser deixar de usar DBIC (DBIx::Class) para manipular dados, basta escolher outro módulo. Além disso, o Catalyst, por ser Perl, tem melhor suporte a UTF-8 que o concorrente mais conhecido, o Ruby on Rails. Diferentemente do RoR, o Cat suporta chaves primárias de múltiplas colunas, graças ao DBIC, entre outros "poderes" e vantagens técnicas.  
  
Para compensar a talvez excessiva diversidade de módulos e alternativas, e a confusão que iniciantes fazem com isso, o projeto Catalyst tem se esforçado para criar boa documentação. A principal documentação para iniciantes é o Catalyst::Manual::Tutorial, que pode ser lido juntamente com os comentários (geralmente muito úteis) de outros usuários no [annoncpan.org](http://www.annocpan.org/pod/Catalyst::Manual::Tutorial).  
  
O [wiki](http://dev.catalyst.perl.org/) é um excelente recurso, bem organizado e com muita informação. Por último, no canal #catalyst do irc.perl.org é possível obter ajuda, em inglês, de outros usuários - extraordinariamente simpáticos, por sinal.  
  
**CRIAÇÃO DE UM SITE RÁPIDO**  
  
Nesse tutorial, irei relatar o passo-a-passo do desenvolvimento inicial de um sistema real - o PF-Graph, uma ferramenta de análise de logs e auditoria para o sistema de e-mail Postfix.  
  
0) **Instalação do Catalyst**  
  
No Ubuntu (estou utilizando o Edgy Eft), o processo de instalação do Catalyst é simples, como sempre.  

> sudo aptitude install libcatalyst-perl libcatalyst-modules-extra-perl libcatalyst-model-dbic-perl libcatalyst-view-tt-perl libcatalyst-modules-perl

  
Alguns módulos não estão empacotados ainda, portanto devem ser instalados via CPAN:  

> sudo perl -MCPAN -e 'force install("Catalyst::Example::InstantCRUD")'

  
Sugiro responder "no" à primeira pergunta para simplificar a configuração do ambiente do CPAN.  
  
Se você tiver problemas, deixe um comentário e tentarei ajudar.  
  
Esse módulo [InstantCRUD](http://search.cpan.org/~zby/Catalyst-Example-InstantCRUD-v0.0.10/script/instantcrud.pl) faz a mágica por nós, criando automaticamente o site e os métodos geralmente utilizados para manipulação de um banco de dados - por isso é um "CRUD framework". CRUD significa "Create, Read, Update and Delete", ou "Criar, Ler, Atualizar e Apagar". O resultado é uma interface agradáveç que serve como ponto de partida do seu trabalho. É o InstantCRUD que gera o View, portanto os templates, da página mostrada anteriormente na screenshot. Veja a como é fácil chegar até lá, seguindo os próximos 6 simples passos. Os comandos a serem digitados estão destacados em itálico.  
  
1) **Configuração do banco de dados  
**Iremos utilizar o SQLite pela simplicidade, mas você pode usar outro qualquer suportado pelo DBI do Perl. A fama do DBI é que você pode guardar suas informações em qualquer lugar, incluindo PostgreSQL, MySQL, arquivos CSV, Excel, cartola de mágico, etc etc. Veja a [lista de drivers](http://search.cpan.org/search?query=DBD%3A%3A&mode=module) no CPAN.  
  
O arquivo maillog.db é um banco de dados SQLite. Grave em um arquivo com nome maillog.sql o seguinte conteúdo:  

> BEGIN TRANSACTION;  
> CREATE TABLE blockedmail (id INTEGER PRIMARY KEY,  
> timestamp INTEGER,  
> clientdns VARCHAR(255), clientip  
> VARCHAR(15), sender varchar(255),  
> rcpts BLOB, helo VARCHAR(32),  
> restriction\_applied VARCHAR(32),  
> detail VARCHAR(255));  
> CREATE TABLE maillog (id INTEGER PRIMARY KEY,  
> timestamp INTEGER,  
> host TEXT,  
> program TEXT,  
> pid INTEGER,  
> text TEXT);  
> CREATE TABLE mailtraffic (id INTEGER PRIMARY KEY,  
> timestamp INTEGER,  
> sender VARCHAR(255), rcpts TEXT,  
> bytes\_rcvd INTEGER  
> );  
> INSERT INTO "mailtraffic" VALUES(1, 1154232272, 'john@example.com', 'yves@cetico.org', 1231321);INSERT INTO "mailtraffic" VALUES(2, 1154232574, 'john@example.com', 'yves@cetico.org', 838334);  
> INSERT INTO "mailtraffic" VALUES(3, 1154232630, 'yves@cetico.org', 'amanda@example.com', 65333);COMMIT;

  
Depois, crie o banco executando (você precisa do sqlite3):  

> yves@elvis:~/catalyst$ sqlite3 maillog.db < maillog.sql

  
Teste se está tudo em seu devido lugar com o comando:  

> _yves@elvis:~/catalyst$ sqlite3 maillog.db .dump_

  
2) **Crie seu site  
**  

> _yves@elvis:~/catalyst$ instantcrud.pl -name=pfgraph \\ -dsn='dbi:SQLite:dbname=maillog.db'  
> _created "pfgraph"  
> created "pfgraph/script"  
> created "pfgraph/lib"  
> ...  
> dir: /home/yves/catalyst/pfgraph/root/static  
> created "/home/yves/catalyst/pfgraph/root/static/pagingandsort.css"  
> created "pfgraph/script/../t/controller\_InstantCRUD.t"

  
Mova o maillog.db para o diretório criado - no caso, "pfgraph":  

> _yves@elvis:~/catalyst$ mv maillog.db pfgraph/_

  
3) **Tudo pronto!**  
  
Rode o servidor:  

> yves@elvis:~/catalyst/pfgraph$ script/pfgraph\_server.pl

  
Abra agora seu navegador e aponte para http://localhost:3000. Veja o resultado:  
  
Visualização da lista de e-mails recebidos e enviados (método "list"):  

![cetico-catalyst1.png](http://www.cetico.org/tech/wp-content/uploads/2006/07/cetico-catalyst1.png)[  
](http://www.cetico.org/tech/wp-content/uploads/2006/07/catalyst2.png "catalyst 2")

  
Visualização de um item específico:  
  
  
  
  

![cetico-catalyst2.png](http://www.cetico.org/tech/wp-content/uploads/2006/07/cetico-catalyst2.png)

  
[  
](http://www.cetico.org/tech/wp-content/uploads/2006/07/catalyst3.png "catalyst 3")  

Edição de itens:

  

  
  

![cetico-catalyst3.png](http://www.cetico.org/tech/wp-content/uploads/2006/07/cetico-catalyst3.png)

  

O InstantCRUD faz o scaffold do MVC, isso é, gera explicitamente o código para cada método utilizado, cabendo a você, agora, adaptar os Modelos, as Aprestanções e os Controles. É mais fácil mexer em algo pronto do que ter que escrever do zero, pelo menos para iniciantes.

  

O Catalyst e o InstantCRUD nos forneceram um sistema moderamente complexo, mas sem termos escrito nenhuma nova linha de código. Isso é muito cômodo, mas não se engane: mesmo que você use um framework que lhe poupe boa parte do trabalho inicial, nada substitui seu próprio estudo e prática. É necessário dominar a linguagem (para isso, recomendo Learning Perl e Programming Perl) e seguir boas práticas de desenvolvimento. Performance deve ser uma preocupação constante de um bom desenvolvedor.

  

Aliás, falando de performance, o Catalyst atende todos os gostos. Para desenvolvimento, você pode usar o servidor HTTP::Daemon próprio, como fizemos aqui, mas para o ambiente de produção recomenda-se Apache+FastCGI ou mod\_perl. Fica uma bala. Veja o [Cookbook](http://search.cpan.org/~mramberg/Catalyst-Runtime-5.7001/lib/Catalyst/Manual/Cookbook.pod#Deployment).

  

Num próximo post, continuarei o desenvolvimento do PF-Graph mostrando buscas específicas, autenticação e tentarei usar alguns gráficos bonitinhos :-).
# Archived Comments

#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-07-30T04:37:00.000-07:00">Jul 0, 2006</time>

_Original comment from: [Fábio Nogueira](http://barraroumi.wordpress.com)_  
  
Grande Yves.. blza?  
Parabéns pela dica.. bem detalhada.  
Outra coisa.. tu é fã do Elvis?!? Então são dois...  
Caso utilize o Orkut.. procura pela comunidade Elvis Presley (Brazil) .. é a minha comunidade em homenagem ao Rei. (A maior do Orkut)  
\[\]'s
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-07-30T04:54:00.000-07:00">Jul 0, 2006</time>

_Original comment from: [Fábio Nogueira](http://barraroumi.wordpress.com)_  
  
Yves...  
Ao executar:  
sudo perl -MCPAN -e ‘force install(”Catalyst::Example::InstantCRUD”)’  
Dá um erro:  
erro de sintaxe próximo a símbolo inesperado \`('  
And now? The end is near?!  
:)
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-07-30T08:29:00.000-07:00">Jul 0, 2006</time>

_Original comment from: [cetico](javascript:void(0);)_  
  
Uai. Será que você copiou certo?  
  
depois de -e tem um aspas simples, entre os ( ) tem aspas duplas, e no final aspas simples.  
  
Aqui dá certo.
<hr />
#### _Original comment from: Andre Ferraz_ Bom ...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-07-30T11:06:00.000-07:00">Jul 0, 2006</time>

_Original comment from: Andre Ferraz_  
  
Bom post o seu, tinha curiosidade de conhecer algo sobre o framework e nunca achei coisas em portugues espero que voce escreva mais !  
  
abraços
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-08-09T09:17:00.000-07:00">Aug 3, 2006</time>

_Original comment from: [SiTeS Rj](http://www.fasites.com.br)_  
  
gostei muito das informações apresentadas. me ajudaram..
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-08-09T21:12:00.000-07:00">Aug 4, 2006</time>

_Original comment from: [coredump](http://core.eti.br)_  
  
Deus do ceu... Use Turbogears... :P
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-08-16T06:44:00.000-07:00">Aug 3, 2006</time>

_Original comment from: [Lorn](http://www.lornlab.org)_  
  
Parabéns, muito legal o tutorial  
Comecei a brincar com o Catalyst também, apareceu um cgi simples para fazer, resolvi entender o tal do MVC e o Catalyst.  
Só uma duvida voce alimenta esse maillog.db com outro script certo?  
O Catalyst só le o que tá nele?  
Falow
<hr />
#### _Original comment from: Mauricio_ Yves!!! ...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-09-21T18:06:00.000-07:00">Sep 5, 2006</time>

_Original comment from: Mauricio_  
  
Yves!!!  
Legal, sempre achei Scaffold Programming interessante!!!!  
  
Temos um em Java tb. :-)  
http://www.trailsframework.org/  
  
Da uma olhada!
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-04-28T16:36:00.000-07:00">Apr 0, 2007</time>

_Original comment from: [victor](http://www.playstation.net)_  
  
é massa
<hr />
#### De grande valia o post! Meus parabéns! Sucesso!
[Anonymous]( "noreply@blogger.com") - <time datetime="2008-12-17T18:06:00.000-08:00">Dec 4, 2008</time>

De grande valia o post! Meus parabéns! Sucesso!
<hr />
