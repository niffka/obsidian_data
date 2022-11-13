---
#aliases: [Vynuceni __repr__() při formátování řetězců]
tags: [Honza]
created: 2022-02-03
---

# Vynuceni __repr__() při formátování řetězců
Při použítá formátová řetězců se používa `str()` pro preprezentaci objektů.
Někdy například pro logování je lepší použít metodu `repr()`, které volá magickou metodu [[Magická metoda __repr__()|magickou metodu `__repr__()`]].

Pokud je to žádocí, můžeme za název proměnné přidat `!r`.

```python
d = {}

print(f'Reprezentace slovniku {d} je {d!r}')

```

---
- [[Python]]
- [[Formátování řetězců v Python]]

## Reference
1. https://docs.python.org/3/library/string.html#format-string-syntax