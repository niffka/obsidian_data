---
#aliases: [Použití v-if v elementu template]
tags: [Honza]
created: 2022-03-09
---

# Použití v-if v elementu template
Atribut `v-if` lze použít i v šabloně, toto je užitečná vlastnost protože od verze Vue 3 může šablona mít více než jeden element.

```vue
<template v-if="ok">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
```

_Stejně tak mohou být použity parametry `v-else` a `v-else-if`_

# Reference
- **Téma(ta)**: [[todo_topic]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. 