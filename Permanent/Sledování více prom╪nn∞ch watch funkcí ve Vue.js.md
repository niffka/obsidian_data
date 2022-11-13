---
#aliases: [Sledování více proměnných watch funkcí ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Sledování více proměnných watch funkcí ve Vue.js
Pokud potřebujeme sledovat více proměnných v jedné `watch` funkci můžeme to udělat následovně:

```javascript
const x = ref(0)
const y = ref(0)

// getter
watch(
  () => x.value + y.value,
  (sum) => {
    console.log(`sum of x + y is: ${sum}`)
  }
)

// array of multiple sources
watch([x, () => y.value], ([newX, newY]) => {
  console.log(`x is ${newX} and y is ${newY}`)
})
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/watchers.html#watch-source-types