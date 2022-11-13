---
#aliases: [Mapování formulářového prvku radio ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Mapování formulářového prvku radio ve Vue.js
Tento element je rovněž velmi snadný na použití:

```vue
<script setup>
import { ref } from 'vue'

const picked = ref(null)
</script>

<template>
  <div>Picked: {{ picked }}</div>
  <hr/>
  <input type="radio" id="one" value="One" v-model="picked" />
  <label for="one">One</label>

  <input type="radio" id="two" value="Two" v-model="picked" />
  <label for="two">Two</label>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/forms.html#radio