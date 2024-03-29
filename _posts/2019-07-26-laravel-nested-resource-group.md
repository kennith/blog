---
layout: post
title: Laravel Nested Resource Group
date: 2019-07-26 13:38:27.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- General
tags: []
meta:
  _publicize_done_external: a:1:{s:7:"twitter";a:1:{i:13540616;s:54:"https://twitter.com/kennith/status/1154747823549632517";}}
  _publicize_job_id: '33296189909'
  timeline_notification: '1564148309'
  _publicize_done_13597067: '1'
  _wpas_done_13540616: '1'
  publicize_twitter_user: kennith
  _oembed_ae7e165d1b36f5742e2500be93f254d0: '<div class="embed-amazon"><iframe title="The
    Manager&#039;s Path: A Guide for Tech Leaders Navigating Growth and Change" type="text/html"
    width="500" height="550" frameborder="0" allowfullscreen style="max-width:100%"
    src="https://read.amazon.com/kp/card?preview=inline&linkCode=kpd&ref_=k4w_oembed_YCzrPBsxbRxAPw&asin=B06XP3GJ7F&tag=kpembed-20"></iframe></div>'
  _oembed_time_ae7e165d1b36f5742e2500be93f254d0: '1564602595'
author:
  login: kennith
  email: kennith.leung@gmail.com
  display_name: Kennith
  first_name: ''
  last_name: ''
permalink: "/2019/07/26/laravel-nested-resource-group/"
---
<p>When I started with Laravel, <a href="https://laravel.com/docs/5.1/controllers#restful-nested-resources">nested resource group</a> was available. I liked it because I can easily create a beautiful URL with ease. For example, to generate an URL like this<code>/user/1/blog/10</code>, I just need to nest my route with this:</p>

```php
class BlogController
{
    public function show(User $user, Blog $blog) 
    {
        //... 
    }
}
```

<p>Since 5.2, this option is removed from documentation (but still available to use). So I was wondering why and I found someone already spotted this and submit a merge request. However, it was not merged with the reason below given by @taylorotwell. </p>
<p><!-- /wp:paragraph --></p>
<p><!-- wp:image {"id":1342,"linkDestination":"custom"} --></p>
<img src="https://kennith.files.wordpress.com/2019/07/image.png" alt="" class="" />
<figcaption>Interesting...</figcaption>
</figure>
<p><!-- /wp:image --></p>
<p><!-- wp:paragraph --></p>
<p>OK, no problem. I will take his word for it. Since you can archieve something similar with alternative approach, e.g.</p>
<p><!-- /wp:paragraph --></p>
<p><!-- wp:syntaxhighlighter/code {"language":"php","lineNumbers":false} --></p>
<pre class="wp-block-syntaxhighlighter-code">Route::post('user/{$user}/blog/{$blog}', 'BlogController@store');
Route::resource('blog', 'BlogController')-&gt;except(['store']);</pre>
<p><!-- /wp:syntaxhighlighter/code --></p>
<p><!-- wp:paragraph --></p>
<p>but... I still want to know why it is not a good idea? I want to find out... so I can become a better developer. </p>
<p><!-- /wp:paragraph --></p>
<p><!-- wp:paragraph --></p>
<p>Is it because of <strong>security</strong>? This is the first thing I come of mind. Assuming the URL meant to let user store or view their own blog, e.g. user Alice with user id <code>1</code>, and she has blog entries <code>10,11,12</code>. Does it mean if she access URL <code>user/1/25</code> will be a problem? I don't think so given if <strong><a href="https://laravel.com/docs/5.1/authorization#policies">Policy</a></strong> is setup properly. </p>
<p><!-- /wp:paragraph --></p>
<p><!-- wp:paragraph --></p>
<p>The other thing I can think of is keeping the route simple. It is because if your model route key name is not its ID but a customized <code>route key name</code>, the URL will be very long. e.g., using the route example above, if the user model route key name is user's name and the blog model route key name is the blog title, the route will be <code>user/alice/blog/this-is-my-title-of-my-blog</code>. It is definitely longer than <code>blog/this-is-my-title-of-my-blog</code>. </p>
<p><!-- /wp:paragraph --></p>
<p><!-- wp:paragraph --></p>
<p>There must be some disadvantage of using nested route, what do you think it is?</p>
<p><!-- /wp:paragraph --></p>
