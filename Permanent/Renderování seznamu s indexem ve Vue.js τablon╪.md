---
#aliases: [Renderování seznamu s indexem ve Vue.js šabloně]
tags: [Honza]
created: 2022-03-09
---

# Renderování seznamu s indexem ve Vue.js šabloně
Pokud při procházení seznamu chceme znát i pořadí prvku, můžeme použit: `v-for="(item, index) in items"`.

```vue
<script setup>
import { ref } from 'vue'
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
</script>

<template>
  <ul>
    <li v-for="(item, index) in items">
      {{ index }} - {{ item.message }}
    </li>
  </ul>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/list.html#v-for