---
#aliases: [Zpracování html formulářů ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Zpracování html formulářů ve Vue.js
Vue poskytuje řadu nástrojů a mechanizmů pro zpracováni HTML formulářů.

V podstatě se jedná o obousměrnou vazbu mezi tagem `input` a proměnou. 
- Pro směr z **html -> js** používáme `v-on`/`@`
- Pro směr **js -> html** pak `v-bind`/`:`

```vue
<script setup>
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <input :value="text" @input="text = $event.target.value">
  <p>{{ text }}</p>
</template>
```

~~~ad-info
collapse: true

Můžete rovněž použít 

**1. Arrow funkci**
```vue
  <input :value="text" @input="(event) => text = $event.target.value">
```

**2. obyčejnou funkci** 
```vue
function onInput(e) {
  // a v-on handler receives the native DOM event
  // as the argument.
  text.value = e.target.value
}
```

```vue
<input :value="text" @input="onInput">
```
~~~

Tuto obousměrnou smyčku můžeme zjednodušit pomocí atributu `v-model`:

```vue
<script setup>
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <input v-model="text">
  <p>{{ text }}</p>
</template>
```

`v-model` je kromě `<input>` možné použít na další typy tagů:
- `<textarea>` se mapuje stejně jako `<input>` na atributy `value` a `input`,
- `<input type="checkbox">` a `<input type="radio">` se mapuje na `checked` vlastnost a `change` událost,
-   `<select>` element se mapuje na `value` vlastnost a událost `change` .``

# Reference 
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Mapování formulářového prvku textarea ve Vue.js]]
	- [[Mapování formulářového prvku checkbox ve Vue.js]]
	- [[Mapování formulářového prvku radio ve Vue.js]]
	- [[Mapování formulářového prvku select ve Vue.js]]
	- [[Povázávání hodnot formulářových prvků ve Vue.js]]
	- [[Modifikátory v-model atributu]]
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-5