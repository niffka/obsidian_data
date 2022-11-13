---
#aliases: [Definice property v komponentě ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Definice property v komponentě ve Vue.js
Nadřazená komponenta může vložit do vnořené komponenty dat pomoci property.

Definice property `msg` ve vnořené komponentě **ChildComp.vue**:
```vue
<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <h2>{{ msg || 'No props passed yet' }}</h2>
</template>
```

Nastavení vlastnosti v nadřazené komponentě:
```vue
<script setup>
import { ref } from 'vue'
import ChildComp from './ChildComp.vue'

const greeting = ref('Hello from parent')
</script>

<template>
  <ChildComp :msg="greeting" />
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-12