---
#aliases: [Modifikátory klávesových událostí ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Modifikátory klávesových událostí ve Vue.js
Vue umožňuje v rámci události `keyup` definovat konkrétní klávesy, které událost vyvolají:

```vue
<!-- only call `vm.submit()` when the `key` is `Enter` -->
<input @keyup.enter="submit" />
```

Názvy kláves jsou: `.enter`, `.tab`, `.delete`, `.esc`, `.space`, `.up`, `.down`, `.left`, `.right`, `.ctrl`, `.alt`, `.shift`, `.meta`

Kombinace kláves definujeme následovně:
```vue
<!-- Alt + Enter -->
<input @keyup.alt.enter="clear" />

<!-- Ctrl + Click -->
<div @click.ctrl="doSomething">Do something</div>
```

Speciální modifikátor `.exact` naopak zabrání vyvolání události na klávesu v rámci jiné kombinace:

```vue
<!-- this will fire even if Alt or Shift is also pressed -->
<button @click.ctrl="onClick">A</button>

<!-- this will only fire when Ctrl and no other keys are pressed -->
<button @click.ctrl.exact="onCtrlClick">A</button>

<!-- this will only fire when no system modifiers are pressed -->
<button @click.exact="onClick">A</button>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/event-handling.html#key-modifiers