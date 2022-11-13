---
#aliases: [Zasíláni zpráv mezi komponentami ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Zasíláni zpráv mezi komponentami ve Vue.js
Vnořená komponenta může zasílat zprávy nadřazené komponentě

Definice události `response` ve  vnořené komponentě **ChildComp.vue**:
```vue
<script setup>
const emit = defineEmits(['response'])

emit('response', 'hello from child')
</script>

<template>
  <h2>Child component</h2>
</template>
```

Vnořená komponent emituje událost vždy, když se provádí metoda `setup`

Zachycení události `response` v nadřazené komponentě a její zpracování pomocí arrow funkce:
```vue
<script setup>
import { ref } from 'vue'
import ChildComp from './ChildComp.vue'

const childMsg = ref('No child msg yet')
</script>

<template>
  <ChildComp @response="(msg) => childMsg = msg" />
  <p>{{ childMsg }}</p>
</template>
```

~~~ad-attention
title: Znak `@` nahrazuje direktivu `v-on`.
~~~


# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-13