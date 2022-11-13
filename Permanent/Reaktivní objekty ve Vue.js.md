---
#aliases: [Reaktivní objekty ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Reaktivní objekty ve Vue.js
Aby Vue monitorovalo změny na objektu v JS, musí o něm Vue vědět.

Pro deklaraci monitorovaných objektů, ale i polí, `Set`, `Map` a pod.,  používáme funkci `reactive()`, který předaný objekt obaluje [[Proxy objekt]].

```JavaScript
import { reactive } from 'vue'

const counter = reactive({
  count: 1
})

console.log(counter.count) // 0
counter.count++
```

V šabloně pak s tímto objektem pracujeme:
```vue
<template>
  <p>Count is: {{ counter.count }}</p>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Reaktivní proměnné ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-2