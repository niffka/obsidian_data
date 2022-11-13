---
#aliases: [Příklad datové analýzy - t-test]
tags: [Honza]
created: 2022-02-01
attachments: pandas.t-test.example
---

# Příklad datové analýzy: t-test

**Pojďme se podívat na příklad, kdy se z veřejně dostupných dat budeme snažit ověřit naši hypotézu.** _Tento příklad je převzat z kurzu: Introduction to Data Science in Python by University of Michigan_

---

### Formulace hypotézy

Univerzitní města mají průměrné ceny bydlení méně ovlivněné recesemi.

Na ověření hypotézy použijeme [t-test](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.ttest_ind.html#scipy.stats.ttest_ind) a budeme porovnává průměrné ceny domů v univerzitních městech čtvrtletí před začátkem recese ve srovnání se dnem recese.

price_ratio = quarter_before_recession / recesion_bottom

Čtvrtletí : čtvrtletí je tříměsíční období, které budeme označovat rokem a příponou `q1`, `q2`, `q3`, `q4`.

Recese : Recese je definována jako obdobím začínající dvěma po sobě jdoucími čtvrtinami poklesu HDP a končící dvěma po sobě následujícími čtvrtinami růstu HDP.

Dno recese : Je čtvrtletí v rámci recese, které mělo nejnižší HDP.

### Data pro ověření hypotézy

Pro toto přiřazení jsou k dispozici následující datové soubory:

1.  Data z výzkumného datového serveru [Zillow](https://www.zillow.com/ "https://www.zillow.com/") s údaji obsahujícími průměrné prodejní ceny domů v Amerických městech: [`static/City_Zhvi_AllHomes.csv`](static/City_Zhvi_AllHomes.csv)
2.  Ze stránky Wikipedia ze stránky [List_of_college_towns](https://en.wikipedia.org/wiki/List_of_college_towns), kde je uveden seznam univerzitních měst: [`static/university_towns.txt`](static/university_towns.txt).
3.  A od [Bureau of Economic Analysis](https://www.bea.gov/ "https://www.bea.gov/"), amerického ministerstva obchodu, udaje o HDP v čase, jenž jsou uložena v souboru: [`static/gdplev.xls`](gdplev.xls.md). V našem příkladě použijeme pouze data od 1 čtvrtletní roku 2000 a to hodnotu uloženou ve sloupci **GDP in billions of chained 2009 dollars**.
4.  Slovník (`dict`) v jazyce pythonu obsahujícím kódy amerických států.

```python
# Use this dictionary to map state names to two letter acronyms
states = {'OH': 'Ohio', 'KY': 'Kentucky', 'AS': 'American Samoa', 'NV': 'Nevada', 'WY': 'Wyoming', 'NA': 'National', 'AL': 'Alabama', 'MD': 'Maryland', 'AK': 'Alaska', 'UT': 'Utah', 'OR': 'Oregon', 'MT': 'Montana', 'IL': 'Illinois', 'TN': 'Tennessee', 'DC': 'District of Columbia', 'VT': 'Vermont', 'ID': 'Idaho', 'AR': 'Arkansas', 'ME': 'Maine', 'WA': 'Washington', 'HI': 'Hawaii', 'WI': 'Wisconsin', 'MI': 'Michigan', 'IN': 'Indiana', 'NJ': 'New Jersey', 'AZ': 'Arizona', 'GU': 'Guam', 'MS': 'Mississippi', 'PR': 'Puerto Rico', 'NC': 'North Carolina', 'TX': 'Texas', 'SD': 'South Dakota', 'MP': 'Northern Mariana Islands', 'IA': 'Iowa', 'MO': 'Missouri', 'CT': 'Connecticut', 'WV': 'West Virginia', 'SC': 'South Carolina', 'LA': 'Louisiana', 'KS': 'Kansas', 'NY': 'New York', 'NE': 'Nebraska', 'OK': 'Oklahoma', 'FL': 'Florida', 'CA': 'California', 'CO': 'Colorado', 'PA': 'Pennsylvania', 'DE': 'Delaware', 'NM': 'New Mexico', 'RI': 'Rhode Island', 'MN': 'Minnesota', 'VI': 'Virgin Islands', 'NH': 'New Hampshire', 'MA': 'Massachusetts', 'GA': 'Georgia', 'ND': 'North Dakota', 'VA': 'Virginia'}
len(states)
```

## Příprava dat

Jak je vidět, data jsou v různých formátech a nejprve je musíme vhodně načíst a zpracovat.

### Data o Amerických městech

Nejprve vytvoříme `DataFrame` obsahující názvy měst a informace, do kterého státu patří.

Ty jsou v jednoduchém textovém formátu:`

```
Alabama[edit]
Auburn (Auburn University)[1]
Florence (University of North Alabama)
Jacksonville (Jacksonville State University)[2]
Livingston (University of West Alabama)[2]
Montevallo (University of Montevallo)[2]
Troy (Troy University)[2]
Tuscaloosa (University of Alabama, Stillman College, Shelton State)[3][4]
Tuskegee (Tuskegee University)[5]
Alaska[edit]
Fairbanks (University of Alaska Fairbanks)[2]
Arizona[edit]
```

Nejprve je uveden název Regionu (následuje vždy řetězec `[edit]`). Poté následují názvy měst pro region. Za těmi je v kulaté závorce uvedena příslušná univerzita.

Vytvoříme tedy datovou tabulku s dvojitým indexem (`State` a `RegionName`) což je jedinečný identifikátor města. Jako hodnoty přiřadíme `True` do jednoho datového sloupce tohoto DataFrame "university".

```python
import re

university_towns = pd.DataFrame(columns=["State", "RegionName"])
re_state = re.compile(r'^([\w ]+)\[.*$')
re_region = re.compile(r'^(.+?) \(.*$')

with open('static/university_towns.txt', mode='r') as f:
    for line in f.readlines():
        state_match = re_state.match(line)
        if state_match:
            state = state_match.group(1)
            continue
        
        region_match = re_region.match(line)
        if region_match:
            region = region_match.group(1)
            university_towns = university_towns.append({'State':state, 'RegionName':region}, ignore_index=True)
            continue
        
        university_towns = university_towns.append({'State':state, 'RegionName':line.replace(':', '')}, ignore_index=True)

university_towns["university"] = True
university_towns = university_towns.set_index(["State","RegionName"]).sort_index()
university_towns.head(10)
```

### Načtení dat o HDP po čtvrtletích:

Nyní zpracujeme data o HDP, která si zobrazíme do grafu, abychom měli hrubou představu o jeho průběhu.

_Podívejte se do excelové tabulky, v jakém formátu se data nacházejí, aby Vám byly jasné některé operace._

V tabulce jsou uložena data po čtvrtletích od roku 1947, nám ale stačí od roku 2000 dále, proto vybereme jen potřebné roky.

```python
gdplev = (pd.read_excel('static/gdplev.xls', usecols=[4,6], skiprows=7)
   .rename(columns={'Unnamed: 6': 'GDP', 'Unnamed: 4': 'year_quarter'})
   .set_index('year_quarter')
   .loc["2000q1":,:]
)

gdplev.plot(figsize=(15,5), grid=True)
```

A dalším krokem je určit datum začátku recese.

```python
decrease = gdplev["GDP"].diff() < 0
two_year_decrease = decrease.rolling(2).sum() == 2
recession_start = gdplev[two_year_decrease].index[0]
recession_start
```

a konce recese lze pak zjistit velmi podobně.

```python
gdplev_after_recession_start = gdplev.loc[recession_start:]
two_year_grow = (gdplev_after_recession_start["GDP"].diff() > 0).rolling(2).sum() == 2
recession_end = gdplev_after_recession_start[two_year_grow].index[0]
recession_end
```

A výpočet vrcholu hospodářské krize:

```python
year_of_recess = gdplev.loc[recession_start:recession_end, "GDP"]
recession_bottom = year_of_recess.idxmin()
recession_bottom
```

Následně jsi nalezené informace vykreslíme opět do grafu. K tomu nám pomůže knihovna [Matplotlib](https://matplotlib.org/")

```python
import matplotlib.pyplot as plt
%matplotlib inline


fig, ax = plt.subplots(figsize=(15, 4))
gdplev.plot(ax=ax)

ax.annotate("Recession bottom",
           xy=(gdplev.index.get_loc(recession_bottom), gdplev.loc[recession_bottom,"GDP"]), 
           xycoords='data',
           bbox=dict(boxstyle="round", fc="none", ec="gray"),
           xytext=(10, 40), textcoords='offset points', ha='center',
           arrowprops=dict(arrowstyle="->"))

ax.annotate('Recession',
           xy=(gdplev.index.get_loc(recession_bottom), gdplev.loc[recession_bottom,"GDP"]),
           xycoords='data',
           ha='center',
           xytext=(0, -25), textcoords='offset points')
ax.annotate('',
           xy=(gdplev.index.get_loc(recession_start), gdplev.loc[recession_start,"GDP"]),
           xytext=(gdplev.index.get_loc(recession_end), gdplev.loc[recession_end,"GDP"]),
           xycoords='data',
           textcoords='data',
           arrowprops={'arrowstyle': '|-|,widthA=0.2,widthB=0.2', })


ax.set(title='Development of GDP in the USA',
      ylabel='GDP',
      xlabel="quarters")

fig.show()
```

### Načtení informací o cenách nemovitosti:

Tabulka, tentokrát ve formátu csv, obsahuje řadu údajů. My musíme v rámci jejího načtení vyřešit dvě věci:

1.  Vhodně nastavit index tak, aby se data dala spárovat s univerzitními městy.
2.  Transformovat data, která jsou po měsíci, na čtvrtletní.

Nejprve ale data načteme, vybereme jen potřebné roky (od 2000) a vhodně na indexuje.

```python
convert_housing = pd.read_csv('static/City_Zhvi_AllHomes.csv')
convert_housing['State'].replace(states, inplace=True)
convert_housing = (convert_housing
   .set_index(["State","RegionName"])
   .sort_index()
   .loc[:,'2000-01':]
)

convert_housing.head()
```

Pro převod roku a měsíce na čtvrtletí si vytvoříme pomocnou funkci:

```python
import re

def date_to_quater(year_month):
    if type(year_month) == re.Match: # Při testování přichází String, ale
        year_month = year_month.group(0) # pandas bude posílat match z regexu.
    
    year = year_month[:4]
    month = int(year_month[5:])
    quater = ((month - 1) // 3) + 1
    return year + "q" + str(quater)

# Jednoduchý test správnosti ....
date_to_quater("2000-01")
```

Následně převedeme každý měsíc v roce do správného čtvrtletí, čímž získáme sloupce stejných se stejnými názvy. To nám ale nevadí, protože následně tato data seskupit a spočítáme průměr.

```python
convert_housing.columns = convert_housing.columns.str.replace(r'.+', date_to_quater)
convert_housing.head()
```

```python
housing_data = (convert_housing
   .groupby(convert_housing.columns.values,axis=1)
   .mean()
)

housing_data.head()
```

Můžeme se podívat na průběh cen nemovitosti a HDP dohromady:

```python
housing_sum = housing_data.mean()
housing_sum.name = "Prices"

ax_gdplev = gdplev.plot()

ax_housing = ax_gdplev.twinx()
ax_housing.spines['right'].set_position(('axes', 1.0))
housing_sum.plot(ax=ax_housing, c="orange", legend=True)
```

## Ověření hypotézy

Nyní máme všechna data načtená a připravená pro další krok.

Spočítáme tedy poměr cen v období před začátkem krize v době vrcholu (dna) krize:

```python
housing_data['ratio'] = housing_data["2008q3"] / housing_data[recession_bottom]
ratio = (housing_data
   .loc[:, 'ratio':'ratio']
   .dropna()
)

ratio.head()
```

V Dalším kroku roztřídíme univerzitní a neuniverzitní města. To provedeme tak, že k tabulce **ratio** připojíme tabulku s univerzitními městy.

Města, která nejsou univerzitní, budou mít v nové tabulce ve sloupci "'university'" hodnotu `NaN`. Tu změnit na `False`.

A vypíšeme průměrné hodnoty **ratio** pro univerzitní a neuniverzitní města.

```python
df = pd.merge(ratio, university_towns, how='left', left_index=True, right_index=True)
df['university'] = df['university'].fillna(False)

df.groupby('university').mean()
```

Posledním krokem je ověření naší hypotézy výpočtem **p-value**.

```python
from scipy.stats import ttest_ind

university = df[df['university'] == True]['ratio']
non_university = df[df['university'] == False]['ratio']

ttest_ind(university, non_university)
```

Hodnota **p-value** je menší než 0.05? Pokud ano, tak se hypotéza potvrdila.

Problém je ale použití špatné statistivké metody, pro daný příklad totiž `ttest_ind` nezle použít.

```python
ttest_ind(university.sample(100), non_university.sample(100))
```

---
- 

## Reference
1. 