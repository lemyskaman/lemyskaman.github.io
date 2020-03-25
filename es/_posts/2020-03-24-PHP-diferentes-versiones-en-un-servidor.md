---
title: PHP Diferentes versiones en un servidor
crawlertitle: PHP Diferentes versiones en un servidor
summary: php para todo
date: 2020-03-24T20:00:00.000+00:00
categories: posts
tags: guides_and_tutorials
author: Lemys Lopez
lang-ref: running-multiple-versions-of-php-on-server
bg: "/bg.svg"

---

Aveces queremos compartir los recursos disponibles de nuestro servidor entre diferentes aplicaciones o soluciones escritas en diferentes versiones de PHP, Sin embargo por lo general en el repositorio de nuestro sistema operativo (alemnos en debian y ubuntu ) solo encontramos una version disponible o un muy limitado rango de versiones a instalar.

Si bien la comunidad que desarrolla php junto a la mayoría de los cms, aplicaciones y frameworks desarrollados en php, hacen lo posible en respetar la filosofía de "backward compatibility" (que traducido al español es compatibilidad hacia atrás), algunos cambios y mejoras introducidas en la especificación de el lenguaje junto a a la eliminación de características marcadas como obsoletas impiden que código escrito en versiones antiguas sean correctamente ejecutadas por el interprete de php.

Una solucion simple y directa para que coexistan diferentes versiones de php, probada en ubuntu 18.04 que deberia funcionar tambien en versiones superiores, seria añadir el  [repositorio PPA](https://launchpad.net/~ondrej/+archive/ubuntu/php)  de [Ondřej Surý](https://twitter.com/oerdnj) que nos pone a disposicion la version 5.6 de php y las mayores a 7.0 y desde donde podemos instalarlas para que coexistan (todas inclusive) en un mismo sistema operativo. 

Para añadir el repositorio a nuestro sistema solo es necesario ejecutar el siguiente comando:

    $sudo add-apt-repository ppa:ondrej/php

Luego actualizamos la lista de paquetes:

    $sudo apt-get update 

Si usas Apache como servidor http puedes ejecutar cualquiera de los siguientes comandos segun la version que deseas instalar:

    $sudo apt install php5.6   [PHP 5.6]
    $sudo apt install php7.0   [PHP 7.0]
    $sudo apt install php7.1   [PHP 7.1]
    $sudo apt install php7.2   [PHP 7.2]
    $sudo apt install php7.3   [PHP 7.3]
    $sudo apt install php7.4s   [PHP 7.4]

Si el caso es nginx entonces debes instalar la fpm de la version:

    $sudo apt install php5.6-fpm   [PHP 5.6]
    $sudo apt install php7.0-fpm   [PHP 7.0]
    $sudo apt install php7.1-fpm   [PHP 7.1]
    $sudo apt install php7.2-fpm   [PHP 7.2]
    $sudo apt install php7.3-fpm   [PHP 7.3]
    $sudo apt install php7.4-fpm   [PHP 7.4]



