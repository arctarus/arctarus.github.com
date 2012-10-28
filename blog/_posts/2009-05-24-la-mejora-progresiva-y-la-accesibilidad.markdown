---
layout: post
title: La mejora progresiva y la accesibilidad
tags:
- accesibilidad
- css
- javascript
- progressive enhancement
status: publish
type: post
published: true
comments: true
meta:
  _edit_last: '87616'
---
La mejora progresiva (o <a href="http://en.wikipedia.org/wiki/Progressive_enhancement">progressive enhancement</a>) es una estrategia de desarrollo web en la que se destaca la accesibilidad, el marcado semántico, y el uso de hojas de estilo y scripts enlazados externamente.

Nace en contraposición a la estrategia clásica conocida como degradación agraciada (o <a href="http://en.wikipedia.org/wiki/Graceful_degradation">graceful degradation</a>) en la que los desarrolladores web crean sus páginas para los navegadores más recientes y posteriormente prueban y adaptan a los navegadores menos avanzados tecnológicamente.

La mejora progresiva se basa en los siguientes principios:
<ul style="margin-bottom:1em;">
	<li>El contenido básico debe ser accesible a todos los navegadores.</li>
	<li>La funcionalidad básica debe ser accesible a todos los navegadores.</li>
	<li>Mínimo marcado (X)HTML semántico para todo el contenido.</li>
	<li>Las mejoras de diseño son proporcionadas por hojas de estilo externas.</li>
	<li>Las mejoras de comportamiento son proporcionadas por JavaScript no intrusivo enlazado externalmente.</li>
	<li>Las preferencias de los navegadores de los usuarios son respetadas.</li>
</ul>

Para ello propone centrarse en el contenido y comenzar creando el marcado (X)HTML semántico al cuál se le irán añadiendo capas que lo enriquezcan.

<a href="http://www.flickr.com/photos/sugarbloom_cupcakes/3002400314/" title="Blonde and Brown Cupcakes"><img src="http://farm4.static.flickr.com/3228/3002400314_f4c5d4ffbe.jpg" alt="Blonde and Brown Cupcakes" /></a>

De esta manera conseguimos que aquellos usuarios que usen navegadores antiguos, dispositivos móviles o sintetizadores de voz obtendrán un mejor soporte. De hecho, como vimos, gracias a las <a href="http://arctarus.wordpress.com/2009/04/26/ventajas-de-escribir-html-semantico/" title="">ventajas del (X)HTML semántico</a> se mejorará la indexación de la página por parte de los buscadores lo que es básico en una estratégia <acronym title="Search Engine Optimization">SEO</acronym>.

La primera capa que se añade a nuestro marcado (X)HTML semántico es la de <acronym title="Cascading Style Sheets">CSS</acronym> la cual nos permitirá mejorar el aspecto de nuestra página y en la que deberemos poner cuidado en la forma en la que enlazamos cada una de las hojas de estilo y los tipos de medios para los cuales deben estar disponibles de forma que se aprovechen las características de los navegadores nuevos siempre teniendo en cuenta de que el contenido debe ser accesible para el resto de los navegadores.

Finalmente añadimos la capa de JavaScript, previamente ha debido ser programada la funcionalidad básica de la web en el lado del servidor de forma que se pueda ejecutar independientemente del soporte de JavaScript que tenga el usuario, para posteriormente ir añadiendo mejoras en la usabilidad por medio de la programación en en lado del cliente. Para ello es imprescindible la utilización de técnicas de JavaScript no intrusivo como enlazar los scripts desde archivos externos o la eliminación de los manejadores de eventos en linea.

Cómo se puede ver todo el flujo de trabajo está orientado a que el contenido de la página, la razón por la cual los usuarios te visitan, esté siempre accesible en cualquier circunstancia independientemente de los medios de los que dispongan, ya que en el peor de los casos tendrán acceso a la capa de (X)HTML de nuestra web, y por tanto, tendrán acceso a su contenido.

<h3 style="margin-top:2em;">Referencias</h3>
<ul>
	<li><a href="http://en.wikipedia.org/wiki/Progressive_enhancement">Progressive enhancement</a></li>
	<li><a href="http://www.alistapart.com/articles/understandingprogressiveenhancement">Understanding Progressive Enhancement</a></li>
	<li><a href="http://www.alistapart.com/articles/progressiveenhancementwithcss">Progressive Enhancement with CSS</a></li>
	<li><a href="http://www.alistapart.com/articles/progressiveenhancementwithjavascript/">Progressive Enhancement with JavaScript</a></li>
	<li><a href="http://css-discuss.incutio.com/?page=ProgressiveEnhancement">Progressive enhancement using CSS</a></li>
	<li><a href="http://icant.co.uk/articles/pragmatic-progressive-enhancement/">Pragmatic progressive enhancement</a></li>

</ul>


