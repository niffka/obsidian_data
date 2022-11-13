---
#aliases: [Vytváření vlastních komponent ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Vytváření vlastních komponent ve Vue.js
Při vytváření reálné aplikace potřebujeme pracovat s více komponentami.

Komponenty musíme:
1. naimportovat v `setup` metodě
2. Vložit do šablony.

Mějme komponentu **ChildComp.vue**
```vue
<template>
  <h2>A Child Component!</h2>
</template>
```

Tuto komponentu pak použijeme v jiné komponentně následovně:
```vue
<script setup>
import ChildComp from './ChildComp.vue'
</script>

<template>
  <ChildComp />
</template>
```


# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-11