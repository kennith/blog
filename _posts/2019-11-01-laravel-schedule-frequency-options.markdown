---
title: Laravel Schedule Frequency Options
layout: post
categories: ['laravel']
---
I have a tasks schedule to run every Monday and Wednesday, I set the scheduler to run like below:

```php
// Incorrect.
$schedule->command('inspire')
         ->weekly()
         ->wednesdays()
         ->fridays()
         ->at('05:00');
```

At first, I thought it would run every Wednesday and Friday. Reading more carefully with the [documentation](https://laravel.com/docs/6.x/scheduling), `wednesdays()` and `fridays()` are the **schedule constraints**. The way I setup meaning that it will honor the last contraint I set. In this case, it will be `fridays()`.

So, one way to meet my requirement with the fluent schedule setters with Laravel, it will be:

```php
$schedule->command('inspire')
         ->cron('* * * * 3,5')  // Wednesday and Friday
         ->at('05:00');
```

Of course, you can set it as

```php
$schedule->command('inspire')
         ->cron('5 5 * * 3,5');
```

It's up to you.

