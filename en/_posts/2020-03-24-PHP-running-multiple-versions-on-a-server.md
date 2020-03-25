---
title: PHP Running Multiple Versions on a Server
crawlertitle: PHP Running Multiple Versions on a Server
summary: php para todo
date: 2020-03-24T20:00:00.000+00:00
categories: posts
tags: guides_and_tutorials
author: Lemys Lopez
lang-ref: php-running-multiple-versions-on-a-server
bg: "/bg.svg"

---



Most of the time we want to share the resources of our server among diferent aplications written in also diferent php versions. But normaly our web server os, ships with a close range of diferente php versions or with only one avaibale version to install. 

Si bien la comunidad que desarrolla php junto a la mayoría de los cms, aplicaciones y frameworks desarrollados en php, hacen lo posible en respetar la filosofía de "backward compatibility" (que traducido al español es compatibilidad hacia atrás), algunos cambios y mejoras introducidas en la especificación de el lenguaje junto a a la eliminación de características marcadas como obsoletas impiden que código escrito en versiones antiguas sean correctamente ejecutadas por el interprete de php.

The people behind php and it comunity including cms, apps and frameworks creators do their best on whats is known as backward compatbility. But some changes and upgrades introudced on the language spesification togeter with the deprecation of some characteristics makes hard to allow legacy code to be interpeted by the php preprocesor    

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



