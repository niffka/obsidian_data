---
#aliases: [Příklad použití ref k řízení focus ve Vue.js šabloně]
tags: [Honza]
created: 2022-03-09
---

# Příklad použití ref k řízení focus ve Vue.js šabloně
Následující příklad ukazuje scénář, kdy chceme na stavit fokus na určitý prvek na stránce

```vue
<script setup>
import { ref, onMounted } from 'vue'

// declare a ref to hold the element reference
// the name must match template ref value
const input = ref(null)

onMounted(() => {
  input.value.focus()
})
</script>

<template>
  <input ref="input" />
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/template-refs.html#accessing-the-refs