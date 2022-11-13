---
#aliases: [Reaktivní proměnné ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Reaktivní proměnné ve Vue.js
Pokud potřebujeme sledovat pouze proměnnou, nikoliv objekt musíme použít jinou funkce než u [[Reaktivní objekty ve Vue.js]]: `ref()`.

```JavaScript
import { ref } from 'vue'

const message = ref('Hello World!')

console.log(message.value) // "Hello World!"
message.value = 'Changed'
```

V šabloně pak již s proměnnou pracujeme normálně, aniž bychom použili operátor `.`

```vue
<h1>{{ message }}</h1>
```



# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[JavaScript expression ve Vue šablonách]]
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-2