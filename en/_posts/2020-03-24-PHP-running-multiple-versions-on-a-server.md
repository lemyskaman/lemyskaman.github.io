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
Most of the time we want to share the resources of our server among different applications written in also different php versions. But normaly our web server os, ships with a close range of different php versions or with only one available version to install.

The people behind php and its community including cms, apps and frameworks creators, do their best on what  is known as backward compatibility. But some changes and upgrades introduced on the language specification together with the deprecation of some characteristics makes hard to allow legacy code to be interpreted by the php preprocesor

One proved simple solution to allow the coexistence of multiple php versions  on ubuntu >=18.04 would be to add the [PPA](https://launchpad.net/\~ondrej/+archive/ubuntu/php) repository of  [Ondřej Surý](https://twitter.com/oerdnj), in which we can find the 5.6 version and all above 7.0, available to install in the same OS.

We only need to run the next command to add the repository:

    $sudo add-apt-repository ppa:ondrej/php

Then we update all packages:

    $sudo apt-get update 

If you use Apache as http server you can run any of the next commands depending of the versions you want to install

    $sudo apt install php5.6   [PHP 5.6]
    $sudo apt install php7.0   [PHP 7.0]
    $sudo apt install php7.1   [PHP 7.1]
    $sudo apt install php7.2   [PHP 7.2]
    $sudo apt install php7.3   [PHP 7.3]
    $sudo apt install php7.4s   [PHP 7.4]

Otherwise if you are nginx user the you should use the related fpm version:

    $sudo apt install php5.6-fpm   [PHP 5.6]
    $sudo apt install php7.0-fpm   [PHP 7.0]
    $sudo apt install php7.1-fpm   [PHP 7.1]
    $sudo apt install php7.2-fpm   [PHP 7.2]
    $sudo apt install php7.3-fpm   [PHP 7.3]
    $sudo apt install php7.4-fpm   [PHP 7.4]