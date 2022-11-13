---
duration: 45min
---

# Úvod do problematiky webových aplikací
Úvod, web, HTTP komunikace - server/client, webový prohlížeč jako platforma, Apache

---
## Vyučující
- Ing. Jan Kolomazník, Ph.D.
- Ing. Ivo Pisařovic

Stánky: https://akela.mendelu.cz/~xkoloma1/wa 

---
## Ukončení předmětu
- projekt
	- řešený během semestru
 - nutné odevzdat
	- 50% výsledné známky
	- na konci nutné obhájit
- zkouška
	- test na počítači (teoretická + praktická + body z přednášek)
 - 50% výsledné známky
 
---
### Projekt - zadání - DS
![[WA-project-cartoon.png]]

---
## Co se naučíte?
- Více o [NodeJS](https://nodejs.org/en/) + frameworky + prostředí
- REST API
- JavaScript + některé knihovny
- SPA pomocí frameworku [Vue.js](https://vuejs.org/)

---
## Co byste už měli znát
- Základy HTML, CSS, jazyka JavaScript a databáze PostgreSQL, šablony
	 - Framework Expres a Mustache z APV 
- Principy relačních databází
	- databáze, tabulka, sloupec, řádek, primární klíč, index, cizí klíč, kardinalita vztahu (1:1, 1:n, m:n), normální formy
- Principy OOP
	- Třída, metoda, vlastnost + dědičnost
 
---
## Web/internet
- Moderní prostředí pro komunikaci
- Prostředí složené z propojených hypertextových dokumentů na různých serverech
- Prostředí služeb 
	- (např. zdrojů dat) dostupných na různých serverech

---
### Webová stránka
- Prezentace umístěná v prostředí internetu
- Slouží k předání určité informace
- Malá nebo žádná interakce
- Složena ze souborů (HTML, obrázky, CSS, minimum JS…)
 
---
![[WA-Web_Site-vs-Web_App .jpg]]

---
### Webová aplikace
- Aplikace spuštěná z webového serveru
- Velké možnosti interakce
- Uživatel pracuje pomocí "tenkého klienta" (prohlížeč) a spouští na serveru různé akce
- Data ukládá na server (obvykle databáze nebo cloudové služby)

---
#### Části Webová aplikace
- **Část klientská**
	- prezentace dat a navigačních nástrojů, možnost spouštět akce na serveru
 - HTML, CSS, volitelně i více JS
- **Část serverová**
	- stará se o modifikaci a ukládání dat
	- PHP (nebo jiné) skripty
	- úložiště (databáze, cloud)

---
## HTTP(S)
- Zkratka: **HyperText Transfer Protocol**
- Protokol pro přenos dat mezi klientem a serverem
- Port 80
 - Bez šifrování
 - nadstavba pro šifrování HTTPs (port 443)
- Bezstavový
- Požadavek + odpověď
	- Hlavičky + tělo

---
## URL/URI
- Zkratka: **Uniform Resource Locator/Identifier**
- řetězec lokalizující zdroj nebo službu
- obsahuje protokol, server, port, autentizaci, cestu, query, hash…
	- URL je vč. způsobu, jak zdroj oslovit
 
~~~ad-example
- https://login:heslo@akela.mendelu.cz:443/~vas_login/devel/index.php?a=123
- ftp://login:heslo@server.cz:21](ftp://login:heslo@server.cz/
- https://www.google.com](https://www.google.com/
~~~

---
## Webový prohlížeč jako platforma
- Webový prohlížeč je prostředí pro spouštění webových aplikací
	- dokáže zobrazit uživatelské rozhraní (HTML) a vaši grafiku/CSS
	- dokáže spustit váš kód v JavaScriptu
	- dokáže zprostředkovat rozhraní pro práci se soubory nebo jiným hardwarem (myš, klávesnice, GPS, mikrofon, kamera, …)

---
## Node JS
- Softwarový systém navržený pro psaní vysoce škálovatelných internetových aplikac
- Programy jsou psané v jazyce
- Využívající model událostí a asynchronní s I/O operace.
- Byl oceněn webem InfoWorld jako *Nejlepší technologie roku 2012*
 
---	

## Reference
1. https://nodejs.org/en/
2. https://vuejs.org/