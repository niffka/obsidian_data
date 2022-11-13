---
#aliases: [Pandas]
tags: [Honza]
created: 2022-02-01
---

# Pandas
[Pandas](https://pandas.pydata.org/) je knihovna Pythonu, která je navržená tak, aby poskytovala rychlé a flexibilní datové struktury.

Přičemž vývojáři Pandas mají snahu, aby práce s těmito strukturami byla co nejvíce snadná a intuitivní.

Hodně je v nich vidět inspirace relačními databázemi nebo tabulkovými procesory (excel).

---

Pandas je knihovnou jazyka Python, ale není součástí základní distribuce.

Ale najdete ho v některých distribucích, jako je například [Anaconda](https://www.anaconda.com/ "https://www.anaconda.com/").

Také můžete použít příkaz:

pip install pandas

Knihovnu pak naimportovat do svého skriptu příkazem:

```python
import pandas as pd
```

_Pro Pandas se tolik používala zkratka **pd**, že ji mnozí autoři ani uvádějí._

### Pandas se dobře hodí pro:

-   Tabulková data s heterogenně zadanými sloupci, jako v tabulce SQL nebo Excelu
-   Údaje o časových řadách uspořádaných a neuspořádaných (nemusí být nutně pevná frekvence).
-   Libovolná maticová data (homogenně zadaná nebo heterogenní) s popisky řádků a sloupců

### V čem pandas vyniká

Ve Snadné manipulace s daty, a to i s chybějícími daty (reprezentovaný jako NaN), s desetinnými i celý čísly a dalšími typy dat.

Datové struktury jsou dynamické, co se do velikosti týče, dají se volně rozšiřovat. Přidávat sloupce i řádky ale i mazat.

Snadné spojování a seskupování dat, které velmi připomíná práci s SQL.

Dovoluje snadný převod různě indexovaných dat a uložených dat z různých struktur (pole, slovníky, Numpy Array) do `DataFrame`

Transformace tvaru matice (transpozice, pivot table).

Hierarchické indexy a práce s nimi.

Široká podpora různých nástrojů pro načítání a ukládání dat z/do CSV, excelu, SQL, HTML table a ultra rychlého formátu HDF5

Funkce specifické pro časové řady: generování časového období a převod kmitočtu, statistika pohyblivého okna, lineární regrese pohybujícího se okna, posunutí data a zpoždění atd.

---
- [[Dvě základní datové struktury v Pandas]]

## Reference
1. 