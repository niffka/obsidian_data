---
#aliases: [Životní cyklus komponent ve Vue.js]
tags: [Honza]
created: 2022-03-09
---

# Životní cyklus komponent ve Vue.js
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

# Reference
- **Téma(ta)**: [[Vue.js]]
- **Kam dál**: 
	- 
- **Biblio**:
	1. https://vuejs.org/api/composition-api-lifecycle.html