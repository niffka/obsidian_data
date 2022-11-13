---
#aliases: [Deklarativní vykreslování ve Vue.js template]
tags: [Honza]
created: 2022-03-08
---

# Deklarativní vykreslování ve Vue.js šabloně
V rámci Vue.js template používá "Mustache" syntaxi pro vkládání hodnot do html.

```vue
<template>
<span>Message: {{ msg }}</span>
</template>
```

Díky **Deklartivnímu vykreslování** Vue monitoruje stav proměnných a překresluje šablonu v případě jejich změny.

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Reaktivní objekty ve Vue.js]]
	- [[Reaktivní proměnné ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/guide/essentials/template-syntax.html#text-interpolation