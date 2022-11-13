---
#aliases: [Parametrizované testy v pytest]
tags: [Honza]
created: 2022-02-03
---

# Parametrizované testy v pytest

Častým případem při psaní testů je, že chceme otestovat funkcionalitu, ale na jiných datech.

Například funkci `is_palindrome`:
```python
def is_palindrome(s):
	return s == s[::-1]
```

A tuto funkci chceme otestovat:
```python
%%run_pytest[clean]

def test_is_palindrome_empty_string():
	assert is_palindrome("")

def test_is_palindrome_single_character():
	assert is_palindrome("a")

def test_is_palindrome_mixed_casing():
	assert is_palindrome("Bob")

def test_is_palindrome_with_spaces():
	assert is_palindrome("Never odd or even")

def test_is_palindrome_with_punctuation():
	assert is_palindrome("Do geese see God?")

def test_is_palindrome_not_palindrome():
	assert not is_palindrome("abc")

def test_is_palindrome_not_quite():
	assert not is_palindrome("abab")
```

Jedná se o velmi podobné testy líčící se je hodnout a jménem

```python
def test_is_palindrome_<in some situation>():
	assert is_palindrome("<some string>")
```

Můžete použít `@pytest.mark.parametrize()` k vyplnění tohoto tvaru různými hodnotami, čímž výrazně snížíte svůj testovací kód:
```python
%%run_pytest[clean]

@pytest.mark.parametrize("palindrome", [
	"",
	"a",
	"Bob",
	"Never odd or even",
	"Do geese see God?",
])
def test_is_palindrome(palindrome):
	assert is_palindrome(palindrome)

  
@pytest.mark.parametrize("non_palindrome", [
	"abc",
	"abab",
])
def test_is_palindrome_not_palindrome(non_palindrome):
	assert not is_palindrome(non_palindrome)
```

Zde je ještě jeden příklad:

```python
%%run_pytest[clean]

from isHoliday import getholidays

@pytest.mark.parametrize('year', (2015, 2016, 2017, 2033, 2048))

def test_xmas(year):
	"""Test whether there is Christmas"""
	holidays = getholidays(year)
	assert (24, 12) in holidays
```

První argument `parametrize()` slouží k pojmenování parametrů a druhým je `list` hodnot nebo `tuple`, které představují hodnoty parametrů testovací funkce.

Takto můžete všechny metody sloučit do jedné.

```python

%%run_pytest[clean]
	@pytest.mark.parametrize("maybe_palindrome, expected_result", [
		("", True),
		("a", True),
		("Bob", True),
		("Never odd or even", True),
		("Do geese see God?", True),
		("abc", False),
		("abab", False),
])
def test_is_palindrome(maybe_palindrome, expected_result):
	assert is_palindrome(maybe_palindrome) == expected_result
```

Nevýhoda více téměř stejných testů je patrná sama o sobě, nevýhoda cyklu je v tom, že celý test selže, i pokud selže jen jeden průběh cyklem.

Zároveň se průběh testu při selhání ukončí.

A ještě jeden příklad na svátky, tentokrát s více parametry:
```python
%%run_pytest[clean]

@pytest.mark.parametrize(['year', 'month', 'day'],
						 [(2015, 12, 24),
						  (2016, 12, 24),
						  (2017, 1, 1),
						  (2033, 7, 5),
						  (2048, 7, 6)],
)
def test_some_holidays(year, month, day):
	"""Test a few sample holidays"""
	holidays = isholiday.getholidays(year)
	assert (day, month) in holidays
```

Vždy je dobré pokusit se nějaký test rozbít v samotném kódu, který testujeme, abychom se ujistili, že testujeme správně.

Přidáme tedy dočasně na konec funkce `getholidays()` tento pesimistický kus kódu:

```python
if year > 2020:
	# After the Zygon war, the puppet government canceled all holidays
	holidays = set()
```

---
- [[Pytest]]

## Reference
1. [isHoliday.py](https://gist.github.com/oskar456/e91ef3ff77476b0dbc4ac19875d0555e)
2. [Getting Started With Testing in Python](https://realpython.com/python-testing/)
3. [Effective Python Testing With Pytest](https://realpython.com/pytest-python-testing/)
4. [Nauč se Python: Testování 2](https://naucse.python.cz/lessons/intro/testing/)