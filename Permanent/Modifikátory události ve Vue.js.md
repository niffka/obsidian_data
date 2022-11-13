---
#aliases: [Modifikátory události ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Modifikátory události ve Vue.js
Při zpracování události DOM se často valíme pro modifikaci dalšího zpracování zachycené události, jedná se například o:
- `event.preventDefault()`
- `event.stopPropagation()` 

To můžeme udělat snadno uvnitř metod, což je ale nepřehledné a naše metody to úzce svazuje s DOM Eventy.

Vue poskytuje modifikátory událostí pro `v-on` a řetězíme je vždy za danou událost pomocí operátoru `.`

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Modifikátory chování událostí ve Vue.js]]
	- [[Modifikátory klávesových událostí ve Vue.js]]
	- [[Modifikátory události myši ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/guide/essentials/event-handling.html#event-modifiers