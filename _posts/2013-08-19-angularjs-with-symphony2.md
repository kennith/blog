---
layout: post
title: AngularJS with Symphony2
status: publish
categories: General
---
<div><a href="http://angularjs.org/img/AngularJS-large.png"><img border="0" height="55" src="http://angularjs.org/img/AngularJS-large.png" width="200" /></a> <span>+</span> <a href="http://symfony.com/images/common/logo/logo_symfony_header.png"><img border="0" height="50" src="http://symfony.com/images/common/logo/logo_symfony_header.png" width="200" /></a></div>
<div></div>
<p><a href="http://angularjs.org/" target="_blank">AngularJS</a> is great. I personally think it is an upgrade from <a href="http://jquery.com/" target="_blank">jQuery</a>.</p>
<p>I have been testing AngularJS with <a href="http://symfony.com/" target="_blank">Symfony2</a>. One of the problems to build a web application with these two frameworks is that Symfony2's twig language uses the same symbol operator.</p>
For example: PHP uses , AngularJS uses \{\{ \}\}, and Symfony2's twig uses \{\{ \}\} as well.
<p>The solution is to change the default AngularJS symbol to something else.</p>
<p>After your page finish loading the AngularJS, in your script, add the following function:</p>
<p><span>angular.module('apps', [])</span><br /><span>.config(['$interpolateProvider', function ($interpolateProvider) {</span><br /><span>    $interpolateProvider.startSymbol('[[');</span><br /><span>    $interpolateProvider.endSymbol(']]');</span><br /><span>    }]);</span><br /><span><br /></span><span>It change the symbol operator from using \{\{ \}\} to using [[ ]]. </span><br /><span><br /></span><span>Remember, you also need to define your app in your html code inside the . In this case, I define the AngularJS app to use apps, therefore, in my , I need to define it using </span><br /><span><br /></span><span>Have fun coding!</span></p>
