![Nucleo logo](http://elnucleo.co/logoSmall.png)

#Guía de estilo HTML/CSS 

##Contenido
1. Reglas Generales de Estilo 	
2. Reglas generales de formato
3. Reglamento General Meta
4. Normas de estilo HTML
5. Reglas de formato HTML
6. Reglas de estilo CSS
7. Reglas de formato CSS
8. Reglas de CSS Meta
9. Referencias


##Introducción
Este documento define las reglas de formato y estilo para HTML y CSS. Su objetivo es mejorar la colaboración y la calidad del código en los archivos de trabajo que utilizan HTML y CSS.

##Reglas Generales de Estilo
###Protocolo
Omitir el protocolo para recursos incrustados.

Omitir la parte de protocolo (http:, https :) de las URLs que apuntan a imágenes y otros archivos multimedia, hojas de estilo y secuencias de comandos a menos que los archivos respectivos no están disponibles en ambos protocolos.

La omisión en el protocolo hace que la dirección URL sea relativa, previeniendo problemas de contenido mixto y ahorra un poco en el tamaño del archivo.

En HTML

	<!-- No recomendado -->
	<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
	
	<!-- Recomendado -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

En CSS	
				
	/* No recomendado */
	.ejemplo {
	  background: url(http://www.google.com/images/example);
	}
	/* Recomendado */
	.ejemplo {
	  background: url(//www.google.com/images/example);
	}

##Reglas generales de formato
###Indentación (sangría)
Indentar con un tab (4 espacios).

No mezclar tabs y espacios para la indentacion.

En HTML

```
 <ul>
     <li>Fantastic
     <li>Great
 </ul>
```

En CSS

```
.example {
    color: blue;
}
```
###Capitalización
Utilizar sólo letras minúsculas.

Todo el código tiene que estar en minúsculas: Esto se aplica a los nombres de elementos, atributos, valores de atributos (a menos que sea texto/CDATA), los selectores, propiedades y valores de las propiedades (con la excepción de las cadenas).

```
 <!-- No recomendado -->
 <A HREF="/">Home</A>
 
 <!-- Recomendado -->
 <img src="google.png" alt="Google">
```
###Espacios en blanco
Quitar los espacios blancos finales.

Los espacios en blanco son innecesarioss y pueden complicar el uso de herramientas diffs.

```
 <!-- No recomendado -->
 <p>Que?_
 
 <!-- Recomendado -->
 <p>Si por favor.
```
##Reglamento General Meta
###Codificación
Usar UTF-8 (sin BOM).

Asegúrese de que el editor utiliza UTF-8 como codificación de caracteres, sin una marca de orden de bytes.

Especifique la codificación de plantillas HTML y documentos a través de ```<meta charset="utf-8">```. No especifique la codificación de las hojas de estilo ya que estos se asumen como UTF-8.

###Comentarios
Explique el código según sea necesario, siempre que sea posible.

Use los comentarios para explicar el código: ¿Qué es lo que cubre?, ¿Cual es su propósito?, ¿Por qué la solución respectiva o utilizada es la que prefiere?

> Este elemento es opcional, ya que no se considera una expectativa realista exigir siempre el código totalmente documentado. Los resultados pueden variar en gran medida para el código HTML y CSS, y depende de la complejidad del proyecto.

##Normas de estilo HTML
###Tipo de documento
Usar HTML5.

HTML5 (la sintaxis HTML) es la preferida para todos los documentos HTML: ```<DOCTYPE html!>```.

> Se recomienda el uso de HTML, como ```text/html``. No utilice XHTML. XHTML, como ```application/xhtml+xml```, carece de soporte de infraestructura y de navegadores y ofrece menos espacio para la optimización que HTML.

###Validez del HTML
Utilice el código HTML válido, a menos que no sea posible debido a objetivos de rendimiento inalcanzables de otro modo con respecto a tamaño del archivo.

Utilizar herramientas como el validador HTML del W3C para pruebas.

El uso de HTML válido es un atributo de calidad medible que contribuye al aprendizaje acerca de los requisitos y limitaciones técnicas, y que garantiza el uso de HTML adecuado.

```
 <!-- No recomendado -->
 <title>Prueba</title>
 <article>Esta es una prueba.
 
 <!-- Recomendado -->
 <!DOCTYPE html>
 <meta charset="utf-8">
 <title>Prueba</title>
 <article>Esta es una prueba.</article>
```

###Semántica
Utilice HTML de acuerdo con su propósito.

Utilice los elementos (a veces incorrectamente llamados "etiquetas") para lo que han sido creados. Por ejemplo, utilice los elementos de encabezado para los encabezados, elementos ```p``` para los párrafos, los elementos ```a``` para los enlaces, etc.

El uso de HTML de acuerdo a su propósito es importante para la accesibilidad, la reutilización, y la eficiencia del código.

```
 <!-- No recomendado -->
 <div onclick="goToRecommendations();">Todas las recomendaciones</div>
 
 <!-- Recomendado -->
 <a href="recommendations/">Todas las recomendaciones</a>
```

###Multimedia
Proporcione contenidos alternativos para elementos multimedia.

Para multimedia, como imágenes, vídeos, objetos animados a través de ```canvas```, asegúrese de ofrecer un acceso alternativo. Para imágenes esto significa el uso de texto alternativo (ALT) y para audio y vídeo, los subtítulos, si están disponibles.

Proporcionar contenidos alternativos es importante por razones de accesibilidad: Un usuario ciego tiene pocas claves para contar lo que se trata de una imagen sin ```@alt```, y otros usuarios no tienen forma de entender lo que los contenidos de vídeo o audio tratan tampoco.

> Para las imágenes cuyos atributos alt podría introducir una redundancia, y para las imágenes, cuya finalidad es puramente decorativa y no se puede usar mediante CSS, no use texto alternativo, deje el atributo vacio: ```alt = ""```

```
 <!-- No recomendado -->
 <img src="spreadsheet.png">
 
 <!-- Recomendado -->
 <img src="spreadsheet.png" alt="Spreadsheet captura de pantalla.">
```

###La separación de los elementos
Separar la estructura de la presentación de los comportamientos.

Estrictamente mantenga la estructura (markup), presentación (estilo), y el comportamiento (scripts) separados, y tratae de mantener la interacción entre los tres en un mínimo absoluto.

Es decir, asegurese que los documentos y las plantillas contengan sólo HTML y HTML que sirve exclusivamente para fines estructurales. Mover todo lo de presentación a las hojas de estilo, y todo comportamiento a los scripts.

Además, mantener el área de contacto lo más pequeña posible mediante la vinculación de pocas hojas de estilo y scripts como sea posible en los documentos y plantillas.

La separación de la estructura de la presentación del comportamiento es importante por razones de mantenimiento. Siempre es más costoso cambiar los documentos HTML y plantillas de lo que es actualizar las hojas de estilo y scripts.

```
 <!-- No recomendado -->
 <!DOCTYPE html>
 <title>HTML sucks</title>
 <link rel="stylesheet" href="base.css" media="screen">
 <link rel="stylesheet" href="grid.css" media="screen">
 <link rel="stylesheet" href="print.css" media="print">
 <h1 style="font-size: 1em;">HTML sucks</h1>
 <p>I’ve read about this on a few sites but now I’m sure:
   <u>HTML is stupid!!1</u>
 <center>I can’t believe there’s no way to control the styling of
   my website without doing everything all over again!</center>
 
 <!-- Recomendado -->
 <!DOCTYPE html>
 <title>My first CSS-only redesign</title>
 <link rel="stylesheet" href="default.css">
 <h1>My first CSS-only redesign</h1>
 <p>I’ve read about this on a few sites but today I’m actually
  doing it: separating concerns and avoiding anything in the HTML of
  my website that is presentational.</p>
 <p>It’s awesome!</p>
```

###Las referencias a entidades
Do not use entity references.

There is no need to use entity references like &mdash;, &rdquo;, or &#x263a;, assuming the same encoding (UTF-8) is used for files and editors as well as among teams.

The only exceptions apply to characters with special meaning in HTML (like < and &) as well as control or “invisible” characters (like no-break spaces).

```
 <!-- Not recommended -->
 The currency symbol for the Euro is &ldquo;&eur;&rdquo;.
 
 <!-- Recommended -->
 The currency symbol for the Euro is “€”.
```

###Los atributos de texto
Omit type attributes for style sheets and scripts.

Do not use type attributes for style sheets (unless not using CSS) and scripts (unless not using JavaScript).

Specifying type attributes in these contexts is not necessary as HTML5 implies text/css and text/javascript as defaults. This can be safely done even for older browsers.

```
 <!-- Not recommended -->
 <link rel="stylesheet" href="//www.google.com/css/maia.css"
  type="text/css">

 <!-- Recommended -->
 <link rel="stylesheet" href="//www.google.com/css/maia.css">

 <!-- Not recommended -->
 <script src="//www.google.com/js/gweb/analytics/autotrack.js"
  type="text/javascript"></script>
 
 <!-- Recommended -->
 <script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```
##Reglas de formato HTML
###El formato general
###HTML entre comillas
##Reglas de estilo CSS
###CSS validez
###Identificación y la clase de nombres
###Identificación y el estilo de nombre de la clase
###selectores de tipos
###las propiedades resumidas
###0 y unidades
###Los principales 0s
###La notación hexadecimal
###Los prefijos de identificación y delimitadores de la clase de nombre
###hacks
##Reglas de formato CSS
###Declaración de fin de
###Bloquear el contenido de la sangría
###Declaración se detiene
###Nombre de la propiedad deja de
###Selector y la declaración de separación
###Regla de separación
###CSS entre comillas
##Reglas de CSS Meta
###comentarios de la sección
##Referencias
- Basado en la [Guia de estilos de Google](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)