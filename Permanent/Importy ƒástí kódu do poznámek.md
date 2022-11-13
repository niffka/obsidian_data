---
#aliases: [Importy částí kódu do poznámek]
tags: [Honza]
created: 2022-02-01
---

# Importy částí kódu do poznámek
Pro prezentace je potřeba vkládat do poznámke reference na kód:
- To se dá sice obejít přímým vkádáním rovnou do textu, ale to se mizdá těžkopádné a je to krok zpět.
- Na stránkách Obsidianu je popsána možnost vlkádat [embeded files](https://help.obsidian.md/How+to/Embed+files) pomocí `!` ale jak vkládat části?
	- Jako neslibnější možnost se mi jeví možnost použít `<iframe>`
	
[Testovací soubor](https://gitlab.com/jan.kolomaznik/pyth1/-/raw/master/hello.py)

#### Vložení přes `!`

~~~
![](https://gitlab.com/jan.kolomaznik/pyth1/-/raw/master/hello.py)
~~~

#### Vloženi přes `<iframe>`

~~~
<iframe 
		border=0
		frameborder=0
		width=600
		height=250
		src="https://gitlab.com/jan.kolomaznik/pyth1/-/raw/master/hello.py">
</iframe>
~~~

Problém `<iframe`> je, že se musí určovat velikost, šířka je ok, ale výška...

#### Vložení přes plugin `quoth`
Tento plugin umožňuje vkládat části souborů, musí být ale uvnitř *vault*

~~~
```quoth
path: [[OpenAi]]
ranges: 4:0 to 12:0
display: embedded
```
~~~

----

[[Spolecny Zettlekasten]]

## References
- https://help.obsidian.md/How+to/Embed+files
- https://github.com/erykwalder/quoth