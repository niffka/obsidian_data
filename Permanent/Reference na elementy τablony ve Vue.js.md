---
#aliases: [Reference na elementy šablony ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Reference na elementy šablony ve Vue.js
Pomocí atributu `ref` můžeme přistupovat k elementu šablony přímo, jako bychom si jej vytáhli například pomocí knihovny jQuery.

Základní použití je následující:
```vue
<script setup>
import { ref } from 'vue'

const p = ref(null)
</script>

<template>
  <p ref="p">hello</p>
</template>
```

Jak je vidět proměnná `p` je inicializovaná na hodnotu `null`. 
Pokud chceme provádět s elementy operace v kódu, musíme to udělat až po té, co Vue komponentu připojí. 

K to tomu účelu slouží metoda `onMounted`
```vue
<script setup>
import { ref, onMounted } from 'vue'

const p = ref(null)

onMounted(() => {
  p.value.textContent = 'mounted!'
})
</script>

<template>
  <p ref="p">hello</p>
</template>
```


# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Životní cyklus komponent ve Vue.js]]
	- [[Příklad použití ref k řízení focus ve Vue.js šabloně]]
	- [[Atribut ref jako funkce ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-9