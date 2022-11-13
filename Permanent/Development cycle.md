---
#aliases: [Development cycle]
tags: [Honza]
created: 2022-02-20
theme: simple
---

# Development cycle
**Nasazení software a služeb**

_Jan Kolomaznik_

---
## Cyklus vývoje SW
![SW development cycle](https://bigwater.consulting/wp-content/uploads/2019/04/SDLC_BWC.png)

--
Nebo také

![](https://upload.wikimedia.org/wikipedia/commons/7/7e/SDLC-Maintenance-Highlighted.png)

...

---
## Životní cyklus softwaru
Etapy:
1.  Analýza a specifikace požadavků (8 %)[1)](https://kalabovi.org/pitel:isz:zivotni_cyklus_softwaru#fn__1)
2.  Architektonický a podrobný návrh (7 %)
3.  Implementace (12 %)
4.  Integrace a testování (6 %)
5.  Provoz a údržba (67 %)
    
--
### Analýza a specifikace požadavků
- Snažíme se přesně specifikovat co zákazník chce (ale neřešíme jak toho dosáhnout), protože on to většinou neví.
- V této etapě také zjistíme jestli to zákazník produkt opravdu potřebuje. 
- Výstupem může být analýza rizik, ale především **akceptační testy** – testy, které si provede zákazník při převzetí, a pokud jsou splněny, je SW v pořádku.

--
### Architektonický a podrobný návrh
- Naplánování rozdělení na podproblémy, specifikace jejich funkcionalit a rozhraní mezi nimi. Také se plánují podrobnější testy systému.

- Také je vhodné už teď naplánovat postup nasazení, protože zatím nejsme ve stresu a tlačeni časem a tak se nad tím dá v klidu zamyslet.

--
### Podrobný návrh
- Podrobnější zamyšlení nad jednotlivými moduly, jejich algoritmy a datovými strukturami.
- Výstupem by měl být odhad ceny a jednotlivých modulů, jejich nároků na lidské zdroje a čas. 
- Výstupem by také měly být podrobnější testy jednotlivých modulů

--
### Implementace a testování součástí
- Programování, realizace, dokumentace.

--
### Integrace a testování systému
- Začlenění jednotlivých modulů dohromady a jejich testování. 
- Při testování se často vracíme k předchozímu kroku, kvůli opravám chyb.

--
### Akceptační testování a instalace
- Otestování systému uživatelem, který se na základě (ne)splnění akceptačních testů produkt (ne)převzít. 
- Proto jsou akceptační testy důležité, jinak by mohl zákazník oddalovat převzetí projektu (a samozřejmě by nechtěl za prodloužení platit) a my bychom na něj neměli žádné páky.

--
### Provoz a údržba
- Řešení problémů při provozu a opravy nalezených chyb. 
- Také rozšiřování o nové funkce.

---
## Základni modely

--
### Vodopádový
- [![](https://kalabovi.org/lib/exe/fetch.php?tok=fde956&media=http%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fen%2Fthumb%2Fe%2Fe2%2FWaterfall_model.svg%2F200px-Waterfall_model.svg.png)](https://en.wikipedia.org/wiki/Waterfall%20model "https://en.wikipedia.org/wiki/Waterfall model")Jednotlivé etapy na sebe navazují. 
- Až je jedna etapa dokončena, začne teprve další. 
- Nejjednodušší a nejpřirozenější model.

- Nevýhodou je, že když zákazník dostane hotový produkt a něco si rozmyslí, musí se začít v podstatě od začátku. 
- Což může být problém, protože analytici už nejspíš pracují na jiném projektu a tento si jen matně vybavují. 
- V reálném životě se navíc jednotlivé etapy často překrývají, nebo jsou dokonce v jiném pořadí.
--
### Iterativní a inkrementální

[![upload.wikimedia.org_wikipedia_commons_a_ac_iterative_development_model_v2.jpg](https://kalabovi.org/lib/exe/fetch.php?tok=078e4e&media=http%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2Fa%2Fac%2FIterative_development_model_V2.jpg "upload.wikimedia.org_wikipedia_commons_a_ac_iterative_development_model_v2.jpg")](https://en.wikipedia.org/wiki/Iterative%20and%20incremental%20development "https://en.wikipedia.org/wiki/Iterative and incremental development")
- Jednotlivé etapy (kromě prvotní analýzy a předání produktu) se opakují, a teprve až je vše v pořádku, dojde k předání výsledného softwaru.
--
### Spirálový

[![](https://kalabovi.org/lib/exe/fetch.php?tok=eed6e3&media=http%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2Fthumb%2Fe%2Fec%2FSpiral_model_%28Boehm%2C_1988%29.svg%2F200px-Spiral_model_%28Boehm%2C_1988%29.svg.png)](https://en.wikipedia.org/wiki/Spiral%20model "https://en.wikipedia.org/wiki/Spiral model")
- Jednotlivé etapy se opakují jako u iterativního modelu, ale je zde zaveden tzv. **prototyp**, který si může zákazník vyzkoušet. 
- Při každé další iteraci je tak výsledek značně blíže cíli, protože velmi rychle získáváme zpětnou vazbu od zákazníka.

--
**Prototyp** se od „verze s omezenou funkcionalitou“ liší tím, že je po otestování zahozen, a nový prototyp se vytváří znovu (často se však „zrecyklují“ staré fungující kusy projektu).

--
### RUP
[IBM Rational Unified Process](https://en.wikipedia.org/wiki/IBM%20Rational%20Unified%20Process "https://en.wikipedia.org/wiki/IBM Rational Unified Process")

### Agilní
[Agile software development](https://en.wikipedia.org/wiki/Agile%20software%20development "https://en.wikipedia.org/wiki/Agile software development")

---
## Moderní trendy vývoje 
- Za posledních dvacet let se vývoj softwaru významně změnil.
--
- Původní model byl takový:
	-   Vytvořil se projektový plán
	-   Analytici sesbírali od klienta business požadavky
	-   Přetvořili je společně s klientem ve funkční požadavky
	-   Vše popsali https://kalabovi.org/pitel:isz:zivotni_cyklus_softwaruve specifikaci
	-   Tu předali k tvorbě architektury a technického designu seniorním vývojářům a architektům
	-   Poté se to předalo na vývoj a ten dlouhou dobu vyvíjel
	-   Software se testoval = testoval se interně a s uživateli
	-   Pak se software předal administrátorům, ti jej nasadili a provozovali (monitorovali).
- A podobně to bylo s každou další změnou a rozšířením.
--
- Popsaný model vývoje funguje někdo do teď. 
- Stále je to vlastně takový základ, který dává smysl - něco se prozkoumá, navrhne se řešení, naprogramuje se to, a pak se to používá. 
- Tento základní princip totiž asi jen tak nic nezmění (nebudeme nejprve programovat, abychom pak teprve zjišťovali, co kdo chtěl naprogramovat - i když tohle se také děje :-)).
- Jde především o to, v jaké míře a jak moc rigidně se tento model dodržuje.
--
- Moderní přístup se snaží o větší flexibilitu, zrychlení celého procesu, dělání všeho v iteracích, více agilně. 
- Míra, jak hodně se tento postup aplikuje striktně ve výše uvedeném postupu a jak moc je zjednodušený, agilní, záleží na prostředí. 
	- Například stále některé banky a velké instituce realizují projekty stále tímto postupem, kterému se říká waterfall, 
	- naproti tomu startupy a businessově exponované sektory (např. e-commerce) jdou agilnější cestou. 
- V jejich případě je to dáno potřebou rychle reagovat na změny, které se na trhu odehrávají.
--
- Problém tohoto rigidního postupu je totiž čas a flexibilita. 
- Takový projekt se může vyvíjet roky, když vezmeme všechny fáze včetně analýz a nasazení. 
- Za tři roky ale může dojít ke změně zadání - a většinou k němu také dojde. 
- Zároveň na začátku lidé nedokáží popsat, co přesně chtějí a po spuštění projektu uživatelé zjišťují, že chtěli trochu něco jiného. 
- To už je ale pozdě. Každá změna pak prochází stejným postupem. 
- Právě tomuto modelu se říká waterfall, všechny fáze jdou jen směrem dopředu a zpětně proti vodopádu se k zadání vrací špatně.
--
- Waterfall sám o sobě není špatný a v určitých sektorech a pro určité problémy dává smysl.
- Záleží na velikosti projektu, prostředí, schopnosti fungovat agilně apod. 
- Waterfall je dnes brán jako sprosté slovo, ale reálně se s ním pracuje velmi často. 
- A není to chyba dodavatelské firmy. 
- Představte si veřejnou zakázku, kde si stát objedná projekt, neví ovšem, co dostane, a také neví, kolik ho to bude stát a má porovnat mezi sebou nabídky a vybrat nejlepší. 
- Úředníci jsou ale mnohdy pod tlakem, navíc kontrolováni, proto si takový agilní přístup nemohou dovolit. 
- Stejně tak velké firmy.

---
### Jak celý proces udělat flexibilnější?

--
**Agilita, metodologie Scrum:**
- Stanoví se high level cíl, iteruje se v krátkých sprintech, např. týden, 14 dní. 
	- Výsledkem je nový kód, nový kus projektu. 
	- Vždy po konci části projektu se sejde zadavatel s vývojovým týmem a řeknou si, co by se mělo změnit a jak dál postupovat.
- Zrychlí se tím celý cyklus, dohodnutá věc je vidět brzy a ne až za 3 roky. 
	- Ale samozřejmě nemáte za 14 dní celý projekt, stejně se tedy nedá kompletně otestovat, pořád je ale lepší než čekat několik let a pak většinu vyhodit.
--
**Microservices, jiný styl architektury:**
- Stále velmi populární téma, které umožňuje nepsat software jako obrovský monolit, ale rozdělit ho na samostatně žijící servisy (malé software na serveru), které si spolu povídají.
	- Výhoda u velkých projektů: na servise pracuje vždy jeden tým, má know how, dokáže si to měnit. 
	- Když udělají změnu, ale nedojde ke změně API (tj. komunikace mezi jinými službami), pak to nikoho nemusí až tak zajímat. 
	- Tým dostane do produkce pár kliky novou verzi, mění si jenom svojí servisu. 
	- Opět se tím urychlí proces doručení.
--
- Není ovšem dobré to s microservices moc přehánět 
	- (tj. mít stovky malých servis, když to není v dané situaci nutné, například když pracují na všech službách stejní lidé, nepomáhá to výkonu systému). 
	- Celkově to totiž prodraží vývoj a náklady se naopak šetří až u větších systémů, případně systému s velkým požadavkem na výkon.

---
* Styl, jakým se vyvíjí ve firmách software, se různí a je opravdu na široké škále všeho výše popsaného. 
	* Určitě není pravidlo, že každá firma musí vyvíjet agilně, striktně aplikovat DevOps a celý systém dnes přepsat do mikroservis.  
	* Je to ale cesta, kterou se již nějakou dobu vydává postupně celý svět a ve spoustě případů dává velký smysl.

---
![[Výhody cloudu a virtualizace při vývoji aplikací]]


---
## Teoretické seznámení s DevOPS
- Mění proces tak, že sloučí lidi, co dělají vývoj a provoz (adminy). 
	- Je to tedy Development and Operations, z toho zkratka DevOps. 
	- Developeři jsou potom takoví admini. 
--
- Vliv na Agilitu
	- Je to podobné jako u vývojových cyklů v agilitě (business je tam více spojený s vývojem, s analýzou), vše se tím urychlí. 
	- Nasadit projekt v nějaké těžkopádnější instituci trvá třeba i měsíce. 
	- Vývojáři mají hotovo a pak se čeká na adminy. 
	- Veškeré změny v konfiguraci si řeší admini, developeři do nich nevidí, všechno je příliš zdlouhavé. 
	- Naopak v DevOps to dělají developeři.
--
- Výhoda DevOps je, že vyvíjí software tak, jak si ho sami budou provozovat. 
	- Neberou to tak jako že „tohle bude na adminech“. 
	- Už první verze si někam nasazují a většinou podobně pokračují na produkčním (ostrém) prostředí. 
	- Takže to nenechávají nakonec adminům, ale celý ten výrobní chain softwaru se hned na začátku nastaví.
--
- Tomu pomáhají moderní nástroje pro kontejnerizaci, virtuální stroje a další. 
	- Velmi populárním nástrojem je Docker, který jakoby „zabalí“ celý software včetně celého operačního systému do jednoho balíku („image“) a ten je možno nasadit k sobě na laptop nebo třeba na produkční server a to bez jakýchkoliv změn v softwaru a operačním systému.
--
- Pomáhá tomu continuous integration, tedy automatizace nasazování. 
	- Vývojář vyvine, pošle kód a on se mu automaticky dostane na server. 
	- Tím se opět zrychluje celý proces. 
	- Zároveň se nový kód před nasazením na server otestuje pomocí automatizovaných testů bez zásahu člověka. 
	- Tím se ověří, že se v softwaru nic nerozbilo a ušetří se čas na dlouhé regresní testování celého systému.

---
## Technologie pro continuous integration a jejich implementace
- CI je zkratkou continuous integration - česky průběžná integrace. 
- Využívá se u systémů správy verzí (Git, Subversion, ...) hlavně pro automatické testování kódu. 
- Obecně lze CI využít k provedení jakýhkoliv příkazů či skriptů na daném projektu, po nahrání nových změn do repozitáře. 
- Například když spravujete větší projekt, do kterého přispívá několik vývojářů, tak díky CI vidíte na první pohled, jestli začleňované změny fungují a jestli celý projekt nerozbijí.
--
Mezi hlavní důvody k použití průběžné integrace a nasazení integračního serveru nebo prostředí patří:
-   Vysoká **chybovost** ve zdrojových kódech.
-   Nalezení chyb je **časově a kapacitně náročné**
-   Tvorba nových buildů je **složitý proces**
-   Tvorba buildu je **každodenní záležitost**
-   Nepořádek ve **verzování** jednotlivých buildů
-   Nedostatečný **technický dohled** nad softwarovými projekty
-   Nepořádek v **úložišti zdrojových kódů** (CVC, SVn GIT)

---
## Shrnutí
- nutnost plánování projektu, protože jinak je to naprostý chaos
- základní fáze: analýza požadavků, návrhy, implementace, testování a odevzdávání, provoz a údržba (nejnáročnější)
- vodopádový model, iterativní model, spirálovitý model (prototypy)
- RUP: iterativní vývoj, aktivní správa požadavků, komponentová struktura, ověřování kvality, vizuální modelování, řízení změn
- RUP fáze: zahájení, příprava, konstrukce, předávání
- RUP disciplíny: tvorba podnikového modelu, správa požadavků, analýza a návrh, implementace, testování, nasazení
- Agilní: krátké časové úseky, malé jednotky lidí, kteří se starají o své moduly, rychlé vytváření meziproduktů, snížený důraz na dokumentaci, …
- Agilní metody: například extrémní programování  
- Agilní postupy: např. test-driven programming, analýza a code-refactoring



---
- [[NSS]], [[LS 2021/2022]]

## Reference
1. https://kalabovi.org/pitel:isz:zivotni_cyklus_softwaru
2. https://www.systemonline.cz/sprava-it/soucasne-trendy-ve-vyvoji-software.htm 
3. https://theses.cz/id/21v8dq/STAG89423.pdf