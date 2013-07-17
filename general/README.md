![Sancho BBDO](https://dl.dropboxusercontent.com/u/2402696/external/logo-sancho.png)

#Guía general

##Tabla de contenidos
1. [**Introducción**](#introducción)
1. [**Reglas de formato**](#reglas-de-formato)
1. [**Reglas de estilo**](#reglas-de-estilo)
  1. [identificadores](#identificadores)
  1. [Uso de comentarios](#uso-de-comentarios)
    1. [Uso de anotaciones](#uso-de-anotaciones)
1. [**Referencias**](#referencias)
1. [**Contribuidores**](#contribuidores)
1. [**Licencia**](#licencia)

##Introducción

Este documento define reglas generales de formato y estilo que debes aplicar a
código fuente. Su objetivo es mejorar la colaboración y la calidad del código.

Aplica estas reglas a menos qué una guía de tipo de archivo, *framework*
o proyecto defina reglas diferentes.

Algunas reglas definidas por el lenguaje de programación principal o *framework*
utilizado pueden sobreescribir las reglas generales con el fin de mantener
consistencia a través del proyecto - p. ej. si la guía de un *framework* PHP
sugiere utilizar tabulaciones, debes utilizar tabulaciones no sólo en código PHP
sino también en hojas de estilo, *markups* y *scripts*.

Configura tu IDE o editor de texto de acuerdo a las siguientes reglas.

**[[⬆]](#tabla-de-contenidos)**

##Reglas de formato

- Usa UTF-8 sin BOM
- Usa terminaciones de línea Unix - LF, **no** CR (MacOS) o LF+CR (Windows)
- Usa indentaciones a 4 espacios

  ```javascript
  // Camino a seguir:
  if (indent === 4) {
  ····var imHappy = true;
  }
  ```

  ```javascript
  // Evita esto:
  ··var twoSpaces;
  ↦   var orTabs;
  ```

- Elimina espacios en blanco al final de las lineas

  ```html
  <div class="error">Acá vienen los espacios rezagados</div>····
  ```

- Usa una línea vacía para separar bloques de código

  ```javascript
  // Esto está bien:
  var me = 'Hola';
  ····
  me = me + ' mundo!';
  me = me + ' Qué ha pasado?!';
  ····
  var world = 'Todo está bien';
  ```

  ```javascript
  // Esto no lo está:
  var me = 'Hola';
  ····
  ····
  ····
  var world = 'Hay demasiadas líneas y no te puedo escuchar.';
  ```

- Deja una línea vacía al final del archivo

  ```javascript
  // No lo hagas:
  endOfFile = true;
  ····
  ····
  ····
  ```

  ```javascript
  // No lo hagas:
  endOfFile = true; // Eso es todo, no hay más líneas
  ```

  ```javascript
  // Hazlo:
  endOfFile = true;
  ····
  ```

- Limita las lineas a 80 caracteres de longitud

**[[⬆]](#tabla-de-contenidos)**

##Reglas de estilo

###Identificadores

  - Nombra identificadores en **inglés**
  - Usa nombres significativos
  - Usa nombres tan cortos cómo sea posible y tan largos cómo sea necesario
  - Usa abreviaciones sólo si utilizas una convención conocida (p. ej. ```nav```
    cómo abreviación de ```navigation```)
  - Usa nombres consistentes a través del proyecto, incluso a través de archivos
    de diferentes tipos

    ```html
    <!-- Esto es feo (song, mp3 y audio para referirse a lo mismo) -->

    <script>
        var song = $('.mp3');
        ····
    </script>

    ····

    <a href="····" class="mp3">
        <?php echo $audio; ?>
    </a>

    ····
    ```

    ```html
    <!-- Esto es muchisimo mejor (track para todo) -->

    <script>
        var track = $('.track');
        ····
    </script>

    ····

    <a href="····" class="track">
        <?php echo $track; ?>
    </a>

    ····
    ```

**[[⬆]](#tabla-de-contenidos)**

###Uso de comentarios

- Escribe código qué se explique a sí mismo en vez de código que necesite
  documentación
- Manten actualizados los comentarios existentes
- Escribe comentarios en **inglés**
- Evita comentarios superfluo

> **TODO**: Cuando escribir comentarios

**[[⬆]](#tabla-de-contenidos)**

####Uso de anotaciones

- Marca acciones pendientes con ```TODO```
- Utiliza el formato ```TODO(contacto): acción pendiente``` donde ```contacto```
  es tu nombre de usuario o correo electrónico
- Escribe anotaciones arriba del código relevante
- Escribe anotaciones en **inglés**

```html
<!-- TODO(joe.doe): remove optional tags -->
<ul>
    <li>Manzanas</li>
    <li>Naranjas</li>
</ul>
```

**[[⬆]](#tabla-de-contenidos)**

##Referencias

- Políticas de comentarios basadas en:
  - [The Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide#comments)
  - [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)

**[[⬆]](#tabla-de-contenidos)**

##Contribuidores

  - [Ver contribuidores](../../../graphs/contributors)

**[[⬆]](#tabla-de-contenidos)**

##Licencia

[![Creative Commons Atribución 3.0 Unported](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/deed.es_CO)

[Creative Commons Atribución 3.0 Unported](http://creativecommons.org/licenses/by/3.0/deed.es_CO) Sancho BBDO
