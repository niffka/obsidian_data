---
#aliases: [Sledování atributů objektů funkcí watch ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Sledování atributů objektů funkcí watch ve Vue.js
V případě potřeby sledování atributu objektu, můsíme v funkci `watch`
 opět použít arrow funkci:

```javascript
watch(
  () => obj.count,
  (count) => {
    console.log(`count is: ${count}`)
  }
)
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/watchers.html#watch-source-types