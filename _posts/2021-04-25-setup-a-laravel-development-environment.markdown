---
title: Setup a Laravel Development Environment
layout: post
categories: ['laravel', 'development']
---
There are many choices to set up a Laravel development environment. I think in general, the Laravel team [has provided](https://laravel.com/docs/8.x/installation#your-first-laravel-project) many good choices to get the development started. 

If you are really starting from scratch with minimal computer knowledge, I think you should go with [WAMP](https://www.wampserver.com/en/) or [MAMP](https://www.mamp.info/en/mac/). It has a web server and database ready to go out of the box. 

Once your application needs more services, such as S3, there are plenty of options for next steps. 

Laravel Homestead is a really good choice. In my opinion, it has packaged a lot of services that I think covered for an everyday average (or even above average) Laravel development. The setup is easy and straight forward if you follow the instruction provided in the documentation.

Laravel Sail is a docker equivalent of Homestead. While the industry is leaning forward to container technology (Docker or Kubernetes), Sail seems to close the architectural gap(?) between developer and ops. (I often found this a non issue)

I have been a long time Laravel Homestead user, but VirtualBox does not look like will support M1 chip anytime soon, so I got myself ready for Docker. This [Artisanship](https://github.com/kennith/artisanship) is a starting point for me, but I think you should just use [Laravel Sail](https://laravel.com/docs/8.x/sail#introduction).

Note: There is no argument on what tool is best, it depends on your situation is and use what you like best. 
