---
layout: post
title: Extendiendo FormBuilder para añadir nuevos helpers personalizados
tags:
- custom
- error messages
- form
- FormBuilder
- helpers
- rails
status: publish
type: post
published: true
comments: true
meta:
  _edit_last: '87616'
  jabber_published: '1298983758'
---
A la hora de hacer nuevos formularios en rails siempre había echado de menos algún helper que te ayudara a incluir los típicos mensajes de error junto al campo al que se refieren para contextualizar cada uno de los mensajes, en lugar de que aparezcan todos listados en la cabecera del formulario.

La idea fundamental de lo que pretendía conseguir es la siguiente:
<a href="http://arctarus.files.wordpress.com/2011/03/form_error1.png"><img class="aligncenter size-full wp-image-429" title="ejemplo de errores en campos de formulario" src="http://arctarus.files.wordpress.com/2011/03/form_error1.png" alt="ejemplo de errores en campos de formulario" width="560" height="251" /></a>

Todo esto usando para ello un helper de FormBuilder para que el objeto concreto quede implícito y que el código resultante (en haml) nos quede como el siguiente:
<pre style="overflow:auto;">= form_for @user do |form|
   .field
      = form.label :name
      = form.error :p, :name
      = form.text:field :name</pre>
El primer parámetro indica el tag html que queremos usar como contenedor del error, y el segundo en atributo del modelo que debemos comprobar. Además, al tag contenedor le añadiremos la clase "error" de css para luego poder darle algunos estilos.

Tras dar algunas vueltas googleando me dí cuenta de que crear un nuevo helper no era tarea demasiado complicada, así que le eché un ojo a <a href="https://github.com/rails/rails/blob/master/actionpack/lib/action_view/helpers/form_helper.rb">FormHelper</a> y observé que está dividido en tres partes principales:
<ol>
	<li>El modulo FormHelper, que encapsula a todos los helpers de formularios.</li>
	<li>La clase FormBuilder, que es el resultado de usar el helper form_for y que contiene una instancia del objeto al que se refiere el formulario. Tiene métodos internos con el mismo nombre que los helpers que hacen uso de estos.</li>
	<li>La clase InstanceTag, que  es la encargada de generar el código para cada uno de los tags html. Es llamada desde los helpers.</li>
</ol>
Finalmente, adaptando un poco el código de otros helpers en el mismo fichero, el resultado fue:
<pre style="overflow:auto;">module ActionView
  module Helpers
    module FormHelper
      def error(object_name, tag_name, method, options = {})
        InstanceTag.new(object_name, method, self, options.delete(:object)).to_error_tag(tag_name)
      end
    end

    class InstanceTag
      def to_error_tag(tag_name)
      	unless @object.errors[@method_name].blank?
      	  content_tag tag_name, @object.errors[@method_name].first, :class =&gt; :error
      	end
      end
    end

    class FormBuilder
      def error(tag_name, method, options = {})
        @template.error(@object_name, tag_name, method, objectify_options(options))
      end
    end
  end
end</pre>
Que también se puede ver en <a title="extendiendo FormBuilder para añadir helpers personalizados" href="https://gist.github.com/849052">su gist correspondiente</a>.

&nbsp;

<strong>Actualización 22 de Marzo de 2011:</strong>

Otra forma de <a href="http://guides.rubyonrails.org/active_record_validations_callbacks.html#customizing-the-error-messages-html">personalizar los mensajes de error de los formularios en rails</a>, que acabo de ver en la guía de rails y que ya no recordaba, es usando ActionView::Base.field_error_proc. Simplemente se necesita asignarle un nuevo Proc que reciba el tag html y una instancia del modelo y listo. Podemos devolver lo que deseemos.
