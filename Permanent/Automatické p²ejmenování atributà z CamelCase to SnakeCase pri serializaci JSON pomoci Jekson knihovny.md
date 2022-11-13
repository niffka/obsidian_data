---
#aliases: [Automatické přejmenování atributů z CamelCase to SnakeCase pri serializaci JSON pomoci Jekson knihovny]
tags: [Honza]
created: 2022-02-10
---

# Automatické přejmenování atributů z CamelCase to SnakeCase pri serializaci JSON pomoci Jekson knihovny
Při převodu objektů je někdy potřeba převést jména paramaterů z jednoho formátu na druhý.
V tomto případě se jedná o [[CamelCase formát]], který použí Java na formát [[SnakeCase format]].

Je k tomu několik cest:

## 1. Pro každý atribut
```ad-tip
To se v tomto případě hodí spíše pro úplné přejmenování, kde není šance to provést automaticky.
```

```java
@JsonProperty("country_code")  
private String countryCode = NOT_DETECTED;
```

## 2. Pro celou třídu
[[Jackson knihovna]] umožnujě definovat *Naming strategy* pro celou třídu

```java
@JsonNaming(SnakeCaseStrategy.class)  
public class BrowserJson {
```

---
- [[Spring REST]]

## Reference
1. http://fasterxml.github.io/jackson-databind/javadoc/2.13/com/fasterxml/jackson/databind/PropertyNamingStrategies.html
2. https://www.baeldung.com/jackson-deserialize-snake-to-camel-case