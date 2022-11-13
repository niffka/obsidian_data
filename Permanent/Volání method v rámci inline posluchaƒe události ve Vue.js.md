---
#aliases: [Volání method v rámci inline posluchače události ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Volání method v rámci inline posluchače události ve Vue.js
Namísto přímé vazby na název metody u `@event=` atributu, můžeme také dodefinovat volání metody.

To nám umožňuje předat vlastní argumenty metody namísto nativní události:

```vue
<script setup>
	function say(message) {
	  alert(message)
	}
</script>

<template>
	<button @click="say('hello')">Say hello</button>
	<button @click="say('bye')">Say bye</button>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/event-handling.html#calling-methods-in-inline-handlers