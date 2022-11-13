---
#aliases: [Mapování formulářového prvku select ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Mapování formulářového prvku select ve Vue.js
Zde můžeme použít dvě varianty:

1. Jednoduchý select

```vue
<script setup>
import { ref } from 'vue'

const selected = ref(null)
</script>

<template>
  <div>Selected: {{ selected }}</div>
	<hr/>
  <select v-model="selected">
    <option disabled value="">Please select one</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
</template>
```

2. Vícenásobný select

```vue
<script setup>
import { ref } from 'vue'

const selected = ref(null)
</script>

<template>
	<div>Selected: {{ selected }}</div>
	<hr/>
	<select v-model="selected" multiple>
	  <option>A</option>
	  <option>B</option>
	  <option>C</option>
	</select>
</template>
```

3. Select z definovaný nabídkou v JS pomocí `v-for` atributu
```vue
<script setup>
import { ref } from 'vue'

const selected = ref('A')

const options = ref([
  { text: 'One', value: 'A' },
  { text: 'Two', value: 'B' },
  { text: 'Three', value: 'C' }
])
</script>

<template>
	<div>Selected: {{ selected }}</div>
	<hr/>
	<select v-model="selected">
		<option v-for="option in options" :value="option.value">
	    {{ option.text }}
	    </option>
	</select>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/forms.html#select