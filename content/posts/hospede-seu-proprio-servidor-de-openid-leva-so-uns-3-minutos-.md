---
title: 'Hospede seu proprio servidor de OpenID. Leva so uns 3 minutos :-)'
date: 2008-01-21T14:13:00.000-08:00
draft: false
url: /2008/01/hospede-seu-proprio-servidor-de-openid.html
tags: 
- Tech Tip
- yourbase
- iniciantes
- Ubuntu
- openid
- sysadmin
---

O OpenID é um mecanismo de autenticação e autorização distribuído que começa a ser adotado pelos big players, como [Yahoo!](http://googlediscovery.com/2008/01/17/yahoo-comeca-a-implementar-openid/) e [Google](http://googlediscovery.com/2008/01/18/blogger-in-draft-blogger-torna-se-fornecedor-de-openid/).  
  
Logando-se apenas no seu provedor de OpenID, você pode criar novos perfis em outros sites **que o suportem**, ou fazer coisas que normalmente exigiriam autenticação, como deixar comentários em blogs, sem a necessidade de se logar novamente. E o principal é que **você não precisar criar um usuário e senha novamente em cada um dos sites que você visita**. W00t!  
  
Há várias opções de provedores de OpenID atualmente, e a tendência é que quase todo grande site (Google, Yahoo, UOL, sei lá) se torne provedor de OpenID. Alguns do mais populares hoje em dia são:  

  
*   [myopenid](http://www.myopenid.com/): utilizado por exemplo pelo [Christiano Anderson](http://christiano.blog.br/2008/01/18/utilizando-seu-proprio-dominio-como-openid/) (que aliás explica como manter um OpenID com seu nome de domínio, porém sem hospedá-lo no seu servidor, utilizando o [**own-id.com**](http://www.own-id.com)).
  
*   [wordpress.com](http://wordpress.com): basta utilizar "usuario.wordpress.com"
  
*   [blogger.com](http://googlediscovery.com/2008/01/18/blogger-in-draft-blogger-torna-se-fornecedor-de-openid/)
  

  
Veja aqui uma lista com [vários outros provedores públicos de OpenID](http://wiki.openid.net/OpenIDServers).  
  
Mas, bem, você que é um über-geek certamente vai preferir hospedar seu próprio mecanismo de OpenID, certo :-) ? Assim, além de ter um openID com o seu domínio, você está garantindo que só você sabe sua senha. A forma mais simples de se fazer isso é usando o [phpMyID](http://siege.org/projects/phpMyID/).  
  
Tenha em mente que os sites não são obrigados a aceitar seu OpenID. Mas a previsão é que seja criada uma _whitelist_ de provedores de OpenIDs _do bem_.  
  
Veja só como fazer o seu servidor de OpenID no Linux, usando apenas dois arquivos em PHP:  
  
  
Supondo que você já tenha um servidor rodando PHP, vá até o [site do projeto](http://siege.org/projects/phpMyID/) e baixe a última versão. Descompacte o 'tarball' e copie para o diretório onde ficará hospedado seu openid apenas os arquivos 'MyID.php' e 'MyID.config.php'. Neste exemplo, vou deixar os arquivos em /var/www/html/openid:  

> \# wget http://siege.org/projects/phpMyID/phpMyID-0.8.tgz  
>   
> \# tar zxvf phpMyID-0.8.tgz  
>   
> \# mkdir /var/www/openid  
>   
> \# mv phpMyID-0.8/MyID.php /var/www/openid

  
Renomeie o 'MyID.config.php' para 'index.php':  

> \# mv phpMyID-0.8/MyID.config.php /var/www/openid/index.php

  
Pronto, agora é só editar o _/var/www/openid/index.php_. Nesse arquivo, há duas arrays com as configurações relevantes: 'profile' e 'sreg'. Veja abaixo um exemplo com os itens mais importantes e uma explicação de cada item:  
  
$GLOBALS\['profile'\] = array(  
\# Basic Config  
'auth\_username' => 'yves',  
'auth\_password' => '37fa04faebe5249023ed1f6cc867329b',  
'auth\_realm' => 'cetico',  
\# Optional Config - Please see README before setting these  
#'microid' => array('user@site.com', 'http://delegator.url'),  
'pavatar' => 'http://cetico.org/pavatar.png',  
  
);  

  
*   **auth\_username**: é o nome de usuário a ser utilizado quando você se logar no seu openID. Escolha um valor e não mude.
  
*   **auth\_password**: é o hash criptográfico da sua senha. Deixe como está e vamos falar disso por último.
  
*   **auth\_realm**: na prática, é apenas o título da caixa diálogo para entrada de usuário e senha. Escolha um valor e não mude.
  
*   **pavatar** é um 'gravatar', porém hospedado no seu próprio servidor. É bem menos suportado do que o Gravatar.
  

  
Faltam agora a outra parte, o 'sreg'. Essas variáveis são importantes pois serão os dados informados aos outros sites. Ao fazer um comentário no blogger usando seu OpenID, por exemplo, o nome e o nickname que vão aparecer são os que você definir aqui.  
  
/\*\*  
\* Simple Registration Extension  
\* @name $sreg  
\* @global array $GLOBALS\['sreg'\]  
\*/  
$GLOBALS\['sreg'\] = array (  
'nickname' => 'cetico',  
\# 'email' => 'yves@cetico.org',  
'fullname' => 'Yves Junqueira',  
\# 'dob' => '1970-10-31',  
'gender' => 'M',  
\# 'postcode' => '22000',  
\# 'country' => 'US',  
\# 'language' => 'en',  
\# 'timezone' => 'America/New\_York'  
);  

  
*   **nickname**: Importante: é o que deve aparecer na maioria das vezes
  
*   **fullname**: Importante
  
*   **email**: opcional
  
*   **dob**: data de nascimento. opcional.
  
*   O restante é óbvio e opcional.
  

  
Definindo a senha:  
  
Lá atrás, deixamos o campo "auth\_password" inalterado. Agora está na hora de configurá-lo. O procedimento é simples. Basta concatenar o nome de usuário, o realm e a senha, separados por dois pontos ":" e calcular o hash md5. Supondo que minha senha seja _T4B4j4rA_, é só executar o seguinte comando no Linux:  
  
$ echo -n 'yves:cetico:T4B4j4rA' | md5sum  
7f88f2da9a2b54eedc5f62bad9c17058 -  
  
Pegue o resultado, nesse caso "7f88f2da9a2b54eedc5f62bad9c17058" (o seu, claro, vai ser bem diferente) e coloque no campo "auth\_password". Lembre-se de cercar essa string por aspas simples e incluir uma vírgula depois.  
  
Salve o arquivo e vá até a página onde deve estar seu openid. Já deve estar funcionando. Se não funcionar contigo, deixe um recado aqui. Não posso prometer, mas vou tentar ajudar.  
  
Lembre-se de ser gentil com quem acessa seu blog, permitindo que eles façam comentários autenticando-se com suas respectivas OpenIDs. [Fazer isso no Wordpress é fácil](http://wordpress.org/extend/plugins/openid/) e certamente outros sistemas já devem estar se adaptando aos novos tempos.
# Archived Comments

#### _Comment from[](http://gutocarvalho.net)_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-01-22T05:52:00.000-08:00">Jan 2, 2008</time>

_Comment from [guto](http://gutocarvalho.net):_  
  
Excelente dica Yves, eu uso openid do myopenid no trac do SACIX Gnu/Linux e GESAC Gnu/Linux, é bem prático mesmo ;)  
  
Sucesso em BH.  
  
\[s\]  
Guto
<hr />
#### _Comment from_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-05-27T23:55:00.000-07:00">May 3, 2008</time>

_Comment from [Leonardo Priori](http://www.leonardopriori.com):_  
  
o link site do projeto tá errado, dá uma olhada ae, tem um http// a mais ae
<hr />
#### Valeu, Leonardo. Vou corrigir.
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2008-05-28T15:53:00.000-07:00">May 3, 2008</time>

Valeu, Leonardo. Vou corrigir.
<hr />
