---
#aliases: [Práce s atributy ve Vue.js šabloně]
tags: [Honza]
created: 2022-03-08
---

# Práce s atributy ve Vue.js šabloně
Proměnné můžeme také provázat s hodnotami atributů HTML tagů.
K tomu slouží direktiva `v-bind`.

```vue
<script setup>
import { ref } from 'vue'

const titleClass = ref('green')
</script>

<template>
	<div v-bind:class="titleClass">Text</div>
</template>

<style>
.green {
  color: green;
}
.red {
  color: red;
}
</style>
```

Stejně jako události i `v-bind` je natolik často používaný, ze se zkracuje na `:`.

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Boolean atributy ve Vue.js]]
	- [[Hromadné mapování atributů ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/guide/essentials/template-syntax.html#attribute-bindings