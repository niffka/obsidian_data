---
#aliases: [Mapování formulářového prvku textarea ve vue.js]
tags: [Honza]
created: 2022-03-08
---

# Mapování formulářového prvku textarea ve Vue.js

Příklad elementu `<textarea>`

```vue
<script setup>
import { ref } from 'vue'

const text = ref('')
</script>

<template>
	<span>Multiline message is:</span>
	<p style="white-space: pre-line;">{{ text }}</p>
	<textarea v-model="text"></textarea>
</template>
```


# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/forms.html#multiline-text