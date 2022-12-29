---
title: Develop NPM Package Locally
layout: post
categories: ["programming"]
---
Steps to develop an NPM package without publishing it on NPM.

### Creating a package

1. Create a folder name `example-js`
2. `cd example-js`
3. `npm init --scope=@example-org`
4. Create a file named `index.js` and add your function.

As an example, I created a function name `sum`

```javascript
export default function sum(x, y) {
    return x + y;
}
```

### Test out package

I use `nuxtjs` framework as an example.

1. Run `npm init nuxt-app test-example-js`
2. Run `npm link ../example-js`. (I put text-example-js and example-js on the same folder level)
3. As an example, edit `index.vue` and add the following lines

```vuejs
<script setup>
	import sum from '@example-org/example-js'

	const testSumJs = computed(() => {
		return sum(1, 2);
	})
</script>
```

### Cleanup

Once you done testing the NPM package locally, remove the local link: `npm unlink example-js`

