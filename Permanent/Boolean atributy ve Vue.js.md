---
#aliases: [Boolean atributy ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Boolean atributy ve Vue.js
Některé atributy ve HTML nabývají hodnotu **true/false** identifikovanou pouze jejich přítomností.

Příkladem takového atribut je `disabled`.

Vue zpracuje takový atribut pouze v případě, kdy přiřazná promenná nabývá hodnoty `true`

```vue
<script setup>
import { ref } from 'vue'

const isButtonDisabled = ref(true)
</script>

<template>
 <button :disabled="isButtonDisabled">Button</button>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. 