# VUEJS1
Vue.js je progresivní JavaScript open source framework, který oproti svým konkurentům vyniká rychlostí a jednoduchostí. 

V rámci kurzu se mimo samotného framework naučíte pomocí Material Design vytvořit moderní SPA aplikaci, optimalizovanou nejen pro desktop i mobilní zařízení. 

Seznámíte se také se základy služby Firebase v roli backed serveru pro napojení webových aplikací, což Vám v provozu pomůže ušetřit čas a peníze. 

## Základní informace
- [[Co je Vue.js]]
	- [[MVVM návrhový vzoru]]
	- [[Reaktivní aplikace]]
- [[Instalace Vue.js]]
- [[Verze Vue.js]]
- [[Nástroje pro vývoj Vue.js]]

## Začínáme
- [[Vytvoření Vue.js aplikace]]
- [[Základy práce s komponentami ve Vue.js]]
- [[Struktura Vue.js komponenty]]
 
## Práce s šablonami
- [[Syntaxe šablony ve Vue.js]]
- [[Deklarativní vykreslování ve Vue.js šabloně]]
- [[Práce s atributy ve Vue.js šabloně]]
- [[Zpracování vstupu uživatele]]
- [[Reakce na události ve Vue.js]]
- [[Zpracování html formulářů ve Vue.js]]
- [[Podmíněné renderování ve Vue.js šabloně]]
- [[Renderování seznamů ve Vue.js šabloně]]

## Možnosti setup metody
- [[Odvozené property ve Vue.js]]
- [[Reference na elementy šablony ve Vue.js]]
- [[Watch funkce ve Vue.js]]

## Komponenty
- [[Vytváření vlastních komponent ve Vue.js]]
- [[Definice property v komponentě ve Vue.js]]
- [[Zasíláni zpráv mezi komponentami ve Vue.js ]]
- [[Skládání komponent pomocí slotů ve Vue.js]]

    - Vkládání HTML kódu
    - 
3. **Instance aplikací a komponent**

4. **Syntaxe šablony**
    - [[Interpolace]]
5. **Vlastnosti a metody dat**
    - [[Vlastnosti]]
    - [[Metody]]

7. **Pokročilá témata**
    - [[Routing]]
    - [[Pinia – state management]]
8. **Pomocné knihovny**
    - [[Vue .js a nástroje Lite]]
    - [[Vue Router]]
    - [[Vue DevTools]]
    - [[Vuetify]]
    - [[Distribuce]]
## Co je Vue.js
Vue je třetí nejrozšířenější framework na tvorbu [[SPA Aplikace|SPA aplikací]][^stackoverflow_trends].
Jeho konkurenty jsou například [[Angular]] od Google nebo [[React]] od Facebook.
Na rozdíl od jeho konkurentů za ním nestojí žádná velká spolčenost, ale rostoucí opensource komunita.
Zdrojové kódy je možné získat přímo z https://github.com/vuejs.

Nejedná se o monolitický framework ale skládá se ze skupiny knihoven.
Programátor si tedy může snadno celý framework "poskládat" podle vlastních potřeb.

Seznam oficiálně podporovaných komponent/knihoven je zde: https://github.com/vuejs/awesome-vue#components--libraries.

## Hlavní výhody
- **Snadno naučitelný**: Už znáte HTML, CSS a JavaScript? Přečtěte si průvodce a začněte stavět věci během okamžiku!
- **Univerzální**: Postupně přizpůsobitelný ekosystém, který se pohybuje mezi knihovnou a plnohodnotným rámcem.
- **Výkonný**: 20 kB min + doba běhu gzip, bleskově rychlý virtuální DOM, minimální optimalizační úsilí

Vue je postaveno na [[MVVM návrhový vzoru]], a principu [[Reaktivní aplikace]].
## MVVM návrhový vzoru
Díky tomu že JavaScript začal podporovat asynchronní programování a asynchronní požadavky, odpadla nutnost vytvářet nový request pro změnu na zobrazované stránce.

