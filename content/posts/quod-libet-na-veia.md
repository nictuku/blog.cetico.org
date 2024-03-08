---
title: 'Quod Libet na veia'
date: 2006-02-28T13:21:00.000-08:00
draft: false
url: /2006/02/quod-libet-na-veia.html
tags: 
- Ubuntu
---

Depois de ameaçar São Longuinho de morte várias vezes, finalmente encontrei.Só com a dica do _rockz_ da Freenode achei **um programa alternativo ao Amarok, pro GNOME**. O Quod Libet, além de não depender de nada QT, é escrito em Python e PyGTK.  

[![Quod Libet](http://www.cetico.org/tech/wp-content/uploads/2006/02/Captura_da_tela-2.thumbnail.png)](http://www.cetico.org/tech/2006/02/quod-libet-na-veia.html/quod-libet/ "Quod Libet")

  
Ele tem todas as funcionalidades do Amarok que eu utilizava: baixa letras da internet (e salva!), baixa figura do álbum, visualiza informações na Wikipedia. Tem também outras coisas muito boas, como o sistema de organização e edição de tags "em batch". É muito mais organizado e os modos de reprodução dele são bem mais inteligentes, inclusive.  
  
O Quod Libet é tão promissor que a comunidade tentou melhorá-lo - HEHEHE. Foi baseado no Quod Libet que um sonso escreveu o [listen](http://listengnome.free.fr/ "Listen para Gnome") - só esqueceu de dar o devido crédito ao autor. Foi uma confusão digna de PSL-Brasil. Deve ter sido a violação de GPL mais mocoronga da história.  
  
Veja a seguir instruções de instalação do Quod Libet.  
  
  
  
O Quod Libet está nos repositórios do Debian e do Ubuntu, mas em versões mais antigas.  
  
Baixe a última versão do Quod Libet para sua máquina:  
  
wget http://www.sacredchao.net/~piman/software/quodlibet-0.17.1.tar.gz  
  
Expanda o tarball:  
  
tar zxvf quodlibet-0.17.1.tar.gz  
  
Mova o diretório para /usr/local/share:  
  
mv quodlibet-0.17.1 /usr/local/share/  
  
"Instale" os executáveis do quodlibet e do exfalso (para um editor de tags independente do quodlibet):  
ln -s /usr/local/share/quodlibet-0.17.1/quodlibet.py /usr/local/bin/quodlibet  
ln -s /usr/local/share/quodlibet-0.17.1/exfalso.py /usr/local/bin/exfalso  
Crie um ícone no menu do seu GNOME ou no Desktop e pronto.  
  
Você pode, e eu recomendo, entretanto, que você baixe os plugins também:  
  
cd /usr/local/share/quodlibet-0.17.1/  
mkdir plugins-svn ; cd plugins-svn  
svn co http://svn.sacredchao.net/svn/quodlibet/trunk/plugins  
Com o usuário sem privilégios (não-root), copie os plugins que você precisa, ou todos, para o seu ~/.quodlibet/plugins:  
$ cp \*.py ~/.quodlibet/plugins/  
  
Recomendo em especial os plugins para baixar capas de álbuns da Amazon, para pegar informações pela Wikipedia, o Animated OSD, além do QLScrobbler, que integra o Quod Libet com o [last.fm](http://www.last.fm/user/yvesjm/).  
  
É isso e depois mandar seu Amarok e KDE pro lixo:  
  
sudo apt-get remove kdelibs-bin # (observação: Isso removerá seu KDE. O que é bom, vamos concordar)  
  
\[\[End Of World\]\]
# Archived Comments
---
title: 'Quod Libet na veia'
date: 2006-02-28T13:21:00.000-08:00
draft: false
url: /2006/02/quod-libet-na-veia.html
tags: 
- Ubuntu
---

#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-02-28T14:20:00.000-08:00">Feb 2, 2006</time>

_Original comment from: [Leandro Santoro](http://whatever.blog.terra.com.br)_  
  
Por isso que eu sou fã de carterinha do Yves.  
Vou tentar isso amanhã mesmo. Aí só falta me livrar do k3b e estou livre do kde para sempre.  
  
Abr,  
Leandro Santoro.
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-02-28T15:58:00.000-08:00">Feb 2, 2006</time>

_Original comment from: [Cesar Cardoso](http://fudeblog.zyakannazio.eti.br)_  
  
O problema do Listen é que o bicho é ruim. Horroso. Estupra qualquer tentativa do HIG. Não dá pra levar a sério qualquer programa que não tenha um mínimo de preocupação com a usabilidade.
<hr />
#### Leandro, quando você testar digai se você gostou. ...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-02-28T16:05:00.000-08:00">Mar 3, 2006</time>

Leandro, quando você testar digai se você gostou. A interface é menos lotada de coisa e, portanto, leva-se mais tempo pra se chegar onde quer, mas eu gosto disso, se é pra ser clean...  
  
Cesar, você não gosta do listen pq? Eu não conheci. Já testou o quod libet? (cara, não decoro esse nome nunca).
<hr />
#### _Original comment from:_
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-08-06T06:37:00.000-07:00">Aug 0, 2006</time>

_Original comment from: [Nome](http://website.com)_  
  
O QLScrobbler está com bug.  
  
Não toca CDs de Audio.  
  
Talvez fique melhor na próxima versão.
<hr />
#### _Original comment from: Alan Dantas_ Eu ut...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2006-09-03T07:12:00.000-07:00">Sep 0, 2006</time>

_Original comment from: Alan Dantas_  
  
Eu utilizo Ubuntu Dapper Drake e instalei uma versão antiga do Quod Libet (0.18) porque ainda desconheço as novas funcionalidades e correções acrescentadas ao reprodutor de áudio.  
  
Quais são as vantagens de instalar a versão mais nova do Quod Libet?
<hr />
#### _Original comment from: jose eduardo_ Aten...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-08-30T07:51:00.000-07:00">Aug 4, 2007</time>

_Original comment from: jose eduardo_  
  
Atenção galera,  
  
Não tenho muita experiencia para baixar os softwares e o site sacredchao não exite mais. Como baixar o Quod Libet? Esse programa serve para catalogar musicas classicas? Permite importação de outras pastas? A pergunta é pertinente pois tenho cerca de 1500 albuns e isso aqui está uma confusao só.  
Grato a quem possa me ajudar.  
  
jose
<hr />
#### José, veja http://www.sacredchao.net/quodlibet O ...
[Yves Junqueira](https://www.blogger.com/profile/00104361785049371212 "noreply@blogger.com") - <time datetime="2007-08-30T08:55:00.000-07:00">Aug 4, 2007</time>

José, veja http://www.sacredchao.net/quodlibet  
  
O site deles ficou quebrado um tempo.  
  
Esse meu post é bastante antigo (fev de 2006), mas fiquei feliz de ver que de lá pra cá o Quod Libet continua sendo desenvolvido. Veja as últimas atividades em:  
  
http://www.sacredchao.net/quodlibet/timeline  
  
\[\]s  
Yves
<hr />
