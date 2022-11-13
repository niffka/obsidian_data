---
#aliases: [Renderování seznamů ve Vue.js šabloně]
tags: [Honza]
created: 2022-03-09
---

# Renderování seznamů ve Vue.js šabloně
Pro opakované renderování jednoho prvku slouží atribut `v-for`.

```vue
<ul>
  <li v-for="todo in todos" :key="todo.id">
    {{ todo.text }}
  </li>
</ul>
```

- `todo` je lokální proměnná v pro každou iteraci
- `:key` je jednoznačný identifikátor prvků, který Vue využívá pro efektivnější renderování seznamu. Není povinný, ale bez jej Vue.js regeneruje celý seznam při každé změně.

## Modifikace seznamu
Reaktivní seznam vytvoříme pomoc metody `ref()`.

Pokud jej chceme modifikovat můžeme:
1. Použít metody, které jej modifikují: `todos.value.push(newTodo)`
2. Nahradit jej jiným sezname, ale pozor, nesmíme měnit referovanou proměnnou, pouze její obsah uložený v atributu `.value`: `todos.value = todos.value.filter(/* ... */)
`
```vue
<script setup>
import { ref } from 'vue'

// give each todo a unique id
let id = 0

const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo">
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>

```


# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Renderování seznamu s indexem ve Vue.js šabloně]]
	- [[Procházení objektů ve Vue.js šabloně]]
	- [[Použití range ve Vue.js šabloně]]
	- [[Detekce změn v seznamu ve Vue.js šabloně]]
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-7