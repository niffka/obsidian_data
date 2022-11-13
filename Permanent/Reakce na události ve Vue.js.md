---
#aliases: [Reakce na události ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Reakce na události ve Vue.js
Ve Vue můžeme reagovat na události DOM modelu.

Základní princip je takový, že v rámci scriptu vytvoříme funkci, kterou v šabloně pomoci `v-on:` (zkráceně `@`) napojíme na konkrétní událost.

Vytvoření funkce:
```javascript
import { ref } from 'vue'

const count = ref(0)

function increment() {
  // update component state
  count.value++
}
```

Navěšení na událost:
```vue
<template>
	<button @click="increment">{{ count }}</button>
</template>
```

V rámci hodnoty atributu `@event=`  můžeme také napsat JavaSriptový výraz.

Například `foo`, `foo.bar` a `foo['bar']`, které jsou vyhodnocené jako metody posluchače události.

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Parametry posluchačů událostí ve Vue.js]]
	- [[Inline definice posluchače události ve Vue.js]]
	- [[Modifikátory události ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-4