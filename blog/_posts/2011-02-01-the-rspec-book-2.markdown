---
layout: post
title: The RSpec Book 2
tags:
- bdd
- cucumber
- libros
- rspec
- testing
status: publish
type: post
published: true
meta:
  _edit_last: '87616'
  jabber_published: '1296591800'
---
Con motivo de la reciente publicación de <a href="https://github.com/rspec">RSpec 2</a> y la correspondiente reedición de <a href="http://www.pragprog.com/titles/achbd/the-rspec-book">The RSpec Book</a> de <a href="http://davidchelimsky.net/">David Chelimsky</a>, estos días he estado repansando un poco de <a href="http://en.wikipedia.org/wiki/Behavior_Driven_Development">Behaviour Driven Development</a> o BDD.

<a title="The RSpec Book" href="http://www.pragprog.com/titles/achbd/the-rspec-book"><img class="alignright size-full wp-image-306" title="The RSpec Book" src="http://arctarus.files.wordpress.com/2011/02/the-rspec-book.jpg" alt="The RSpec Book: Behaviour-Driven Development with RSpec, Cucumber, and Friends" width="190" height="228" /></a>

El libro está dividido en 5 partes fundamentales.

En primer lugar un ejemplo práctico de uso de RSpec y <a href="http://cukes.info">Cucumber</a> en el que se desarrolla un pequeño juego llamado Codebreaker, donde el usuario debe adivinar un número secreto, y que nos familiariza con el ciclo básico del BDD: red, green, refactor.

La segunda parte está dedicada exclusivamente al BDD, y se centra en explicar por qué los proyectos tradicionales fallan y qué aporta dicha metodología para evitar esos errores.

La tercera parte nos introduce en RSpec y da un repaso completo a la librería: cómo definer expects, el uso de mocks y stubs para aislar cada test y por último cómo extenderla a través de macros o custom matchers entre otros.

La cuarta parte se centra en Cucumber y en cómo escribir requisitos usando <a href="https://github.com/aslakhellesoy/cucumber/wiki/Gherkin">Gherkin</a>, cómo definir escenarios y cómo implementar cada uno de los pasos. Sin embargo, he de confesar que este apartado me lo leí un poco más por encima ya que en <a href="http://qoolife.com">Qoolife</a> hemos reemplazado Cucumber por <a href="https://github.com/cavalle/steak">Steak</a> para hacer los test de aceptación. La razón fundamental es que ya que el producto lo estamos desarrollando en casa, y que todos los que vamos a escribir / leer las historias de usuarios conocemos ruby, eliminamos la capa de definición de los requisitos en lenguaje natural y pasamos directamente a implementarlas usando RSpec y <a href="https://github.com/jnicklas/capybara">Capybara</a>.

En la quinta y última parte se hace un repaso a la integración con rails, desde la definición de features, pasando por distintas opciones que existe para simular el navegador usando Webrat y Selenium y acabando en cada una de las capas del MVC: vista, controlador y finalmente los modelos.

En resumen, un libro muy recomendable para todos aquellos interesados en ponerse al día en lo que a Behaviour Driven Development se refiere, y para los que deseen utilizar RSpec y/o Cucumber como herramienta de testing en particular.
