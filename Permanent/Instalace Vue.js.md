---
#aliases: [Instalace Vue.js]
tags: [Honza]
created: 2022-03-02
---

# Instalace Vue.js
Vue verze 2 se umožňovalo instalaci několika způsoby
Existují tři hlavní způsoby přidání Vue.js do projektu:

1.  Importujte jej jako balíček CDN
    
```html
<script src="https://unpkg.com/vue@next"></script>
```
    
2.  Nainstalujte jej pomocí npm
    
```shell
> npm init vue@latest

✔ Project name: … <your-project-name>
✔ Add TypeScript? … No / Yes
✔ Add JSX Support? … No / Yes
✔ Add Vue Router for Single Page Application development? … No / Yes
✔ Add Pinia for state management? … No / Yes
✔ Add Vitest for Unit testing? … No / Yes
✔ Add Cypress for both Unit and End-to-End testing? … No / Yes
✔ Add ESLint for code quality? … No / Yes
✔ Add Prettier for code formating? … No / Yes

Scaffolding project in ./<your-project-name>...
Done.

> cd <your-project-name>
> npm install
> npm run dev
```

	
3.  Použijte nástroje [CLI](https://v3.vuejs.org/guide/installation.html#cli) k vytvoření projektu.
    
```shell
npm install -g @vue/cli
vue create <my-project>
```

~~~ad-todo
title: Ukol: Založení projektu

Založte projekt `01_calculator` a spusťě jej.
~~~
~~~ad-check
title: Řešení
collapse: close

V termináluzadejte příkazy:
```bash
> npm init vue@latest
> cd 01_calculator
> npm install
> npm run dev
```
~~~

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Vue.js a nástroj Lite]]
- **Biblio**:
	1. https://vuejs.org/guide/quick-start.html