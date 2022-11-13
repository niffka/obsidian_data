---
#aliases: [Přístup k objektu Event v rámci inline metody ve Vuje.js]
tags: [Honza]
created: 2022-03-08
---

# Přístup k objektu Event v rámci inline metody ve Vuje.js
Někdy také potřebujeme přistupovat k původní události DOM v obslužné inline rutině. 
Můžete jej předat do metody pomocí speciální proměnné `$event` nebo použít funkci `=>`:

```vue
<script setup>
function warn(message, event) {
  // `now we have access to the native event`
  if (event) {
    event.preventDefault()
  }
  alert(message)
}
</script>

<template>
	<!-- using $event special variable -->
	<button @click="warn('Form cannot be submitted yet.', $event)">
	  Submit
	</button>
	
	<!-- using inline arrow function -->
	<button @click="(event) => warn('Form cannot be submitted yet.', event)">
	  Submit
	</button>
</template>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/event-handling.html#accessing-event-argument-in-inline-handlers