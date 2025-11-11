---
title: 8. Instrukcje warunkowe
layout: post
---


**Czy program może podejmować decyzje?**
Tak, ale decyzja zależy od tego, co... mu powiemy.
Niektóre rzeczy dzieją się tylko wtedy, gdy zostanie spełniony konkretny warunek.  
Na przykład: woda wrze, gdy osiągnie 100°C, a drzwi otwierają się, gdy masz klucz.  

W programowaniu jest podobnie – dzięki instrukcjom warunkowym mówimy Pythonowi: *„Zrób coś, jeśli…”*.

Na przykład:
```python
if temperatura > 100:
    print("Woda się gotuje!")
```
Komputer nie wie, czym jest wrzątek – ale potrafi porównać liczby i wykonać kod, jeśli spełniony jest warunek.


## Logika w kodzie 🧠

W Pythonie warunki zapisujemy za pomocą `if`, `elif` i `else`.  
To trzy słowa kluczowe, które pozwalają sterować przebiegiem programu i decyzjami jakie podejmiemy

### `if` 

– sprawdza, czy warunek jest spełniony:

```python
age = 16

if age < 18:
    print("Jesteś niepełnoletni/a")
```

### `elif` 

– sprawdzany tylko wtedy, gdy wcześniejszy warunek był fałszywy:

```python
if age < 12:
    print("Jesteś dzieckiem")
elif age < 18:
    print("Jesteś nastolatkiem")
```

### `else` 

– wykonuje się tylko wtedy, gdy **żaden poprzedni warunek nie był spełniony**:

```python
if age < 12:
    print("Jesteś dzieckiem")
elif age < 18:
    print("Jesteś nastolatkiem")
else:
    print("Jesteś dorosły/a")

print("A to juz dalsza część programu")
```

### Wcięcia mają znaczenie!

📌 Jeśli znasz inne języki programowania, zauważysz, że Python **nie używa nawiasów klamrowych `{}` jak JavaScript czy C++**.  
Tutaj **wcięcia (indentacja)** określają, które instrukcje należą do jakiego bloku kodu.

> ##### WARNING
>
> Możesz używać **tabulacji** lub **czterech spacji**, ale nigdy obu naraz!  
> Trzymaj się jednej konwencji w całym pliku, inaczej Python zgłosi błąd.
{: .block-warning }

```
if warunek:
    # kod do wykonania jeśli warunek jest True
elif inny_warunek:
    # jeśli pierwszy nie działa, sprawdź ten
else:
    # jeśli żaden nie działa, wykonaj to
```
### Przetestuj! 🔎 

Przekopiuj poniszy kod i umieść go w nowym pliku, uruchom i zobacz jak działa

```python
score = int(input("Podaj wynik testu w %: "))

if score >= 90:
    print("Ocena: 6")
elif score >= 75:
    print("Ocena: 5")
elif score >= 60:
    print("Ocena: 4")
elif score >= 45:
    print("Ocena: 3")
else:
    print("Ocena: 2")
```

Nie ma co gadać, trzeba poćwiczyć!

### 🧪 Zadanie 1
Poproś użytkownika o dwie liczby. Sprawdź, która jest większa, albo czy są równe.

### 🧪 Zadanie 2 

Stwórz program, który działa jak formularz używany przez Biuro Spraw Uczniowskich w Twojej Szkole Magii 🪄

1. Zapytaj użytkownika o wiek (`input()`)
2. Na podstawie podanego wieku przypisz mu jedną z kategorii magicznych:

   - 0–6 lat → **Młody smok (maluch) - przyszły kandydat na czarodzieja** 🐣  
   - 7–12 lat → **Uczniak (dziecko)** 📚  
   - 13–18 lat → **Czarodziej w trakcie szkolenia** 🧙‍♀️  
   - 19+ → **Absolwent czyli pełnoprawny członek społeczności magicznej (dorosły)** 🎓

3. Wyświetl komunikat z przydziałem, np.:  
   `"Witaj! Twój status: Czarodziej w trakcie szkolenia."`

💡 Pamiętaj o konwersji typu (`int()`), bo dane z `input()` to zawsze tekst.

### 🧪 Zadanie 3 
Zapisz do zmiennej **tajną liczbę** (np. `7`) — to jak ukryta liczba w zaklęciu.  
Poproś użytkownika o zgadnięcie tej liczby, tak jakby próbował rzucić poprawne zaklęcie.

W zależności od odpowiedzi wyświetl:

- `"Zaklęcie za słabe!"` (jeśli liczba jest za mała)  
- `"Zaklęcie za potężne!"` (jeśli za duża)  
- `"Brawo! Trafiłeś dokładnie!"` (jeśli zgadł)


### ⭐️ Zadanie 4 
Rozszerzmy zadanie powyzej 🎩 Wylosuj (poszukaj biblioteki `random`) liczbę i zapisz do zmiennej.
Poproś użytkownika o zgadnięcie.
Wypisz `ciepło - czujesz magię` i `zimno - brrr!` w zależności od odpowiedzi.
- jeśli liczby są takie same → "Brawo! Trafiłeś dokładnie!" → zakończ program
- jeśli roznica mniejsze równe 2 → "Ciepło – czujesz magię!"
- jeśli roznica większe niz 2 → "Zimno – brrr!"

Poznaj wartosc bezwzględną `abs()` ;) 
