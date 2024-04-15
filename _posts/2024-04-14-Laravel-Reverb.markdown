---
title: Laravel Reverb
layout: post
categories: ['laravel']
---
Real-time WebSocket is pretty amazing. It is fun to have this technology in your application. The communication is being push to you instead of you requesting it. It is great to have this type of communication when your application is a monitoring service.

[Laravel Reverb](https://reverb.laravel.com/) and [Pusher](https://pusher.com/) provides realtime update service. [Laravel Echo](https://github.com/laravel/echo) integrates with these two service seamlessly. If you are building monitoring service for the web, these stacks are very good choice.

If you are building this with Laravel, these are the initial integration pain I went through. I hope by listing them here will get you up and running even faster.

1. Laravel Queue is by default using database. That means if you are broadcasting event using `dispatch`, make sure you have `php artisan queue:work` running. Otherwise, you can change the `QUEUE_CONNECTION` to `sync`.

2. `cors` is a pain, but **Laravel** has made it easy to deal with. If you are running into `cors` issue, just do `php artisan config:publish cors` and look into `config/cors.php` should most likely resolve your issue.

3. Sanctum config has a pretty standard out of the box setup. If you are not sure, just add your application's domain (with port) to `SANCTUM_STATEFUL_DOMAINS` in `.env`.

4. Use `axios`. It takes care of XSRF with just adding `window.axios.defaults.withXSRFToken = true;`. I also like `window.axios.defaults.headers.common['Content-Type'] = 'application/json';`.

5. The `Network` tab and `WS` filter in Chrome Devtool is your friend working with real-time update service. Look for the protocol you are using and read the `Messages` will give you a lot of information on troubleshooting.

6. It took me a while to figure out, but with Laravel 11, moving `channels.php` to `->withBroadcasting()` with only `auth:sanctum` middleware does not work. I got it to work after adding `api` middleware. I have a [pull request](https://github.com/laravel/docs/pull/9578) open, maybe we will see if the issue I found is relevant.

7. I have a better time creating SPA with default Vue app over Nuxt. It is probably skill issue.

<blockquote class="twitter-tweet" data-dnt="true"><p lang="en" dir="ltr">skill issue</p>&mdash; ThePrimeagen (@ThePrimeagen) <a href="https://twitter.com/ThePrimeagen/status/1683544547660275725?ref_src=twsrc%5Etfw">July 24, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
