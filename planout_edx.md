"It is a capital mistake to theorize before you have all the evidence:" Experimental trial design and randomization framework integrated into a learning management system


<!-- 
variable categories
1. arm
2. baseline
3. outcomes from exercises
4. outcomes from computer logs

 -->

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
Jacson Barros
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

## edX and Planout descriptions

<!-- get from 3d grant -->

## Requisites and informal use cases

* Requisites
	* randomize anything, not only UX features
	* sophisticated design and randomization frameworks
	* external scripting
	* ability to provide researchers with querying ability to database for <!-- nao essencial, mas vamos discutir -->
* Informal use cases

<!-- abaixo veio do grant, depois eu vou adaptar -->

Since the [Open edX platform](http://code.edx.org/) currently does not have an embedded mechanism for randomization other than an initial mechanism to test interface features, in our project we intend to integrate an existing, open source platform that will allow for a substantially extended functionality. This platform is known as [Planout](http://facebook.github.io/planout/docs/getting-started.html) and was initially designed, validated and then released under an open source license by [Facebook](https://www.facebook.com/). 

[Planout](http://facebook.github.io/planout/docs/getting-started.html) will allow us to extend the current randomization functionality in [Open edX platform](http://code.edx.org/) well beyond the testing of simple interface features, also covering content randomization to test different educational approaches, as well as introducing both simple and complex randomization designs and algorithms. Of importance, [Planout](http://facebook.github.io/planout/docs/getting-started.html) also contains an automatic logging feature, thus allowing instructors to know exactly which participants had access to which features of the experiment, ultimately preventing errors during the analysis phase. Ultimately, the envisioned functionality will allow instructors to conduct multiple, concurrent randomized experiments within a single course if the instructor might so desire. 

The main advantage behind [Planout](http://facebook.github.io/planout/docs/getting-started.html)'s architecture is its ability to control the design of a variety of randomized designs in detail, using a simple syntax. This syntax is then connected to the underlying [Open edX platform](http://code.edx.org/) platform, and in our project we will create this interface between Planout and Open edX so that it might be available to any user of the [Open edX platform](http://code.edx.org/). 

In our architecture, Planout will be implemented using an edX [xblock](https://github.com/edx/XBlock), which is the edX preferred mechanism to extend its own functionality. The workflow for this implementation will be as follows:

1. The initial randomization arm for the trial, often times the control group when it might exist, will have its content fully created and tested by the instructor. This might include any slides, videos, exercises, as well as any features that might be part of the actual course. Included in this design will be any exercises that might serve as the outcome variable for the trial. For example, these could include exercises measuring knowledge secondary to the course content, questions evaluating satisfaction with the course as a student, ability to put the course information into practice, among others. Notice here that from an operational perspective the length of the course is not relevant, and the instructor has complete freedom to include whatever she might want.
<!-- Just to make sure I understand, this initial randmization arm will receive regular slide/video/exercise based course? To be compared with other types of courses? If so, it is no very clear for me. It is no clear of what the first arm will be composed by, or what kind of regular based teaching we are cloning (Joao) -->
<!-- not sure this is relevant here since we are talking about the platform and not a specific trial. but also not sure i understood the comment haha -->
2. Once the initial arm is completed and tested, this arm is cloned. This clone will then be modified to include whatever course features the instructor might want to test. For example, videos and slides could be modified to include a different instructional strategy, the interface could be changed to test a different type of environment, a new wiki could be included to test a more interactive environment eliciting discussions, among others. From a trial design perspective, instructors are not advised to change any exercises representing the outcomes variables of the study since that would violate the assumption that all subjects will have the same evaluation criteria, but the system will not prevent them from doing so in case of a semi-experimental or some other non-experimental exploratory design.
3. Once one or more intervention arms are derived from the original one, then a [Planout](http://facebook.github.io/planout/docs/getting-started.html) script will be written directly in [JSON (JavaScript Object Notation)](http://www.json.org/) format. Given that the platform is highly technical, at this point we do not envision most instructors programming direcly in JSON, but instead discussing the design with a methodologist and a programmer for implementation and testing. Future releases of this software could include a graphical interface, thus creating an [Agile Development environment](http://agilemanifesto.org/) that allows for the progressive inclusion of application features rather than fully loading them upfront without frequent interaction with instructors. <!-- Add a reference to Agile Development (Joao) -->
4. The interface between Planout and Open edX will be created using [xblock](https://github.com/edx/XBlock), an API (Application Programming Environment). The integration between Planout and Open edX will occur by allowing Planout to direct the following online trial features:
    * Defining which pages will render the course
    * Pbtaining user ids and mapping them between Open edX and Planout
    * Connecting an Anchoring Experiment object, which is the internal identification for experiments in Planout for a given user id. The Anchoring Experiment will contain all the design specifications using the Planout Language, including details about factors such as design type, randomization proportion, randomization arms, among any other factors pre-defined by the Planout language. For a full, detailed description of Planout please visit its [official page](http://facebook.github.io/planout/index.html) or its [main article](https://www.facebook.com/download/255785951270811/planout.pdf).
    * Connecting the results of the exercises defined as outcome variables by the instructor to the Planout Anchoring Experiment where the fields representing the outcome variables are defined
    * Testing the logging outcomes to ensure that all participant actions and respective outcomes are being appropriately logged



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