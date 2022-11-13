---
#aliases: [Inicializace Vue.js aplikace]
tags: [Honza]
created: 2022-03-04
---

# Inicializace Vue.js aplikace
Vue aplikace se inicializuje pomocí metody `createApp(root_component)` z knihovnu _vue_.

```js
import { createApp } from 'vue'

const app = createApp({
  /* root component */
})
```

Klíčovým prvkem je zde definovat  root komponentu.

V rámci jedné stránky není množství instancí Vue app nijak omezeni.
Takto vytvořené instance jsou ale jinak zcela nezávislé.
Tento přístup je doporučován v případě že používáte server-side renderování stránek.

Na instanci Vue app můžeme použít její vlastnost `.config` pro modifikaci jejího chování.
Takto můžeme například:
- [[Konfigurace zpracování chyb ve Vue.js]]
- [[Registrace globálních komponent ve Vue.js]]

Pro další možnosti doporučuji prostudovat [API dokumentaci](https://vuejs.org/api/application.html).

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Napojení instance Vue app na html prvek.]]
	- [[Konfigurace zpracování chyb ve Vue.js]]
- **Biblio**:
	1. https://vuejs.org/guide/essentials/application.html