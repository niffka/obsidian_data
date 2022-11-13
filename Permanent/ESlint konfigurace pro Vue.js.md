---
#aliases: [ESlint konfigurace pro Vue.js]
tags: [Honza]
created: 2022-03-28
---

# ESlint konfigurace pro Vue.js
Příklad konfigurace Eslint použitá na Vue.js pro project Epic.

Spuštění pomocí **npm**
```json
"lint": "eslint . --ext .vue,.js,.jsx,.cjs,.mjs --fix --ignore-path .gitignore"
```

Konfigurační soubor v kořenovém adresáři projektu:
```JavaScript
module.exports = {
    "env": {
        "browser": true,
        "es2021": true,
        "node": true
    },
    "extends": [
        "eslint:recommended",
        "plugin:vue/essential",
    ],
    "parserOptions": {
        "ecmaVersion": "latest",
        "sourceType": "module",
    },
    "plugins": [
        "vue",
    ],
    "ignorePatterns": [
        "cypress/**",
    ],
    "rules": {
        "vue/no-multiple-template-root": "off",
    }
}

```

Tato konfigurace se sama načetla a začala používat do VSCode s pluginem [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [ ] Otestovan nastaveni pro WebStrom

# Reference
- **Téma(ta)**: [[ESLint]], [[Vue.js]]
- **Kam dál**: 
	- [[Eslint]]
- **Biblio**:
	1. 