Díky tomu vylo možné začít vytvářet i MVVM frameworky.
Odpadá nutnost implementace [[MVC návrhový vzor#Controller|Controlleru]] a místo toho se vytváří Data-binding.
## Reaktivní aplikace
Základní principy jsou:
- Observer sleduje stav aplikace
- Rozesílání změn pomocí notifikací v rámci aplikace
- Render automaticky reaguje na změny
- Poskytují instantní feedback pro uživatelé akce.
## Instalace Vue.js
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
## Verze Vue.js
Vue aktuálně podporuje dvě verze [[Vue.js v2]] a [Vue.js v3].

**Od 20 ledna 2022 je verze 3 považována za hlavní**

## Nejváznamější rozdíly
Mezi Vue 2 a 3 existune několik zasadních rozdílů.

### Výcenasobný kořen v templates
Ve vue 2 musel být právě jeden kořenový element v šabloně.
Ve Vue 3 tato povinnost odpadá.

#### Vue 2
```html
<template>
  <div>
    <h1>{{ msg }}</h1>
    <button @click="count++">count is: {{ count }}</button>
    <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
  </div>
</template>
```

#### Vue 3
```html
<template>
  <h1>{{ msg }}</h1>
  <button @click="count++">count is: {{ count }}</button>
  <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
</template>
```

### Composition API
Dalším podstatným zlepšením je možnost rozdělání velkých komponent na části.
- To umožňuje snažíš orientaci kódu
- Zvyšuje znovupoužitelnost již vytvořených částí a jejich použít v různých komponentách

Composed api je definuje v nové sekci `setup`, která nahrazuje předchozí sekce.

```html
<template>
  <!-- your template code -->
</template>
<script>
export default {
  setup() {
    // more code to write
  }
};
</script>
```

V této sekci pak probíhá veškerá konfigurace vue komponenty.

## Nástroje pro vývoj Vue.js

Pro vývoj Vue je nejdůležitější mít nainstalovaný [Node.JS + NPM](https://nodejs.org/en/)

## Vývojová prostředí
* [Visual Studio Code](https://code.visualstudio.com/), s následujícími pluginy:
	* [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)
	* [Vue VSCode Snippets](https://marketplace.visualstudio.com/items?itemName=sdras.vue-vscode-snippets)
* [WebStorm](https://www.jetbrains.com/webstorm/)

## Plugin do prohlížeče
Pro vývoj následně potřebuje plugin do prohlížeče:
- Chrome: [Vue.js devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
- Firefox: [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)

## Testování a experimenty
Pro testování a experimenty existuje i několik online nástrojů:
- https://sfc.vuejs.org/
-
## Vytvoření Vue.js aplikace
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

Dalším krojem je pak zpracování scriptu [[Inicializace Vue.js aplikace|main.js]].### Inicializace Vue.js aplikace
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
#### Napojení instance Vue app na html prvek.
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
#### Konfigurace zpracování chyb ve Vue.js
Příklad konfigurace funkce na zpracování chyb:

```js
app.config.errorHandler = (err) => {
  /* handle error */
}
```

## Základy práce s komponentami ve Vue.js
Komponenty rozdělují uživatelské rozhraní na nezávislé a opakovaně použitelné části.
Umožňují každou část vyvíjet a testovat samostatně.

Aplikace je organizována do stromu vnořených komponent:
![Strom komponent](components.7fbb3771.png)

Je to velmi podobné tomu, jak vkládáme prvky HTML.

Vue.js komponenty umožňují zapouzdřit obsah a logiku do uzavřeného celku.
## Struktura Vue.js komponenty
Komponenty můžeme vytvářet více způsoby, například je celé nadefinovat v Javascriptu.
Vue.js ale umožňuje vytvářet speciální typ souboru, které obsahují vždy jednu komponentu: alias **SFC**: _Vue Single File Component_.

Každý takový soubor se pak skládá ze tří části:
- kódu v JS a nebo TS
- šablony v _HTML_
- a stylu, například v _CSS_

 ```vue
<script setup>

</script>

<template>
  <h1>Hello Vue!</h1>
  <p>
    Lorem ipsum ....
  </p>
</template>

<style>
h1 {
	color:green
}
</style>
```
## Syntaxe šablony ve Vue.js
Vue používá syntaxi šablony založenou na HTML.
Kromě HTML tagů je možné do šablony vkládat vlastní komponenty.

Všechny šablony Vue jsou syntakticky platné HTML, které mohou být analyzovány prohlížeči a analyzátory HTML vyhovujícími specifikacím.

Mnoho knihoven pro Vue.js přání vlastní předdefinované komponenty, které pak používáme místo HTML značek v této šabloně.
Jedná se například o:
- [BootstrapVue](https://www.npmjs.com/package/bootstrap-vue-3)
- [Vuetify](https://next.vuetifyjs.com/en/)
- [PrimeVue](https://www.primefaces.org/primevue/#/)
## Deklarativní vykreslování ve Vue.js šabloně
V rámci Vue.js template používá "Mustache" syntaxi pro vkládání hodnot do html.

```vue
<template>
<span>Message: {{ msg }}</span>
</template>
```

Díky **Deklartivnímu vykreslování** Vue monitoruje stav proměnných a překresluje šablonu v případě jejich změny.
### Reaktivní objekty ve Vue.js
Aby Vue monitorovalo změny na objektu v JS, musí o něm Vue vědět.

Pro deklaraci monitorovaných objektů, ale i polí, `Set`, `Map` a pod.,  používáme funkci `reactive()`, který předaný objekt obaluje [[Proxy objekt]].

```JavaScript
import { reactive } from 'vue'

const counter = reactive({
  count: 1
})

console.log(counter.count) // 0
counter.count++
```

V šabloně pak s tímto objektem pracujeme:
```vue
<template>
  <p>Count is: {{ counter.count }}</p>
</template>
```
### Reaktivní proměnné ve Vue.js
Pokud potřebujeme sledovat pouze proměnnou, nikoliv objekt musíme použít jinou funkce než u [[Reaktivní objekty ve Vue.js]]: `ref()`.

```JavaScript
import { ref } from 'vue'

const message = ref('Hello World!')

console.log(message.value) // "Hello World!"
message.value = 'Changed'
```

V šabloně pak již s proměnnou pracujeme normálně, aniž bychom použili operátor `.`

```vue
<h1>{{ message }}</h1>
```


#### JavaScript expression ve Vue šablonách
Ve Vue šabloně můžeme použít výrazy v JavaScript jazyce.

```vue
<template>
	{{ number + 1 }}
	
	{{ ok ? 'YES' : 'NO' }}
	
	{{ message.split('').reverse().join('') }}
	
	<div :id="`list-${id}`"></div>
</template>
```
## Práce s atributy ve Vue.js šabloně
Proměnné můžeme také provázat s hodnotami atributů HTML tagů.
K tomu slouží direktiva `v-bind`.

```vue
<script setup>
import { ref } from 'vue'

const titleClass = ref('green')
</script>

<template>
	<div v-bind:class="titleClass">Text</div>
</template>

<style>
.green {
  color: green;
}
.red {
  color: red;
}
</style>
```

Stejně jako události i `v-bind` je natolik často používaný, ze se zkracuje na `:`.
### Boolean atributy ve Vue.js
Některé atributy ve HTML nabývají hodnotu **true/false** identifikovanou pouze jejich přítomností.

Příkladem takového atribut je `disabled`.

Vue zpracuje takový atribut pouze v případě, kdy přiřazná promenná nabývá hodnoty `true`

```vue
<script setup>
import { ref } from 'vue'

const isButtonDisabled = ref(true)
</script>

<template>
 <button :disabled="isButtonDisabled">Button</button>
</template>
```
### Hromadné mapování atributů ve Vue.js
Vue umožňuje rovněž namapovat více atributů hromadně pomocí jednoho objektu:

```vue
<script setup>
import { reactive } from 'vue'

const objectOfAttrs = reactive({
  id: 'container',
  class: 'wrapper'
})
</script>

<template>
  <div v-bind="objectOfAttrs">Text</div>
</template>

<style>
  #container {
    background: green
  }
  .wrapper {
    color: red
  }
</style>
```
## Zpracování vstupu uživatele
V rámci zpracování vstupu od uživatele se jedná o:

1. [[Reakce na události ve Vue.js]]
2. [[Zpracování html formulářů ve Vue.js]]
## Reakce na události ve Vue.js
Ve Vue můžeme reagovat na události DOM modelu.

Základní princip je takový, že v rámci scriptu vytvoříme funkci, kterou v šabloně pomoci `v-on:` (zkráceně `@`) napojíme na konkrétní událost.

Vytvoření funkce:
```javascript
import { ref } from 'vue'

const count = ref(0)

function increment() {
  // update component state
  count.value++
}
```

Navěšení na událost:
```vue
<template>
	<button @click="increment">{{ count }}</button>
</template>
```

V rámci hodnoty atributu `@event=`  můžeme také napsat JavaSriptový výraz.

Například `foo`, `foo.bar` a `foo['bar']`, které jsou vyhodnocené jako metody posluchače události.
### Parametry posluchačů událostí ve Vue.js
Funkce zaregistrovaná jako posluchač události může mít parametry. 

Základem je parametr `event` do které se předává **DOM Event**, který událost aktivoval.

```javascript
const name = ref('Vue.js')

function greet(event) {
  alert(`Hello ${name.value}!`)
  // `event` is the native DOM event
  if (event) {
    alert(event.target.tagName)
  }
}
```

Pro doplnění ještě template:
```vue
<template>
	<!-- `greet` is the name of the method defined above -->
	<button @click="greet">Greet</button>
</template>
```
### Inline definice posluchače události ve Vue.js
Pokud do hodnoty atributu `@event=`  napišme příkaz v jazyce JavaScript, pak je tento příkaz vyhodnocen jako _inline handler_.

```vue
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <button @click="count++">count is: {{ count }}</button>
</template>
```
#### Volání method v rámci inline posluchače události ve Vue.js
Namísto přímé vazby na název metody u `@event=` atributu, můžeme také dodefinovat volání metody.

To nám umožňuje předat vlastní argumenty metody namísto nativní události:

```vue
<script setup>
	function say(message) {
	  alert(message)
	}
</script>

<template>
	<button @click="say('hello')">Say hello</button>
	<button @click="say('bye')">Say bye</button>
</template>
```
#### Přístup k objektu Event v rámci inline metody ve Vue.js
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
#### Dynamické argumenty ve Vue.js
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
### Modifikátory události ve Vue.js
Při zpracování události DOM se často valíme pro modifikaci dalšího zpracování zachycené události, jedná se například o:
- `event.preventDefault()`
- `event.stopPropagation()` 

To můžeme udělat snadno uvnitř metod, což je ale nepřehledné a naše metody to úzce svazuje s DOM Eventy.

Vue poskytuje modifikátory událostí pro `v-on` a řetězíme je vždy za danou událost pomocí operátoru `.`
#### Modifikátory chování událostí ve Vue.js
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

#### Modifikátory klávesových událostí ve Vue.js
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
#### Modifikátory události myši ve Vue.js
Pokud potřebujeme reagovat jen na určité tlačítko myši, můžeme použít modifikátory `.left`,  `.right` a nebo `.middle`.
## Zpracování html formulářů ve Vue.js
#aliases: [Zpracování html formulářů ve Vue.js]
tags: [Honza]
created: 2022-03-08
---

# Zpracování html formulářů ve Vue.js
Vue poskytuje řadu nástrojů a mechanizmů pro zpracováni HTML formulářů.

V podstatě se jedná o obousměrnou vazbu mezi tagem `input` a proměnou. 
- Pro směr z **html -> js** používáme `v-on`/`@`
- Pro směr **js -> html** pak `v-bind`/`:`

```vue
<script setup>
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <input :value="text" @input="text = $event.target.value">
  <p>{{ text }}</p>
</template>
```

~~~ad-info
collapse: true

Můžete rovněž použít 

**1. Arrow funkci**
```vue
  <input :value="text" @input="(event) => text = $event.target.value">
```

**2. obyčejnou funkci** 
```vue
function onInput(e) {
  // a v-on handler receives the native DOM event
  // as the argument.
  text.value = e.target.value
}
```

```vue
<input :value="text" @input="onInput">
```
~~~

Tuto obousměrnou smyčku můžeme zjednodušit pomocí atributu `v-model`:

```vue
<script setup>
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <input v-model="text">
  <p>{{ text }}</p>
</template>
```

`v-model` je kromě `<input>` možné použít na další typy tagů:
- `<textarea>` se mapuje stejně jako `<input>` na atributy `value` a `input`,
- `<input type="checkbox">` a `<input type="radio">` se mapuje na `checked` vlastnost a `change` událost,
-   `<select>` element se mapuje na `value` vlastnost a událost `change` .``

# Reference 
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- [[Mapování formulářového prvku textarea ve Vue.js]]
	- [[Mapování formulářového prvku checkbox ve Vue.js]]
	- [[Mapování formulářového prvku radio ve Vue.js]]
	- [[Mapování formulářového prvku select ve Vue.js]]
	- [[Povázávání hodnot formulářových prvků ve Vue.js]]
	- [[Modifikátory v-model atributu]]
- **Biblio**:
	1. https://vuejs.org/tutorial/#step-5### Mapování formulářového prvku textarea ve Vue.js

Příklad elementu `<textarea>`

```vue
<script setup>
import { ref } from 'vue'

const text = ref('')
</script>

<template>
	<span>Multiline message is:</span>
	<p style="white-space: pre-line;">{{ text }}</p>
	<textarea v-model="text"></textarea>
</template>
```

### Mapování formulářového prvku checkbox ve Vue.js
Mapování elementu `<input type="checkbox"`

```vue
<script setup>
import { ref } from 'vue'

const checked = ref(false)
</script>

<template>
  <input type="checkbox" id="checkbox" v-model="checked" />
  <label for="checkbox">{{ checked }}</label>
</template>
```

Další užitečnou možností je propojení několika checkboxů s polem

```vue
<script setup>
import { ref } from 'vue'

const checkedNames = ref([])
</script>

<template>
  <div>Checked names: {{ checkedNames }}</div>
	<hr/>
  <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
  <label for="jack">Jack</label>

  <input type="checkbox" id="john" value="John" v-model="checkedNames">
  <label for="john">John</label>

  <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
  <label for="mike">Mike</label>
</template>
```### Mapování formulářového prvku radio ve Vue.js
Tento element je rovněž velmi snadný na použití:

```vue
<script setup>
import { ref } from 'vue'

const picked = ref(null)
</script>

<template>
  <div>Picked: {{ picked }}</div>
  <hr/>
  <input type="radio" id="one" value="One" v-model="picked" />
  <label for="one">One</label>

  <input type="radio" id="two" value="Two" v-model="picked" />
  <label for="two">Two</label>
</template>
```
### Mapování formulářového prvku select ve Vue.js
Zde můžeme použít dvě varianty:

1. Jednoduchý select

```vue
<script setup>
import { ref } from 'vue'

const selected = ref(null)
</script>

<template>
  <div>Selected: {{ selected }}</div>
	<hr/>
  <select v-model="selected">
    <option disabled value="">Please select one</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
</template>
```

2. Vícenásobný select

```vue
<script setup>
import { ref } from 'vue'

const selected = ref(null)
</script>

<template>
	<div>Selected: {{ selected }}</div>
	<hr/>
	<select v-model="selected" multiple>
	  <option>A</option>
	  <option>B</option>
	  <option>C</option>
	</select>
</template>
```

3. Select z definovaný nabídkou v JS pomocí `v-for` atributu
```vue
<script setup>
import { ref } from 'vue'

const selected = ref('A')

const options = ref([
  { text: 'One', value: 'A' },
  { text: 'Two', value: 'B' },
  { text: 'Three', value: 'C' }
])
</script>

<template>
	<div>Selected: {{ selected }}</div>
	<hr/>
	<select v-model="selected">
		<option v-for="option in options" :value="option.value">
	    {{ option.text }}
	    </option>
	</select>
</template>
```
### Povázávání hodnot formulářových prvků ve Vue.js
Hodnoty které nabývají formulářové prvky, nebo které potřebujeme aby nabývali jsou často jiné od těch, které zobrazuje ve formláři. 

Vue umožňuje díky _Value Bindings_ atributů s tím to dále pracovat.

Detaily nastudujte přímo z Vue guilde: https://vuejs.org/guide/essentials/forms.html#value-bindings
### Modifikátory v-model atributu
Atribut `v-model` má také definováno několik modifikátorů:

- `.lazy`: Vue modifikuje prvek při každé změně, takto mu v tom zabráníme
- `.number`: prování automatické přetypování textu na číslo. 
	Tento modifikátor je aplikován automaticky, pokud je `<input type="number" >`
- `.trim`: Automaticky odstraňuje bílé znaky okolo vstupu uživatele.
## Podmíněné renderování ve Vue.js šabloně
Pomocí atributu `v-if` můžeme definovat podmínku, při jejímž splnění se prvek bude renderovat.  

Stejně jak jsme zvyklí, můžeme používat i další atributy: `v-else` a také `v-else-if`.

```vue
<script setup>
import { ref } from 'vue'

const awesome = ref(true)

function toggle() {
  awesome.value = !awesome.value
}
</script>

<template>
  <button @click="toggle">toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
</template>
```
### Použití v-if v elementu template
Atribut `v-if` lze použít i v šabloně, toto je užitečná vlastnost protože od verze Vue 3 může šablona mít více než jeden element.

```vue
<template v-if="ok">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
```

_Stejně tak mohou být použity parametry `v-else` a `v-else-if`_
### Atributy v-show v template
Atribut `v-show` zobrazuje element pomocí parametru `display` ve stylech.

Na rozdíl od `v-if` je tedy takovýto element stále součástí DOM.

Výhoda `v-show` je v tom, že je mnohem efektivnější než, nemodifikuje DOM model pouze upravuje styl. 
Z toho důvodu je tedy dobré o něm uvažovat jako o prvním variantě.
## Renderování seznamů ve Vue.js šabloně
Pro opakované renderování jednoho prvku slouží atribut `v-for`.

```vue
<ul>
  <li v-for="todo in todos" :key="todo.id">
    {{ todo.text }}
  </li>
</ul>
```

- `todo` je lokální proměnná v pro každou iteraci
- `:key` je jednoznačný identifikátor prvků, který Vue využívá pro efektivnější renderování seznamu. Není povinný, ale bez jej Vue.js regeneruje celý seznam při každé změně.

## Modifikace seznamu
Reaktivní seznam vytvoříme pomoc metody `ref()`.

Pokud jej chceme modifikovat můžeme:
1. Použít metody, které jej modifikují: `todos.value.push(newTodo)`
2. Nahradit jej jiným sezname, ale pozor, nesmíme měnit referovanou proměnnou, pouze její obsah uložený v atributu `.value`: `todos.value = todos.value.filter(/* ... */)
`
```vue
<script setup>
import { ref } from 'vue'

// give each todo a unique id
let id = 0

const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo">
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>

```

### Renderování seznamu s indexem ve Vue.js šabloně
Pokud při procházení seznamu chceme znát i pořadí prvku, můžeme použit: `v-for="(item, index) in items"`.

```vue
<script setup>
import { ref } from 'vue'
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
</script>

<template>
  <ul>
    <li v-for="(item, index) in items">
      {{ index }} - {{ item.message }}
    </li>
  </ul>
</template>
```
### Procházení objektů ve Vue.js šabloně
Atribut `v-for` nemusí iterovat jen přes seznamy, může procházet i objekty:

```vue
<script setup>
  import { reactive } from 'vue'
const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})
</script>

<template>
  <ul>
    <li v-for="(value, key) in myObject">
      {{ key }}: {{ value }}
    </li>
  </ul>
</template>
```
### Použití range ve Vue.js šabloně
`v-for` může mít také jako vstup celé číslo. 
V tomto případě bude šablona prvek vygenerován na základě rozsahu 1...n.

```vue
<span v-for="n in 10">{{ n }}</span>
```
### Detekce změn v seznamu ve Vue.js šabloně
Seznam metod pro mutaci pole, které aktivují přegenerování šablony
-   `push()`
-   `pop()`
-   `shift()`
-   `unshift()`
-   `splice()`
-   `sort()`
-   `reverse()`

## Odvozené property ve Vue.js
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
### Caching odvozených property ve Vue.js
Vue prování caching odvozených property na základě hodnot, ze kerných jsou odvozeny.

To ma dva následky:
1. Vue.js nebude překreslovat elementy dokud to nebude nezbytné.
2. V případě že se mění nereaktivní hodnota, *computed* property zůstane stejná, i když se bude stránka znovu rendrovat: `const now = computed(() => Date.now())`

Vue.js umožňuje vytvořit i zapisovatelné *computed* property. 
Je dobré se tomu ale vyhýbat.
## Reference na elementy šablony ve Vue.js
Pomocí atributu `ref` můžeme přistupovat k elementu šablony přímo, jako bychom si jej vytáhli například pomocí knihovny jQuery.

Základní použití je následující:
```vue
<script setup>
import { ref } from 'vue'

const p = ref(null)
</script>

<template>
  <p ref="p">hello</p>
</template>
```

Jak je vidět proměnná `p` je inicializovaná na hodnotu `null`. 
Pokud chceme provádět s elementy operace v kódu, musíme to udělat až po té, co Vue komponentu připojí. 

K to tomu účelu slouží metoda `onMounted`
```vue
<script setup>
import { ref, onMounted } from 'vue'

const p = ref(null)

onMounted(() => {
  p.value.textContent = 'mounted!'
})
</script>

<template>
  <p ref="p">hello</p>
</template>
```

### Životní cyklus komponent ve Vue.js
Následující digram zachycuje životní cyklu komponenty:

![[lifecycle.16e4c08e.png]]
## Seznam callback metohod životního cyklu 
K životnímu cyklu se Váži následující metody:

### onMounted()
Registruje zpětné volání, které se má zavolat po připojení komponenty.

```js
function onMounted(callback: () => void): void
```

### onUpdated()
Registruje zpětné volání, které má být voláno poté, co komponenta aktualizovala svůj strom DOM kvůli změně reaktivního stavu.

```javascript
function onUpdated(callback: () => void): void
```

### onUnmounted()
Registruje zpětné volání, které se má zavolat po odpojení komponenty.

```javascript
function onUnmounted(callback: () => void): void
```

### onBeforeMount()
Registruje zpětné volání, které je voláno těsně před montáží komponenty.

```javascript
function onBeforeMount(callback: () => void): void
```

### onBeforeUpdate()
Registruje zpětné volání, které se má být zavolat těsně předtím, než se komponenta chystá aktualizovat svůj strom DOM kvůli reaktivní změně stavu.

```javascript
function onBeforeUpdate(callback: () => void): void
```

### onBeforeUnmount()
Registruje zpětné volání, které se má být voláno těsně před odpojením instance komponenty.

```javascript
function onBeforeUnmount(callback: () => void): void
```

### onErrorCaptured()

Registruje zpětné volání, které se má zavolat, když byla zachycena chyba šířící se z podřízené komponenty.

```typescript
function onErrorCaptured(callback: ErrorCapturedHook): void

type ErrorCapturedHook = (
  err: unknown,
  instance: ComponentPublicInstance | null,
  info: string
) => boolean | void
```
### Příklad použití ref k řízení focus ve Vue.js šabloně
Následující příklad ukazuje scénář, kdy chceme na stavit fokus na určitý prvek na stránce

```vue
<script setup>
import { ref, onMounted } from 'vue'

// declare a ref to hold the element reference
// the name must match template ref value
const input = ref(null)

onMounted(() => {
  input.value.focus()
})
</script>

<template>
  <input ref="input" />
</template>
```
### Atribut ref jako funkce ve Vue.js
Jako hodnotu `ref` také mlžeme přiřadit funkci, které se zavolá až poté, co jsou komponenty napojené:

```vue
<ChildComponent :ref="(el) => child = el" />
```
## Watch funkce ve Vue.js
Watchers slouží k provádění výpočtu závislém na změně stavu reaktivních proměnných.

Prvním parametrem funkce je reaktivní proměnná, kterou watcher sleduje.

V nejjednodušším případě pak může taková funkce vypadat následovně:

```javascript
const x = ref(0)

watch(x, (newX) => {
  console.log(`x is ${newX}`)
})
```

~~~ad-todo
title: Ukol: Stahování ukolů z api
collapse: close

Vytvořte `watch` funkci, která stáhne nový ukol pokaždé, když se změní `todoId`.

```vue
<script setup>
import { ref } from 'vue'

const todoId = ref(1)
const todoData = ref(null)

async function fetchData() {
  todoData.value = null
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  todoData.value = await res.json()
}

fetchData()
</script>

<template>
  <p>Todo id: {{ todoId }}</p>
  <button @click="todoId++">Fetch next todo</button>
  <p v-if="!todoData">Loading...</p>
  <pre v-else>{{ todoData }}</pre>
</template>
```
~~~

~~~ad-check
title: Řesení
collapse: close


```javascript
// Update imports
import { ref, watch } from 'vue'

// add watch to last line of setup
watch(todoId, fetchData)
```
~~~
### Sledování více proměnných watch funkcí ve Vue.js
Pokud potřebujeme sledovat více proměnných v jedné `watch` funkci můžeme to udělat následovně:

```javascript
const x = ref(0)
const y = ref(0)

// getter
watch(
  () => x.value + y.value,
  (sum) => {
    console.log(`sum of x + y is: ${sum}`)
  }
)

// array of multiple sources
watch([x, () => y.value], ([newX, newY]) => {
  console.log(`x is ${newX} and y is ${newY}`)
})
```
### Sledování atributů objektů funkcí watch ve Vue.js
V případě potřeby sledování atributu objektu, můsíme v funkci `watch`
 opět použít arrow funkci:

```javascript
watch(
  () => obj.count,
  (count) => {
    console.log(`count is: ${count}`)
  }
)
```
### Asynchronous watch funkce ve Vue.js
Pokud v rámci výpočtu modifikujeme reaktivní proměnnou, měla by watch funkce bát asynchronní.

```vue
<script setup>
import { ref, watch } from 'vue'

const question = ref('')
const answer = ref('Questions usually contain a question mark. ;-)')

// watch works directly on a ref
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.indexOf('?') > -1) {
    answer.value = 'Thinking...'
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    } catch (error) {
      answer.value = 'Error! Could not reach the API. ' + error
    }
  }
})
</script>

<template>
  <p>
    Ask a yes/no question:
    <input v-model="question" />
  </p>
  <p>{{ answer }}</p>
</template>
```


## Vytváření vlastních komponent ve Vue.js
Při vytváření reálné aplikace potřebujeme pracovat s více komponentami.

Komponenty musíme:
1. naimportovat v `setup` metodě
2. Vložit do šablony.

Mějme komponentu **ChildComp.vue**
```vue
<template>
  <h2>A Child Component!</h2>
</template>
```

Tuto komponentu pak použijeme v jiné komponentně následovně:
```vue
<script setup>
import ChildComp from './ChildComp.vue'
</script>

<template>
  <ChildComp />
</template>
```

## Definice property v komponentě ve Vue.js
Nadřazená komponenta může vložit do vnořené komponenty dat pomoci property.

Definice property `msg` ve vnořené komponentě **ChildComp.vue**:
```vue
<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <h2>{{ msg || 'No props passed yet' }}</h2>
</template>
```

Nastavení vlastnosti v nadřazené komponentě:
```vue
<script setup>
import { ref } from 'vue'
import ChildComp from './ChildComp.vue'

const greeting = ref('Hello from parent')
</script>

<template>
  <ChildComp :msg="greeting" />
</template>
```
## Skládání komponent pomocí slotů ve Vue.js
V rámci komponent můžeme rovněž definovat části, které používat `<slot>` pro vkládaní částí z nadřazených komponent do vložených.

Definice slotu ve vnořené komponentě **ChildComp.vue**:
```vue
<template>
  <slot>Fallback content</slot>
</template>
```

Použití slovu v nadřazené komponentě:
```vue
<script setup>
import { ref } from 'vue'
import ChildComp from './ChildComp.vue'

const msg = ref('from parent')
</script>

<template>
  <ChildComp><b>Message: </b>{{ msg }}</ChildComp>
</template>
```

V tomto okamžiku vnořená komponenta funguje jako *wrapper* okolo obsahu který do ní vkládá nadřazená komponenta.
## Vue .js a nástroje Lite
Od verze Vue.js 3 přibyla další možnost, a to pomocí nástroje [Vite](https://github.com/vitejs/vite).

Vite je nástroj pro vývoj webových aplikací.

Rychlost zajišťuje nativnímu přístupu k importu modulu ES.

Projekty Vue vytvoříte:

```
npm init @vitejs/app <project-name>
cd <project-name>
npm install
npm run devSample Editor Command
```
