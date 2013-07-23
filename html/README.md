![Sancho BBDO](https://dl.dropboxusercontent.com/u/2402696/external/logo-sancho.png)

#Guía HTML

##Tabla de contenidos

1. [Introducción](#introducción)
1. [Reglas de foramto](#reglas-de-formato)
  1. [Disposición de elementos](#disposición-de-elementos)
  1. [Uso de comillas](#uso-de-comillas)
1. [Reglas de estilo](#reglas-de-estilo)
  1. [Uso de imágenes](#uso-de-imágenes)
1. [Validación](#validación)
1. [Recursos](#recursos)
1. [Referencias](#referencias)
1. [Colaboradores](#colaboradores)
1. [Licencia](#licencia)

##Introducción

Este documento define reglas de formato y estilo para HTML. Su objetivo es
mejorar la colaboración y la calidad del código.

> **Notas:**
>
> - Este documento aplica y extiende las reglas definidas en la
>   [Guía general](../general/README.md).
> - Este documento complementa la [Guía CSS](../css/README.md).

##Reglas de formato

###Disposición de elementos

- Usa una nueva línea sin indentar para elementos estructurales (`html`,
  `head`, `body`).
- Indenta y usa una nueva línea para elementos dentro de `head`.
- Indenta y usa una nueva línea para elementos de tipo bloque, lista, tabla o
  formulario.
- Escribe otro tipo de elementos (incluyendo texto) de forma consecutiva o en
  una nueva línea indentada si hay una buena razón para hacerlo.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Site Title</title>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <ul>
        <li>Moe</li>
        <li>Larry</li>
        <li>Curly</li>
    </ul>
    <table>
        <thead>
          <tr>
            <th scope="col">Income</th>
            <th scope="col">Taxes</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>$ 5.00</td>
            <td>$ 4.50</td>
          </tr>
        </tbody>
    </table>
    <blockquote>
        <p><em>Space</em>, the final frontier.</p>
    </blockquote>
</body>
</html>
```

> Categorización de elementos:
>
> - [Estructurales][html_structure]
> - [Dentro `head`][html_head]
> - [Bloque][html_block]
> - [Formulario][html_form]
> - [Tabla][html_table]
> - [*Inline*][html_inline]

[html_structure]: http://en.wikipedia.org/wiki/HTML_element#Document_structure_elements
[html_head]: http://en.wikipedia.org/wiki/HTML_element#Document_head_elements
[html_block]: http://en.wikipedia.org/wiki/HTML_element#Block_elements
[html_form]: http://en.wikipedia.org/wiki/HTML_element#Forms
[html_table]: http://en.wikipedia.org/wiki/HTML_element#Tables
[html_inline]: http://en.wikipedia.org/wiki/HTML_element#Inline_elements

###Uso de comillas

- Usa comillas dobles para al definir valores de atributos.

  ```html
  <!-- No recomendado: -->
  <a class='button'>Sign in</a>
  <img width=200 height=200 src=image.jpg>

  <!-- Recomendado: -->
  <a class="button">Sign in</a>
  <img width="200" height="200" src="image.jpg">
  ```

##Reglas de estilo

- Usa HTML5 cómo tipo de documento.

  ```html
  <!DOCTYPE html>
  ```

- Escribe los nombres de elementos, atributos y valores en minúsculas.
- Utiliza `spinal-case` para nombrar identificadores.

  ```html
  <!-- No recomendado: -->
  <a href="#" class="buttonAlert">Cancel</a>
  <a href="#" class="button_alert">Cancel</a>
  <a href="#" class="buttonalert">Cancel</a>

  <!-- Recomendado -->
  <a href="#" class="button-alert">Cancel</a>
  ```

- Omite el protocolo al llamar recursos externos.

  ```html
  <!-- No recomendado: -->
  <script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

  <!-- Recomendado: -->
  <script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
  ```

- No uses [referencias a entidades][html_entity_references] a menos qué tengan
  un significado especial en HTML **p. ej.** `<` o `&`.
- No uses el atributo `type` al llamar hojas de estilo y *scripts*.

  ```html
  <!-- No recomendado: -->
  <link rel="stylesheet" href="style.css" type="text/css">
  <script src="script.js" type="text/javascript"></script>

  <!-- Recomendado: -->
  <link rel="stylesheet" href="style.css">
  <script src="script.js"></script>
  ```

- Usa los elementos HTML de acuerdo a su propósito y significado semántico.
- Usa el atributo `id` sólo si mejora sustancialmente el rendiemiento de
  Javascript. Para aplicar estilos e identificar elementos utiliza el atributo
  `class`.
- Proporciona contenidos alternos para imágenes, vídeos, audio y elementos
  `canvas`. Para las imágenes utiliza el atributo `alt`, para vídeos y audio
  utiliza subtítulos o transcripciones.
- Separa la presentación y el comportamiento de la estructura del sitio. No uses
  atributos *inline* para incluir estilos o comportamientos.

  ```html
  <!-- No recomendado: -->
  <h1 style="font-size: 24px">Grande</h1>
  <a href="javascript:showImage()">Imagen</a>
  ```

[html_entity_references]: http://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references

###Uso de imágenes

- Usa el elemento `img` si la imagen es parte del contenido o si es crucial para
  el mismo. Usa imágenes de fondo (a través de tu hoja de estilo) para incluir
  imágenes decorativas o que reemplacen textos **p. ej.** encabezados y botones.
- Describe la imagen en el atributo `alt`.
- Opcionalmente, usa el atributo `title` para indicar cúal es el significado
  de la imagen dentro del contexto del sitio.
- Usa el atributo `longdesc` para describir imágenes complejas cómo gráficas.
- Usa los atributos `width` y `height` para evitar saltos en la renderización
  del sitio.

##Validación

Usa herramientas cómo [W3C HTML validator][nu] para validar tu HTML.

[nu]: http://validator.w3.org/nu/

##Recursos

  - [Introduction to The Web Standards on Opera Developers][opera]
  - [The Road To Reusable HTML Components][resuable-html-components]

[opera]: http://dev.opera.com/articles/view/1-introduction-to-the-web-standards-cur/
[resuable-html-components]: http://coding.smashingmagazine.com/2012/10/23/road-reusable-html-components/

##Referencias

- Basado en [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)

##Colaboradores

  - [Ver colaboradores](../../../graphs/contributors)

##Licencia

[Creative Commons Atribución 3.0 Unported][cc] · Sancho BBDO · 2013

[cc]: http://creativecommons.org/licenses/by/3.0/deed.es_CO
