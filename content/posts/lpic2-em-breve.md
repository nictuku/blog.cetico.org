---
title: 'LPIC2, em breve'
date: 2007-01-07T17:47:00.000-08:00
draft: false
url: /2007/01/lpic2-em-breve.html
tags: 
- Postfix
- Pessoal
---

A turma no trampo está empolgada pra fazer as provas da LPI. Dois colegas passaram na 101 semana passada, Wesley e Alexfuu, e amanhã o [Gabriel Peixoto](http://kernelpanic.eti.br) vai fazer também.  
A 201, [que fiz em outubro](http://www.cetico.org/tech/2006/10/sifudi-lpi-201-na-segunda-feira.html), não foi muito difícil, apesar de algumas perguntas bizarras terem aparecido.  
  
Estou querendo fazer logo a 202, e vejo que vou ter que realmente estudar pra essa prova.  
  
O que me impressiona nos [objetivos da 202](http://www.lpi.org/en/lpi/english/certification/the_lpic_program/exam_202_detailed_objectives) é a abrangência de todas as alternativas. Por exemplo, o objetivo 2.206.1, "**Configuring mailing lists**", engloba mailman, majordomo e Ezmlm.  
  
O objetivo 2.206.2, "**Using email services**", exige conhecimentos de postfix, qmail, sendmail e exim.  
  
Ora, isso é foda. E muito bom. A tendência de todos os sysadmins, eu inclusive, é que, ao aprender a utilizar uma alternativa, surge uma enorme resistência em aprender outra.  
  
Configurar um MTA não é um processo simples. Levei bastante tempo até enteder o funcionamento do Postfix e memorizar os parâmetros de configuração mais importantes. Hoje, configurar um servidor de e-mail usando Postfix é uma coisa bem automática. Nesses casos, quando a gente se topa com outro sistema, dos quais nada conhecemos a não ser a teoria de funcionamento - que é sempre a mesma -, dá sempre vontade de destruir o que está feito e refazer com o que sabemos. Ora, qmail só serve pra ser migrado.  
  
Isso se chama preguiça. Do ponto de vista da "utilidade galática", por um lado pode ser bom pois cria a tendência de uniformização das soluções. Por outro lado, no entanto, aprofunda a tendência universal de que nos tornemos burros e limitados. Ora, um sysadmin decente **tem** que saber Exim e qmail tanto quanto Sendmail e Postfix.  
  
Infelizmente é isso que, felizes, devemos fazer.  
A prova 202 da LPI exige conhecimentos de todos esses MTA's, e de vários softwares de listas de discussão, mesmo aqueles bem velhos. Muita gente reclama: "Eu já sei mailman, não preciso saber majordomo". A certificação não existe pra provar que você sabe muita coisa, e sim que você sabe aquilo que importa.  
E é por isso que eu valorizo tanto essas "certificações de TI". Dou valor à certificação e ao profissional certificado. Pra mim, um cara com LPIC merece respeito, inclusive no nível 1, porque tenho certeza que ele estudou e entende dos conteúdos que realmente importam para o trabalho de administração de sistemas Linux.  
.. mas quem não merece respeito?  
  
Depois tem o LPIC3. Quem fez ([Leandro Godoy da Rocha no under-linux.org](http://under-linux.org/6513-impressoes-sobre-a-prova-do-lpic3.html), e o [Fernando Ribeiro](http://www.nerdgroup.org/fernando/) no IRC) ficou impressionado.
