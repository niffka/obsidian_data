---
#aliases: [Jak vynechat null položky v JSON]
tags: [Honza]
created: 2022-02-03
---

# Jak vynechat null položky v JSON
Nulové položky při seralizzaci objektu na [[json]], například pri implemntace [[REST API]] pomocí [[Spring framework MVC]] můžeme vynechat:

1. Pro kokrétní atribut rovněž pomocí annotace `@JsonInclude(Include.NON_NULL)`

```java
public class MyDto {
	
	@JsonInclude(Include.NON_NULL) 
	private String stringValue; 
	
	private int intValue; 
	
	// standard getters and setters 
}
```

2. Pro konktétní objekt pomocí annotace `@JsonInclude(Include.NON_NULL)`

```java
@JsonInclude(Include.NON_NULL) 
public class MyDto { ... }
```

3. Pro všechny objekty serializované pomocí jednoho mapperu:
```java
mapper.setSerializationInclusion(Include.NON_NULL);
```

4. Gloválně pro celou aplikaci ve [[Spring framework MVC]] 
- [ ] Najit způsob jak to dělat


---
- [[Jackson]]
- [[REST API]]
- [[Spring REST]]

## Reference
1. https://www.baeldung.com/jackson-ignore-null-fields