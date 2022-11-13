---
#aliases: [Caching odvozených property ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Caching odvozených property ve Vue.js
Vue prování caching odvozených property na základě hodnot, ze kerných jsou odvozeny.

To ma dva následky:
1. Vue.js nebude překreslovat elementy dokud to nebude nezbytné.
2. V případě že se mění nereaktivní hodnota, *computed* property zůstane stejná, i když se bude stránka znovu rendrovat: `const now = computed(() => Date.now())`

Vue.js umožňuje vytvořit i zapisovatelné *computed* property. 
Je dobré se tomu ale vyhýbat.

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/computed.html