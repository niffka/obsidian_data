---
#aliases: [Atribut ref jako funkce ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Atribut ref jako funkce ve Vue.js
Jako hodnotu `ref` také mlžeme přiřadit funkci, které se zavolá až poté, co jsou komponenty napojené:

```vue
<ChildComponent :ref="(el) => child = el" />
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/api/built-in-special-attributes.html#ref