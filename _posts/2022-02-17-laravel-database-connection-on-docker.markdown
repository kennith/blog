---
title: "Laravel Database Connection on Docker"
layout: post
categories: ["devops, programming, laravel"]
---

Update: It is actually easier to define the environment in environment in docker compose

```env
environment:
- DB_HOST=<e.g. mysql>
```

When I setup my Laravel application using Docker, one of the things really annoys me when I run php artisan migrate, I had to run the command using `docker exec <something>` or `sail artisan queue:work` if you are using Laravel Sail.

It is because by default, in the .env file, it should have the docker database name like this:

```env
DB_HOST=mysql
```

If you run php artisan migrate from the host machine, it will not work because the dns name mysql only recognized by the docker network.

If I changed DB_HOST=localhost, it will work from the host machine, but it will not work in the docker container because the web server and database are on a different container. The web server has its own “IP” and the database has its own “IP”.

I have a working hack that allows me to run `php artisan migrate` from the host machine while the container still have the correct database “IP”.

In the web server container’s apache config file, I added `SetEnv DB_HOST mysql` so that when the web server is looking for `DB_HOST`, it will use mysql instead of `127.0.0.1` in the `.env`
