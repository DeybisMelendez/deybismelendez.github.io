---
layout: post
title: Como crear un blog desde cero con Jekyll y Github Pages
thumbnail: 
---

En este post aprenderás como crear un sitio web sencillo o blog con jekyll desde cero y publicarlo en github pages sin gastar dinero en hosting ni dominio.

## Pre-requisitos

Es necesario tener instalado git, un editor de código como Visual Studio Code, tener una cuenta en Github.

## 1. Instalar Ruby-full

Lo primero que debemos hacer es instalar Ruby. Para el caso de Linux con el comando:

`sudo apt-get install ruby-full build-essential zlib1g-dev`

## 2. Instalar Jekyll y Bundler

Una vez instalado Ruby, instalamos Jekyll y bundler con el comando:

`gem install jekyll bundler`

## 3. Crear repositorio en Github

Ahora creamos un nuevo repositorio en Github, si utilizamos la estructura **nombreUsuario.github.io** para el nombre, ese sería la url de la página, de lo contrario estaría ubicada en **nombreUsuario.github.io/nombre-repositorio**

Opcionalmente creamos el REAME.md y una licencia. Github tiene un archivo .gitignore para Jekyll, o puedes añadirlo manualmente:


```
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata
```

## 4. Clonamos el repositorio

Nos ubicamos en la terminal donde queramos trabajar el sitio web y clonamos:

```git clone https://github.com/usuario/turepositorio.com```

## 5. Crear proyecto Jekyll para Github Pages

Nos ubicamos en la carpeta del repositorio y en la terminal ejecutamos:

```bundle init```

Esto nos creará un archivo llamado Gemfile, lo abrimos y añadimos la siguiente línea:

```gem "github-pages", group: :jekyll_plugins```

ahora en la terminal ejecutamos:

```bundle```

## 6. Ejecutamos en local el sitio

Ahora ya puedes ejecutar el sitio en tu repositorio local con el comando:

```bundle exec jekyll serve```

Ahora verás algo como esto en el localhost:

![Captura-de-pantalla-2020-12-15-16-30-22.png](https://i.postimg.cc/d1v9Zd0w/Captura-de-pantalla-2020-12-15-16-30-22.png)

## 7. Actualizamos el repositorio en github

En la terminal puedes ejecutar los siguientes comandos:

```
git add .
git commit -m "proyecto jekyll creado"
git push
```

Ahora podrás ver el sitio web creado en la página de github pages.

Ya puedes trabajar tu sitio creando el index.html por ejemplo, puedes ver mi tutorial sobre Jekyll.