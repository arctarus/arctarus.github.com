---
layout: post
title: Web Workers
tags:
- ajax
- hilos
- html5
- javascript
- threads
- worker
status: publish
type: post
published: true
comments: true
meta:
  _edit_last: '87616'
---
Una de las características de HTML 5 introducidas en el reciente <a href="http://en-us.www.mozilla.com/en-US/firefox/3.5/releasenotes/" title="Firefox 3.5 Release Notes">Firefox 3.5</a> y que también se encuentra disponible en Safari 4 y Chrome 2 son los <a href="https://developer.mozilla.org/En/Using_web_workers" title="Using web workers">web workers</a>. 

Los workers proveen un mecanismo para poder ejecutar tareas que requieran mucho tiempo de ejecución en hilos directamente en el sistema operativo sin que bloqueen la interfaz del usuario. Una de sus utilidades principales es la de ejecutar tareas de entrada/salida de datos a través del objeto <a href="http://www.w3.org/TR/XMLHttpRequest/" title="The XMLHttpRequest Object">XMLHttpRequest</a>. 

Los web workers se comunican con el proceso principal a través del envío de mensajes a un manejador de eventos especificado por el desarrollador. Estos mensajes pueden contener desde una cadena de caracteres a un objeto complejo. Una característica importante es que no pueden manipular el <abbr title="Document Object Model">DOM</abbr> por lo que si se desea mostrar los datos resultantes de su ejecución es necesarios que estos sean pasados al manejador a través del paso de mensajes.

<a href="http://www.flickr.com/photos/dinesh_valke/1081956162/" title="un laborioso trabajador de la red"><img src="http://farm2.static.flickr.com/1325/1081956162_e5f955ff5a.jpg?v=0" alt="Nephila maculata (Orb Web Spider) de dinesh_valke" /></a>

Para crear un worker lo único que es necesario es llamar al contructor pasándole como único argumento la URI del script que deberá ejecutar, y definir el manejador del evento onmessage que será el encargado de escribir el resultado en la página.

<code class="javascript"><pre>
var worker = new Worker('worker.js');  
worker.onmessage = function(event) {  
     print("¡llamada ejecutada al finalizar el worker!\n");
}
</pre></code>

y para detener su ejecución:

<code><pre>
worker.terminate();
</pre></code>

Posteriormente deberemos implementar lo que hará el worker durante su ejecución en el archivo <em>worker.js</em> de la siguiente manera:

<code><pre>
onmessage = function(event) {
     var n = calcular();
     postMessage(n);
}
</pre></code>

Al finalizar la ejecución del método <em>calcular</em> el worker enviará un mensaje con el resultado que será recogido por el manejador del evento <em>onmessage</em> definido anteriormente.

El método <em>calcular</em> podría estar definido en otro archivo e importando mediante la función global <em>importScripts('calcular.js')</em> la cuál descagará y traerá dicha función al ámbito del worker.

Además cada worker puede lanzar tantos otros workers como se desee, lo único a tener en cuenta es que la ruta a el fichero que se le pasa en el constructor se calcula dinámicamente dependiendo de la localización del padre. Esto es muy aconsejable sobre todo en el caso de que el usuario posea un microprocesador con más de un núcleo, ya que el sistema operativo podría repartir los hilos entre estos.

<h3>Referencias</h3>
<ul>
<li><a href="http://www.whatwg.org/specs/web-workers/current-work/">Web Workers</a></li>
<li><a href="https://developer.mozilla.org/En/Using_web_workers">Mozilla Developer Center: Using web workers</a></li>
<li><a href="http://inimino.org/~inimino/blog/3box_web_workers">Using Web Workers</a></li>
</ul>
