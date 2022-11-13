---
#aliases: [Inline definice posluchače události ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Inline definice posluchače události ve Vue.js
Pokud do hodnoty atributu `@event=`  napišme příkaz v jazyce JavaScript, pak je tento příkaz vyhodnocen jako _inline handler_.

```vue
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <button @click="count++">count is: {{ count }}</button>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Volání method v rámci inline posluchače události ve Vue.js]]
	- [[Přístup k objektu Event v rámci inline metody ve Vue.js]]
	- [[Dynamické argumenty ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/guide/essentials/event-handling.html#method-vs-inline-detection