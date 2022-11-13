---
#aliases: [Podmíněné renderování ve Vue.js šabloně]
tags: [Honza]
created: 2022-03-09
---

# Podmíněné renderování ve Vue.js šabloně
Pomocí atributu `v-if` můžeme definovat podmínku, při jejímž splnění se prvek bude renderovat.  

Stejně jak jsme zvyklí, můžeme používat i další atributy: `v-else` a také `v-else-if`.

```vue
<script setup>
import { ref } from 'vue'

const awesome = ref(true)

function toggle() {
  awesome.value = !awesome.value
}
</script>

<template>
  <button @click="toggle">toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Použití v-if v elementu template]]
	- [[Atributy v-show v template]]
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-6