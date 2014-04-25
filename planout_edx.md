"It is a capital mistake to theorize before you have all the evidence:" AB-multi-arm bandit framework for a learning management system


<!-- 

https://edx-wiki.atlassian.net/wiki/pages/viewpage.action?pageId=39551632

a. allow for comparison of different educational content rather
than user experience. this means that we could for example randomize
across videos with different types of experiences, exercises, etc
  b. ability to connect the experiments to three main types of
outcomes: educational scores (measuring knowledge or ability to get an
answer right or in the right direction measured through classical
items), satisfaction (how much they liked a certain type of
explanation or item), and computer log-type of outcomes (e.g. if they
dropped out of a video and at which point they watched it before
dropping out)
  c. right now all of their data goes to an external analytics app
called http://import.io/ , while we want to move the data into a csv
format so that it can be analyzed by regular data science languages
like R http://www.r-project.org/ or python

 -->

Jacinto José Franco, MSc
Joao Ricardo Vissoci, PhD
Bruno Melo
Ricardo Pietrobon, MD, PhD
Seiji Isotani, PhD

# Abstract

# Introduction

Despite Sherlock Holmes' widely known advice that theorizing before having data will bias the judgment <!-- Doyle, A Study in Scarlet (1887), Part 1, chap. 3, p. 27 -->, the history of education can be largely summarized as a massive theorization followed by widespread education policy implementation, all of that occurring with no or minimal data. While observational data are now somewhat more prevalent in the educational literature, and randomized studies are slowly becoming more common, it is unfortunate that experiments are still largely divorced from the daily educational practice.

<!-- Hawthorne effect and the problem with experiments run in artificial educational environments  -->

<!-- AB, multi-arm bandit, review educational literature 
Planout and multiple trial integrated into a single platform

-->

The objective of this study is therefore to describe the creation of an extension to the edX Learning Management System that allows it to fully integrate randomized experiments in the form a AB (parallel) randomization as well as multi-arm bandit algorithms.

# Methods

## Requisites and informal use cases

* Requisites
	* randomize anything, not only UX features
	* sophisticated design and randomization frameworks
	* external scripting
	* ability to provide researchers with querying ability to database for <!-- nao essencial, mas vamos discutir -->
* Informal use cases


## edX Code

system description
course cloning
database architecture
[AGPL](http://www.gnu.org/licenses/agpl-3.0.html)

## Planout

system description
planout edX integration
[BSD License](https://github.com/facebook/planout/blob/master/LICENSE)

## Data analysis script

open source library of data analysis scripts in R
github

# Results

# Discussion

<!-- 
https://sites.google.com/a/khanacademy.org/forge/technical/data_n

http://goo.gl/R7Jno7

Renzo - https://github.com/edx/edx-platform/wiki/Split-Testing

blame: http://goo.gl/wczjcY

ele joga tudo pra https://segment.io/
My framework keeps track of which flags are active for a particular user by adding a property to Segment.io API calls which contains a string listing active flags; this particular change was made in segment-io.html. Segment.io routes this information to Mixpanel where we can study the data, allowing us to compare the behavior of different groups of users.


* livro sobre bandit - http://goo.gl/bAhV7
* vagrant datajam http://goo.gl/1m1WTD - isso vai instalar localmente tudo que voce precisa
* o que eu consegui achar sobre AB no edx:
    * http://goo.gl/Eg2Jic
    * http://goo.gl/qovqEZ
    * http://goo.gl/7P8CI2 - eu acabei de achar isso, ele usou o waffle http://goo.gl/OZpY3 inves de ir com as implementacoes de AB que ja existem pro django (eu eu o Bruno tinhamos dado uma olhada ha algum tempo).

emails renzo 


muito interessante. tava lendo http://goo.gl/XVOGSe . voces acham que
isso poderia ter impacto no projeto de AB/bandit? ou seja, se eles
separarem conteudo e estrutura sera que a gente poderia aplicar a
randomizacao pra dois ou mais cursos com estruturas diferentes
(representando os arms experimentais) ao inves de criar os arms dentro
de uma mesma estrutura?

se sim, isso seria interessante porque daria pra gente a possibilidade
de nao so realizar experimentos muito especificos (por exemplo
comparar dois videos em um curso explicando a mesma coisa), mas daria
pra gente a possibilidade de comparar metodos educacionais num nivel
mais "macro", como por exemplo comparar a mudanca de metodo
educacional em todos os videos de um determinado curso. como eles
disseram, vamos ter de ver o que isso vai querer dizer em termos de
storage
-->