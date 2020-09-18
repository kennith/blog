---
title: Laravel 8 Authentication Options
layout: post
categories: ["laravel"]
---
<img src="https://camo.githubusercontent.com/f32ae1200b1b65260e6dcb406d3743fbe2401bbd/68747470733a2f2f6c61726176656c2e636f6d2f6173736574732f696d672f636f6d706f6e656e74732f6c6f676f2d6a657473747265616d2e737667">

Jetstream was released alongside with Laravel 8. It has all the modern authentication method built-in. For example, profile image, password management, two factor authentication, browser session management, and account management. 

You can choose using Livewire or Inertia and the designed is preset using Tailwind. The register, login, and profile pages are ready to use out of the box, unless you need to modify these pages, you don't really know Livewire or Inertia in order to have a fully functional user management system with Jetstream.

Let's say you cannot afford to have Livewire or Inertia added to your application, you can use `Fortify`. 

1. Install Fortify `composer require laravel/fortify`
2. Publish Fortify resources `php artisan vendor:publish --provider="Laravel\\Fortify\\FortifyServiceProvider"`
3. Add `app/Providers/FortifyServiceProvider` in `config/app.php`
4. Manage which services to use in `config/fortify.php`. As of this writing, Fortify documentation recommends only enable `Features::registion()`, `Features::resetPasswords()`, and `Features::emailVerification()`. 

Configuring views

We need to tell Fortify to view the login file. In the `boot` method of `FortifyServiceProvider`. 

Let's take a look at the login as an example. 

```php
Fortify::loginView(function () {
    // resources/views/auth/login.blade.php
    return view('auth.login');
});
```

The required fields are `email` and `password`. It should make a `post` to `/login` route. 

Let's do one more with register

```php
Fortify::loginView(function () {
    // resources/views/auth/register.blade.php
    return view('auth.register');
});
```

The required fields are `name`, `email`, and `password`.

I think Laravel is moving on from `Laravel/Ui`. The authentication portion of `UI` is moved to `Laravel/Jetstream`. Laravel now really don't have a frontend framework preset, it's really up to the developer to choose which one to use. 
