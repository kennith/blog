---
layout: post
title: Testing Laravel Application
categories: [laravel, web-development]
---
```php
class DeveloperTest extends TestCase {
    /**
     * Why?
     */
    public function we_all_should_write_test()
    {
        $this->assertTrue(true);
    }
}
```

If you don't know where to start, [this](https://jasonmccreary.me/articles/start-testing-laravel/) is a very good starting point. </p>

Two points to emphasize:

- Tests give you confident to change code. (Laracasts)
- The value of tests get higher as time goes on. 

Usually my workflow is this:

- How the feature is reached?
- What is expected to come out?

That's pretty much it. Write test first, not after. It helps me clarify the problem and write a better solution.
