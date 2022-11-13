---
#aliases: [Procházení objektů ve Vue.js šabloně]
tags: [Honza]
created: 2022-03-09
---

# Procházení objektů ve Vue.js šabloně
Atribut `v-for` nemusí iterovat jen přes seznamy, může procházet i objekty:

```vue
<script setup>
  import { reactive } from 'vue'
const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})
</script>

<template>
  <ul>
    <li v-for="(value, key) in myObject">
      {{ key }}: {{ value }}
    </li>
  </ul>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/list.html#v-for-with-an-object