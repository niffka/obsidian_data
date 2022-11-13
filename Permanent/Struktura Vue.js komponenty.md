---
aliases: [Vue Single File Component]
tags: [Honza]
created: 2022-03-07
---

# Struktura Vue.js komponenty
Komponenty můžeme vytvářet více způsoby, například je celé nadefinovat v Javascriptu.
Vue.js ale umožňuje vytvářet speciální typ souboru, které obsahují vždy jednu komponentu: alias **SFC**: _Vue Single File Component_.

Každý takový soubor se pak skládá ze tří části:
- kódu v JS a nebo TS
- šablony v _HTML_
- a stylu, například v _CSS_

 ```vue
<script setup>

</script>

<template>
  <h1>Hello Vue!</h1>
  <p>
    Lorem ipsum ....
  </p>
</template>

<style>
h1 {
	color:green
}
</style>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Syntaxe šablony ve Vue.js]]
- **Biblio**:
	1. https://www.techiediaries.com/vue-3-tutorial/