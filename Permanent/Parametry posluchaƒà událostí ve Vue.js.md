---
#aliases: [Parametry posluchačů událostí ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Parametry posluchačů událostí ve Vue.js
Funkce zaregistrovaná jako posluchač události může mít parametry. 

Základem je parametr `event` do které se předává **DOM Event**, který událost aktivoval.

```javascript
const name = ref('Vue.js')

function greet(event) {
  alert(`Hello ${name.value}!`)
  // `event` is the native DOM event
  if (event) {
    alert(event.target.tagName)
  }
}
```

Pro doplnění ještě template:
```vue
<template>
	<!-- `greet` is the name of the method defined above -->
	<button @click="greet">Greet</button>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/event-handling.html#method-handlers