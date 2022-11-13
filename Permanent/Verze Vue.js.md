---
#aliases: [Verze Vue.js]
tags: [Honza]
created: 2022-03-02
---

# Verze Vue.js
Vue aktuálně podporuje dvě verze [[Vue.js v2]] a [Vue.js v3].

**Od 20 ledna 2022 je verze 3 považována za hlavní**

## Nejváznamější rozdíly
Mezi Vue 2 a 3 existune několik zasadních rozdílů.

### Výcenasobný kořen v templates
Ve vue 2 musel být právě jeden kořenový element v šabloně.
Ve Vue 3 tato povinnost odpadá.

#### Vue 2
```html
<template>
  <div>
    <h1>{{ msg }}</h1>
    <button @click="count++">count is: {{ count }}</button>
    <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
  </div>
</template>
```

#### Vue 3
```html
<template>
  <h1>{{ msg }}</h1>
  <button @click="count++">count is: {{ count }}</button>
  <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
</template>
```

### Composition API
Dalším podstatným zlepšením je možnost rozdělání velkých komponent na části.
- To umožňuje snažíš orientaci kódu
- Zvyšuje znovupoužitelnost již vytvořených částí a jejich použít v různých komponentách

Composed api je definuje v nové sekci `setup`, která nahrazuje předchozí sekce.

```html
<template>
  <!-- your template code -->
</template>
<script>
export default {
  setup() {
    // more code to write
  }
};
</script>
```

V této sekci pak probíhá veškerá konfigurace vue komponenty.


# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[]]
- **Biblio**:
	1. https://javascript.plainenglish.io/differences-between-vue-2-and-vue-3-ee627e2c83a8