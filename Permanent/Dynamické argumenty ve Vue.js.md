---
#aliases: [Dynamické argumenty ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Dynamické argumenty ve Vue.js
Pro definici argumentu je možné taky dynamicky měnit jméno argumentu.

Syntakticky se jméno proměnné zapisuje do hranatých závorek:

```vue
<!--
Note that there are some constraints to the argument expression,
as explained in the "Dynamic Argument Expression Constraints" section below.
-->
<a v-bind:[attributeName]="url"> ... </a>

<!-- shorthand -->
<a :[attributeName]="url"> ... </a>
```

V hranatých závorkách může být kromě názvu proměnné také výraz:

```vue
<!-- This will trigger a compiler warning. -->
<a :['foo' + bar]="value"> ... </a>
```

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: git
	- 
- **Biblio**:
	1. https://vuejs.org/guide/essentials/template-syntax.html#dynamic-arguments