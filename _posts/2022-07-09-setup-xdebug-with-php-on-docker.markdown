---
title: "Setup XDebug with PHP on Docker"
layout: post
categories: ["php", "docker", "xdebug"]
---
## tldr

### PHP Docker
```docker
FROM php:8.1-apache

# Install xdebug
RUN pecl install xdebug-3.1.5 && docker-php-ext-enable xdebug

# Copy configuration file, shown below
COPY docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
```

```ini
# docker-php-ext-xdebug.ini
zend_extension=xdebug
xdebug.mode = debug
xdebug.client_host=host.docker.internal
```

### VSCode
```json
// launch.json
{
    "name": "Listen for Xdebug",
    "type": "php",
    "request": "launch",
    "port": 9003,
    "pathMappings": {
        "/var/www/html": "${workspaceRoot}"
    }
},
```

## Story

I was setting up XDebug for my personal learning project. It was a good learning lesson because this was my first time using Docker instead of a virtual machine. (I am a fan of VirtualBox, Packer, Virtual Machine Image, and Laravel Homestead. Since VirtualBox does not work on M1, it was time to move on to Docker)

Running an Laravel application on Docker was not difficult to setup. Laravel Sail is a turn key solution which I recommend. Otherwise, you have to build it on your own, which was not too bad in my opinion.

However, setting up XDebug was an adventure. A search for PHP XDebug Docker returns many results, none of them works out well for me. However, as we software engineers, we often find bit and piece information from blogs or tutorials and gather them for our own information. As a result, I was able to setup my project with XDebug showing at the top of this blog.
