---
title: 3. W trybie interaktywnym 
layout: post
---

Na początku nauki Pythona warto zaprzyjaźnić się z jego **interaktywnym trybem pracy**, czyli tzw. **interpreterem** lub **konsolą Pythona**.  
To miejsce, w którym możesz od razu pisać kod, testować pomysły i sprawdzać działanie poszczególnych poleceń.  
To trochę jak rozmowa z Pythonem - Ty coś wpisujesz, on od razu odpowiada. 🐍💬

## Jak uruchomić interpreter?

Otwórz terminal lub wiersz poleceń na swoim komputerze.  
Wpisz komendę:

```
python
```

lub (na niektórych systemach):

```
python3
```

Jeśli wszystko działa poprawnie, zobaczysz coś takiego:

```
    Python 3.7.2 (default, ...)
    Type "help", "copyright", "credits" or "license" for more information.
    >>>
```

Znak `>>>` to tzw. **prompt** Pythona – oznacza, że interpreter jest gotowy przyjąć Twoje polecenie.

📍 Wcześniej w konsoli systemowej znak zachęty miał postać np. `~$` lub `C:\>`.  
Po uruchomieniu Pythona zmienia się on na `>>>`, co oznacza, że teraz rozmawiamy bezpośrednio z Pythonem.

WAŻNE: W przykładach poniej nie przepisuj `>>>`, to tylko symbol znaku zachęty.

---

## Pierwszy kod w Pythonie 🐍

Spróbuj wpisać:

```python
>>> print("Hello, world!")
```

Po naciśnięciu Enter zobaczysz:

```
Hello, world!
```

Gratulacje! 🎉 Właśnie napisałaś/napisałeś swój pierwszy program w Pythonie.

🔍 `print()` to funkcja, która służy do wyświetlania tekstu lub wartości w konsoli.

---

## Python jako kalkulator 🧮

Python potrafi też liczyć.  
Spróbuj wpisać kolejno:

```python
>>> 2 + 3

>>> 10 - 4

>>> 8 * 5

>>> 12 / 4
```

Python odpowie:
```
    5
    6
    40
    3.0
```
---

## Trochę teorii

- **Operacje arytmetyczne** to działania matematyczne, które dobrze znamy: dodawanie, odejmowanie, mnożenie, dzielenie itd.
- **Operatory** to znaki takie jak `+`, `-`, `*`, `/`, które mówią Pythonowi, co ma zrobić.
- **Wyrażenie** to połączenie danych i operatorów, np. `5 + 7`, które daje nową wartość.

Inaczej mówiąc: wszystko to już znasz – teraz uczysz się, jak powiedzieć to Pythonowi. 💡

---

## Jak wyjść z interpretera?

Aby zakończyć pracę z interpreterem, wpisz:
```
>>> exit()
```
lub naciśnij:

- **Ctrl + Z**, a potem Enter (Windows)
- **Ctrl + D** (Mac/Linux)



To wszystko na początek! W następnym kroku napiszemy już **pierwszy plik `.py`**, zapiszemy go i uruchomimy jak prawdziwi programiści 🚀