---
#aliases: [Modifikátory chování událostí ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Modifikátory chování událostí ve Vue.js
A jedná se o následující modifikátory:

```vue
<!-- the click event's propagation will be stopped -->
<a @click.stop="doThis"></a>

<!-- the submit event will no longer reload the page -->
<form @submit.prevent="onSubmit"></form>

<!-- modifiers can be chained -->
<a @click.stop.prevent="doThat"></a>

<!-- just the modifier -->
<form @submit.prevent></form>

<!-- only trigger handler if event.target is the element itself -->
<!-- i.e. not from a child element -->
<div @click.self="doThat">...</div>
```

~~~ad-tip
Při použití modifikátorů záleží na pořadí, protože příslušný kód je generován ve stejném pořadí. 
Proto použití `@click.prevent.self` zabrání všem kliknutím, zatímco `@click.self.prevent` zabrání pouze kliknutí na samotný prvek.
~~~

```vue
<!-- use capture mode when adding the event listener -->
<!-- i.e. an event targeting an inner element is handled here before being handled by that element -->
<div @click.capture="doThis">...</div>

<!-- the click event will be triggered at most once -->
<a @click.once="doThis"></a>

<!-- the scroll event's default behavior (scrolling) will happen -->
<!-- immediately, instead of waiting for `onScroll` to complete  -->
<!-- in case it contains `event.preventDefault()`                -->
<div @scroll.passive="onScroll">...</div>
```

~~~ad-tip
Nepoužívejte společně `.passive` a ``.prevent`, protože `.passive` již prohlížeči naznačuje, že nehodláte bránit výchozímu chování události, a pokud tak učiníte, pravděpodobně se vám zobrazí varování z prohlížeče.
~~~


# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/event-handling.html#event-modifiers