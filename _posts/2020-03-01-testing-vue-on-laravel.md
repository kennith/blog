---
title: Testing Vue on Laravel
layout: post
categories: ['vue', 'laravel', 'testing']
---
tl;dr version of getting Vue unit testing starting on a Laravel app.

## NPM

1. npm install --save-dev @vue/test-utils mocha mochapack
1. npm install --save-dev jsdom jsdom-global
1. npm install --save-dev expect

## Configuration (opininated)

1. Add tests/Vue/setup.js
2. Add tests/Vue/components/
3. Add test `scripts` to `package.json`

setup.js

```javascript
require('jsdom-global')()
global.expect = require('expect')
```

package.json

```json
"test": "mochapack --webpack-config node_modules/laravel-mix/setup/webpack.config.js --require tests/Vue/setup.js tests/Vue/component
```
