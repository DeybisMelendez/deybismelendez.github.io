---
layout: post
title: Tutorial Jekyll para principiantes
thumbnail: 
---
{%raw%}
## Pre-requisitos:

Para este post es necesario que tengas conocimientos básicos de html y css como mínimo.

## Páginas html y markdown

Una vez que hemos creado un proyecto vacío con Jekyll debemos crear el sitio desde cero.

Primero debemos saber que cualquier página html que creemos se podrá acceder directamente desde la url, por lo que si creamos el index.html es lo que se mostrará al entrar al sitio.

Podemos entonces crear el contacto.html, el 404.html (para los errores de páginas no encontradas), etc.

Tambien podemos optar por trabajar con archivos markdown, pero si deseamos una personalización completa debemos dejar los markdown para contenido y no para páginas completas.

## Front Matter

Front Matter es un formato basado en archivos yml, esto sirve para añadir variables a las páginas, el Front Matter se añade al inicio de cada archivo html o markdown, por ejemplo:
```
---
title: Hola Mundo
---
```
Siempre se deben colocar las variables entre las lineas `---`.

## Liquid

Liquid es un lenguaje de plantilla, es utilizado para trabajar con variables como el front matter por ejemplo, las variables se acceden con las dobles llaves con la estructura:

```
{{variable}}
```

Si añadimos la varible title con el front matter al index.html ahora podremos acceder a ese dato con jekyll con la estructura:

```
{{ page.title }}
```

Liquid también tiene flujos de estados:

```html
{% if page.title == "Hola Mundo" %}
    <h1>Hola Mundo</h1>
{% else %}
    <h1>No es Hola Mundo</h1>
{% endif %}
```

Esto generará los html según la condición dada.

Liquid requiere un tutorial aparte, de modo que en este post nos limitamos solo a los aspectos básicos.

## Layouts

Los layouts son plantillas que podemos utilizar para crear páginas, esto es muy útil para evitar código repetido, para utilizar los layouts es necesario crear la carpeta "_layouts" y ubicar ahí las plantillas para acceder a ellas.

Usualmente se crea un default.html donde se guarda la estructura básica del html, por ejemplo:

```html
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>{{ page.title }}</title>
    </head>
    <body>
        {{ content }}
    </body>
</html>
```

Fíjate como en la etiqueta body he añadido `{{ content }}`, Jekyll sustituirá esa línea y añadirá el contenido que utilice ese layout.

Ahora fíjate como lo utilizamos en el index.html:

```yml
---
layout: default
title: Deybis Melendez
---
Bienvenido a mi sitio web!
```

Si ejecutamos el comando `bundle exec jekyll serve` y revisas en el enlace que te proporciona podrás ver algo parecido a esto:

![Captura de pantalla](https://i.postimg.cc/C1sddnZy/Captura-de-pantalla-2020-12-15-17-04-58.png){:.responsive-img}

Ahora puedes utilizar el layout default para crear el resto de tus páginas.

Lo genial de los layouts es que se pueden incrustar, por ejemplo, podemos crear un layout para los posts que sea contenido en el default:

```html
---
layout: default
---

<h1>{{page.title}}</h1>
{{content}}
```
Esto lo guardamos en `_layouts/post.html` junto con el `default.html`.

## Posts

Jekyll está hecho principalmente para el blogging, por lo que por defecto podemos trabajar los posts, solo debemos crear la carpeta `_posts` y en ella guardar los posts que vayamos creando, se puede utilizar html o markdown (recomendado). El título de los archivos debe tener la estructura `año-mes-dia-titulo.md`.

Entonces el contenido de cada post puede ser el siguiente:

```yml
---
layout: post
title: Mi primer post
---
## Este es mi primer post

Hola mundo!
```

Ahora podrás acceder a los posts desde la estructura url `tuurl.com/año/mes/dia/titulo.html`.

Este ejemplo se vería así:

![Captura de pantalla](https://i.postimg.cc/3w40nwdV/Captura-de-pantalla-2020-12-15-17-41-59.png){:.responsive-img}

## Includes

A diferencia con los layouts, los includes sirven para insertar código html en páginas, esto permite decidir añadir o no código según necesitemos.

Es normal realizar el código para la navegación o los asides de la página con includes.

Se utiliza la carpeta `_includes` y podemos utilizarlo con el formato:

```html
{% include micodigo %}
```

Creando un simple nav en `_includes/nav.html` para la página en el default por ejemplo,:

```html
<nav>
  <a href="/">Principal</a>
  <a href="/contacto.html">Contacto</a>
</nav>
```

Entonces al default solo añadimos una línea:

```html
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>{{ page.title }}</title>
    </head>
    <body>
        {% include nav %}
        {{ content }}
    </body>
</html>
```

Ahora todas las páginas que tengan default tendrán el código de nav.html

## Data files

Jekyll soporta la carga de datos en formato YAML, JSON o CSV, esto es genial para simplificar el código html y manejar los datos dinámicamente.

La carpeta que se usa es `_data`, por ejemplo podemos crear un `_data/nav.yml` para almacenar los datos de la etiqueta nav:

```yml
- name: Principal
  link: /
- name: Contacto
  link: /contacto.html
```

Ahora modificamos el `_include/nav.html`
```html
<nav>
  {% for item in site.data.nav %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>
```

## Assets

Jekyll usa la siguiente estructura para los assets:

```
.
├── assets
│   ├── css
│   ├── images
│   └── js
...
```
Si usas github pages te recomendaría que utilices un sitio web para almacenar archivos pesados como las imágenes, ya que github solo permite almacenar 1gb de información por repositorio.
{%endraw%}