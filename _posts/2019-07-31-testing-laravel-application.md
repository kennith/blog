---
layout: post
title: Testing Laravel Application
date: 2019-07-31 20:16:32.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Laravel
- Web Development
tags: []
meta:
  _publicize_done_13597067: '1'
  _publicize_job_id: '33495557436'
  _publicize_done_external: a:1:{s:7:"twitter";a:1:{i:13540616;s:54:"https://twitter.com/kennith/status/1156659951114342401";}}
  _wpas_done_13540616: '1'
  publicize_twitter_user: kennith
  timeline_notification: '1564604197'
  _oembed_84dd8ae9a3bda50afc977f40fb2ed97b: '<div class="embed-amazon"><iframe title="Coders:
    The Making of a New Tribe and the Remaking of the World" type="text/html" width="500"
    height="550" frameborder="0" allowfullscreen style="max-width:100%" src="https://read.amazon.com/kp/card?preview=inline&linkCode=kpd&ref_=k4w_oembed_Cw9fARRBCkhxy0&asin=B07DBRNN1Z&tag=kpembed-20"></iframe></div>'
  _oembed_time_84dd8ae9a3bda50afc977f40fb2ed97b: '1564700917'
author:
  login: kennith
  email: kennith.leung@gmail.com
  display_name: Kennith
  first_name: ''
  last_name: ''
permalink: "/2019/07/31/testing-laravel-application/"
---
```php
class DeveloperTest extends TestCase {

    public function we_all_should_write_test()
    {
        $this-&gt;assertTrue(true);
    }
}
```

<p><!-- /wp:syntaxhighlighter/code --></p>
<p><!-- wp:paragraph --></p>
<p>If you don't know where to start, <a href="https://jasonmccreary.me/articles/start-testing-laravel/">this</a> is a very good starting point. </p>
<p><!-- /wp:paragraph --></p>
<p><!-- wp:paragraph --></p>
<p>Two points to emphasize:</p>
<p><!-- /wp:paragraph --></p>
<p><!-- wp:list {"ordered":true} --></p>
<ol>
<li>Tests give you confident to change code. (Laracasts)</li>
<li>The value of tests get higher as time goes on. </li>
</ol>
<p><!-- /wp:list --></p>
<p><!-- wp:paragraph --></p>
<p>Usually my workflow is this:</p>
<p><!-- /wp:paragraph --></p>
<p><!-- wp:list {"ordered":true} --></p>
<ol>
<li>How the feature is reached?</li>
<li>What is expected to come out?</li>
</ol>
<p><!-- /wp:list --></p>
<p><!-- wp:paragraph --></p>
<p>That's pretty much it. Write test first, not after. It helps me clarify the problem and write a better solution. </p>
<p><!-- /wp:paragraph --></p>
