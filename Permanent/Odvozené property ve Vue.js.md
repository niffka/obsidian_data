---
#aliases: [Computed property ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Odvozené property ve Vue.js
Dalším častým scénářem je, že v rámci šablony potřebuje data upravit než je zobrazíme. Může se jednat například o transformace na seznamu, skládaní více hodnot  dohromady, ...

Nejedná se tedy o data data přímo uložené v komponentě, ale o odvozená (_Computed_) z již uložených hodnot.

~~~ad-warning
title: Pozor na "side effects"

V rámci výpočtu odvozené property by jsme se měli vyhnout  "side effects".
Odvozené komponenty jsou totiž optimalizované pro použití v čablonách.

Pokud potřebuejeme provést výpočet při změně reaktivní proměnné, slou k tomu [[Watch funkce ve Vue.js]].
~~~

Například v komponentě máme uložené dvě čísle reprezentující **x** a **y**, ale v šabloně chceme zobrazit uhel **alfa** a **vzdálenost** od středu souřadného systému.

```vue
<script setup>
import { reactive, computed } from 'vue'
const coor = reactive({
	x: 1,
	y: 2,
});

const polar = computed(() => {
 	return {
    alfa: Math.atan2(coor.y, coor.x) * 180 / Math.PI,
    d: Math.sqrt(coor.x * coor.x + coor.y * coor.y)
  } 
});
</script>

<template>
	<label for="x">X: </label>
	<input id="x" type="number" v-model="coor.x"/>, 
	<label for="y">Y: </label>
	<input if="y" type="number" v-model="coor.y"/>
	<hr>
	<p>
    {{ coor }}  -> {{ polar }}
	</p>
</template>
```
	
~~~ad-info
Compoud propery jsou mocný nástroj, mnohdy je ale přehlednější jej raději nepoužít.
~~~



~~~ad-question
title: Ukol: Seznam úkolů
collapse: true

Máte seznam ukolů, u kterých evidujete, jestli je hotový nebo ne.

```vue
<script setup>
import { ref } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
])

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo" />
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
```

Doimplementujte filter, který bude zobrazovat pouze hotové ukoly.
~~~
~~~ad-check
title: Řešení
collapse: close

```vue
<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo" />
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
```
~~~

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Caching odvozených property ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/guide/essentials/computed.html