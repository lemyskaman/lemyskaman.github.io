---
title: Sitio web con jekyll en github
crawlertitle: Sitio web con jekyll en github
summary: Jekyll + github = Tu sitio
date: 2019-04-27T04:00:00.000+00:00
categories: posts
tags: guides_and_tutorials
author: Lemys Lopez
lang-ref: jekyll-on-github-website
sumary: Pagina con Jekyll Github
bg: "/jekyll_on_github.png"
---

Github es bien conocido como "la base de datos más grande de código fuente de software" pero hoy en día parte de su cartera de servicios gratis, te permite servir archivos web estáticos para tu propio sitio, (de la misma forma como funciona este sitio). Estas líneas pretenden ser una guía en el proceso de publicar en github archivos web, generados por una herramienta bastante popular creada con ruby llamada Jekyll, usando la consola de comandos.

En esta guía **yo asumo que cuentas con algo de conocimientos sobre cómo funciona un sitio web, algo de experiencia usando git con una cuenta de github,** y también que usas una versión reciente de alguna distribución Debian o basada en Debian como Ubuntu, me centraré únicamente en el proceso de crear un sitio nuevo de jekyll localmente y entonces subirlo a github.

#### Instalando Dependencias

Jekyll fue programado con ruby, y por tanto hace bastante uso de algunas de sus gemas, también son necesarias algunas librerías y archivos de cabecera, distribuidas para nosotros dentro de los paquetes .deb: build-essential y zlib1-dev. Estos paquetes pueden ser instalados con tu gestor de paquetes favoritos o con apt como a continuación:

    $ sudo apt-get install ruby-full build-essential zlib1g-dev git

#### Configurando las gemas que son necesarias

No es buena idea instalar las gemas de ruby como superusuario, es por esto que es recomendable crear un directorio en la carpeta personal de nuestro usuario de nuestro sistema operativo, así que sera esto lo que haremos con los siguientes comandos

    $ cd ~
    $ mkdir gems

Ahora es necesario editar el archivo \~/.bashrc, añadiendo una variable de entorno nueva(**GEM_HOME**), y actualizando el valor de una existente (**PATH**),  puedes usar tu editor de texto favorito aunque yo prefiero nano:

    $ nano .bashrc

Luego al final del archivo escribe lo siguiente:

    #gemas
    export GEM_HOME="$HOME/gems"
    export PATH="$HOME/gems/bin:$PATH"

Finalmente cargamos el script, y estamos listos para usar las gemas de ruby:

    $ source ~/.bashrc

#### Instalando jekyll y github-pages

Ahora con un entorno ruby instalado correctamente, nosotros podemos continuar con la instalación de jekyll, de una utilidad llamada bundler y de una gema creada por la gente de github.com con todo lo necesario para para hacer funcionar nuestro sitio en sus servidores:

    $ gem install jekyll bundler git  github-pages

Hasta ahora, si todo nos ha salido bien, estamos listos para crear un nuevo sitio jekyll de forma local.

#### Creando un sitio con jekyll

Podemos crear un nuevo sitio usando el comando jekyll de la siguiente forma:

    $ jekyll new usuario.github.io

Donde “usuario” es el username de nuestra cuenta en github (en mi caso mi cuenta es lemyskaman), luego nos dirigimos a la nueva carpeta creada por jekyll :

    $ cd user.github.io

Deberías ver una estructura de archivos como esta:

    $ tree
    ├── 404.html
    ├── about.md
    ├── _config.yml
    ├── Gemfile
    ├── index.md
    └── _posts
            └── 2019-04-29-welcome-to-jekyll.markdown

#### Editando el archivo Gemfile para github, actualizar las gemas y probar.

Es necesario comentar la línea que usa la versión de consola de jekyll y descomentar la que instala la gema de github-pages para hacer eso simplemente agrega a inicio de la línea 11 un # , y borra el numeral # de el inicio de la línea 18, el Gemfile debería verse de la siguiente forma para la versión 3.8.x de jekyll o parecido en otras versiones:

{% highlight bash %}
10 # Happy Jekylling!
11 gem "jekyll", "\~> 3.8.5"
12
13 # This is the default theme for new Jekyll sites. You may change this to anything you lik$
14 gem "minima", "\~> 2.0"
15
16 # If you want to use GitHub Pages, remove the "gem "jekyll"" above and
17 # uncomment the line below. To upgrade, run \`bundle update github-pages\`.
18 # gem "github-pages", group: :jekyll_plugins
{% endhighlight %}

Ahora puedes actualizar las gemas usando el comando bundle:

    $ bundle update

Jekyll viene con un servidor web para pruebas locales, mientras que la herramienta bundle supervisa nuestro código y “re-compila” nuestro sitio, a medida que lo modificamos localmente, para correr el servidor ejecutamos lo siguiente:

    $ bundle exec jekyll serve --host=0.0.0.0

Ahora abre tu explorador web favorito apuntando a la dirección  http://localhost:4000 y deberías ver tu sitio.

#### Subir tu sitio a github y hacerlo publico

Primero es necesario crear un repositorio en [http://github.com](http://github.com "github") usando tu no nombre de usuario en github  como prefijo a .github.io, en pocas palabras crea un proyecto con el nombre de la carpeta creada con jekyll en uno de los pasos anteriores, que contiene los archivos de tu sitio (usuario.github.io), luego inicializamos git y lo configuramos  para seguir la rama de tu proyecto con los siguientes comandos :

    $ git init
    $ git remote add origin git@github.com:usuario/usuario.github.io
    $ git push -u origin master

Recuerda siempre reemplazar usuario con el tu nombre de usuario en github y finalmente tu sitio debería estar disponible en http://user.github.io.

Como un administrador de contenido Jekyll tiene bastantes ventajas, al usar el mecanismo de plantillas [liquid](https://shopify.github.io/liquid/ "liquid"), básicamente funciona tomando el texto de archivos tipo [markdown](https://es.wikipedia.org/wiki/Markdown "markdown") junto a la data en su cabecera ( [front matter](https://jekyllrb.com/docs/front-matter/ "jekyll front matter") ) para construir el sitio, yo haré un post explicando mas detalladamente como funciona cómo se usa y las cosas que he aprendido acerca de el uso y las bondades de jekyll.