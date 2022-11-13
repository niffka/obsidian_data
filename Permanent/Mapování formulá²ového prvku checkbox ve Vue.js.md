---
#aliases: [Mapování formulářového prvku checkbox ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Mapování formulářového prvku checkbox ve Vue.js
Mapování elementu `<input type="checkbox"`

```vue
<script setup>
import { ref } from 'vue'

const checked = ref(false)
</script>

<template>
  <input type="checkbox" id="checkbox" v-model="checked" />
  <label for="checkbox">{{ checked }}</label>
</template>
```

Další užitečnou možností je propojení několika checkboxů s polem

```vue
<script setup>
import { ref } from 'vue'

const checkedNames = ref([])
</script>

<template>
  <div>Checked names: {{ checkedNames }}</div>
	<hr/>
  <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
  <label for="jack">Jack</label>

  <input type="checkbox" id="john" value="John" v-model="checkedNames">
  <label for="john">John</label>

  <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
  <label for="mike">Mike</label>
</template>
```
# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/forms.html#checkbox