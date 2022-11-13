---
#aliases: [Skládání komponent pomocí slotů ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Skládání komponent pomocí slotů ve Vue.js
V rámci komponent můžeme rovněž definovat části, které používat `<slot>` pro vkládaní částí z nadřazených komponent do vložených.

Definice slotu ve vnořené komponentě **ChildComp.vue**:
```vue
<template>
  <slot>Fallback content</slot>
</template>
```

Použití slovu v nadřazené komponentě:
```vue
<script setup>
import { ref } from 'vue'
import ChildComp from './ChildComp.vue'

const msg = ref('from parent')
</script>

<template>
  <ChildComp><b>Message: </b>{{ msg }}</ChildComp>
</template>
```

V tomto okamžiku vnořená komponenta funguje jako *wrapper* okolo obsahu který do ní vkládá nadřazená komponenta.

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-14