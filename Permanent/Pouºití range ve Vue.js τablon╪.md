---
#aliases: [Použití range ve Vue.js šabloně]
tags: [Honza]
created: 2022-03-09
---

# Použití range ve Vue.js šabloně
`v-for` může mít také jako vstup celé číslo. 
V tomto případě bude šablona prvek vygenerován na základě rozsahu 1...n.

```vue
<span v-for="n in 10">{{ n }}</span>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/list.html#v-for-with-a-range