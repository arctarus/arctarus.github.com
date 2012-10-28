---
layout: post
title: XFN™ (XHTML Friends Network)
tags:
- (X)HTML
- microformatos
- XFN
status: publish
type: post
published: true
comments: true
meta: {}
---
Cada vez más usamos internet para relacionarnos con nuestros amigos, por lo que hace falta tener una manera sencilla de representar estas relaciones en la web.

<a href="http://www.gmpg.org/xfn/" target="_blank">XFN</a> es un <a href="http://microformats.org/" target="_blank">microformato</a> que representa estas relaciones utilizando para ello el atributo <i>rel</i> de los enlaces, al que se le asignan unos valores que las representen.

Un ejemplo de ello sería los valores para las relaciones de amistad.
<ul>
	<li>contact: Alguien con la quién sabes como llegar a él. Suele ser una relación simétrica.</li>
	<li>acquaintanc: Alguien con quién has intercambiado saludos y has mantenido una o dos conversaciones cortas. También simétrico.</li>
	<li>friend: Alguien de quien eres amigo. Un compatriota, un colega, que tu conoces. A menudo simétrico.</li>
</ul>
Por lo que para construir un enlace a la ficha de un amigo podríamos hacer:<code>
&lt;a href="http://11870.com/manueltxo" rel="friend met co-worker"&gt;manu&lt;/a&gt;
</code>

donde <i>met</i> nos indica que se conoce a esa persona fisicamente, y <i>co-worker</i> que es compañero de trabajo.

De esta manera podemos usar los estilos para diferenciar visualmente cada tipo de relación.
<code> a[rel~="friend"] {font-weight: bold;}
a[rel~="co-worker"] {text-decoration: underline;}
a[rel~="acquaintance"] {font-style: italic;}</code>

Se pueden ver como funciona XFN 1.1 utilizando la herramienta visual <a href="http://www.gmpg.org/xfn/creator-es" title="Creador de XFN 1.1" target="_blank">creador de XFN 1.1</a> para practicar.

Pero más allá de unos simples estilos, nos permitiría tener un sitio centralizado en donde definir nuestras relaciones (como <a href="http://www.orkut.com" title="Orkut">orkut</a> o <a href="http://www.linkedin.com/" title="Linkedin" target="_blank">Linkedin)</a> a partir de la cual otras puedan obtener esos datos y nos eviten tener que reintroducirlos cada vez que nos demos de alta en un nuevo servicio.
