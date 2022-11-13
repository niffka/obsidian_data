---
#aliases: [Hromadné mapování atributů ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Hromadné mapování atributů ve Vue.js
Vue umožňuje rovněž namapovat více atributů hromadně pomocí jednoho objektu:

```vue
<script setup>
import { reactive } from 'vue'

const objectOfAttrs = reactive({
  id: 'container',
  class: 'wrapper'
})
</script>

<template>
  <div v-bind="objectOfAttrs">Text</div>
</template>

<style>
  #container {
    background: green
  }
  .wrapper {
    color: red
  }
</style>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/template-syntax.html#dynamically-binding-multiple-attributes