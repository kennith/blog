---
title: Upgrade Laravel Installer
layout: post
categories: ["programming", "laravel"]
---
Laravel 8 is to be released on September 8, 2020. Along with the framework upgrade is the change in `Laravel Installer`.

Up until `Laravel Installer` version 3.2.0, when you do `laravel new <project-name>`, the installer [downloads](https://github.com/laravel/installer/blob/v3.2.0/src/NewCommand.php#L153) the build from a build server. The build server will be [shutdown](https://twitter.com/taylorotwell/status/1301522915003895808) couple months after Laravel 8 released. 

Therefore, it's important to run the composer update on the `Laravel Installer`.

## Steps

1. Edit `$HOME/.composer/composer.json`
2. Update `laravel/installer` to `^4.0`
3. Run `composer global update laravel/installer`
4. Verify by execute `laravel --version`
