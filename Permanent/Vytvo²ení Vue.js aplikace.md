---
#aliases: [Struktury Vue.js aplikace]
tags: [Honza]
created: 2022-03-02
---

# Vytvoření Vue.js aplikace
_Navazuje se na příklad z [[Instalace Vue.js]]_

**Index.html** je hlavní (a jediná stránka), kterou prohlížeč stahuje.
Plní dvě funkce:
1. Slouží k stažení a spuštění scriptu, který nastartuje Vue aplikaci
2. Můžeme zde ošetřit případ, kdy je klient nekompatibilní s naší aplikaci.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" href="/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite App</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/src/main.js"></script>
  </body>
</html>
```

Dalším krojem je pak zpracování scriptu [[Inicializace Vue.js aplikace|main.js]].
# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Inicializace Vue.js aplikace]]
- **Biblio**: