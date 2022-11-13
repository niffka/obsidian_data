
---
#aliases: [JavaScript expression ve Vue šablonách]
tags: [Honza]
created: 2022-03-08
---

# JavaScript expression ve Vue šablonách
Ve Vue šabloně můžeme použít výrazy v JavaScript jazyce.

```vue
<template>
	{{ number + 1 }}
	
	{{ ok ? 'YES' : 'NO' }}
	
	{{ message.split('').reverse().join('') }}
	
	<div :id="`list-${id}`"></div>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[]]
- **Biblio**:
	1. https://vuejs.org/guide/essentials/template-syntax.html#using-javascript-expressions