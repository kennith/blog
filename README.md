![tweet](https://github.com/kennith/blog/workflows/tweet/badge.svg)

# always learning

This is my personal blog. You can view the source code here.

The site url is https://kennith.github.io

## Stacks

- Jekyll
- SCSS

## Setup

1. Install Ruby from Homebrew `brew install ruby@2.7`
2. Run `bundle` (Install bundles)
3. Run `bundle exec jekyll serve` (--livereload)

## SDLC

1. Commit using `npm run commit`

## Amazon Embed

Add this into Sublime Text `/Packages/User/amazon-preview.sublime-snippet`

```xml
<snippet>
    <content><![CDATA[
<iframe 
    src="https://read.amazon.com/kp/card?asin=${1:asin-code}&preview=inline&linkCode=kpe"
    type="text/html" 
    sandbox="allow-scripts allow-same-origin allow-popups" 
    width="336" height="550" 
    frameborder="0" 
    allowfullscreen 
    style="max-width:100%" 
    >
</iframe>
]]></content>
    <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
    <!-- <tabTrigger>hello</tabTrigger> -->
    <!-- Optional: Set a scope to limit where the snippet will trigger -->
    <!-- <scope>source.python</scope> -->
    <description>Inert Amazon preview card</description>
</snippet>
```

Replace `asin-code` with the ASIN is from link, e.g. B079WM7KLS in https://www.amazon.com/dp/B079WM7KLS
