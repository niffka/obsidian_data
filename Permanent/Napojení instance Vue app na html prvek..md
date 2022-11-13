---
#aliases: [Napojení instance Vue app na html prvek.]
tags: [Honza]
created: 2022-03-04
---

# Napojení instance Vue app na html prvek.
V rámci instance map dále nastavíme prvek na html stránce ke kterému se váže pomocí metody `mount()`.

```html
<div id="app"></div>
```

```js
app.mount('#app')
```

~~~ad-important
Metodu `mount()` je nutné volat vždy jako poslední, až po nastavení konfigurací a assets.
~~~

Metoda mount vrací instanci root komponenty.

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. 