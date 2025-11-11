---
title: 7. Dane wejściowe i teksty
layout: post
---

Do tej pory wpisywaliśmy dane bezpośrednio w kodzie – np. `name = "Rita"`.

Ale co, jeśli chcemy zapytać użytkownika o imię lub wiek?  
Tu z pomocą przychodzi funkcja `input()`.


## Funkcja input()

🧾 Funkcja `input()` pozwala pobrać dane od użytkownika w trakcie działania programu.

Przykład:
```python
    print("Tu wpisz swoje imię: ")
    name = input()
```

Po uruchomieniu kodu Python zatrzyma się i poczeka, aż wpiszesz coś z klawiatury.  
Wpisany tekst zostanie przypisany do zmiennej `name`.

Można to też zapisać krócej:


    age = input("Ile masz lat? ")
    print("To już", age, "lat!")



### 🧪 Zadanie

Czy możesz dołączyć do szkoły magii?
Stwórz program, który sprawdzi, czy użytkownik spełnia wiekowe kryteria przyjęcia do szkoły magii 🏰

1. Przypisz swoje imię do zmiennej `my_name`  
2. Przypisz swoje nazwisko do `my_surname`  
3. Połącz imię i nazwisko w zmienną `full_name`  
4. Zapytaj użytkownika o jego imię i wiek (za pomocą `input()`)  
5. Wyświetl powitanie z imieniem użytkownika  
6. Sprawdź, czy użytkownik ma do 17 lat włącznie  
7. Wypisz:  
   `You can join the school of magic: True`  
   lub  
   `You can join the school of magic: False`


![]({{ site.baseurl }}/assets/albus.gif)

## Indeksowanie znaków

Każdy ciąg znaków w Pythonie (czyli `str`) ma swoje **indeksy** – numerację od 0.  
Dzięki temu możemy „wyciągać” pojedyncze litery lub fragmenty tekstu.
Jest to tzw. indeksowanie. 


![Indeksowanie]({{ site.baseurl }}/assets/step-3b.png){:title="Indeksowanie sekwencji" class="img-responsive"}

```
>>> seq = "Monty Python"
>>> print(seq[0])
>>> print(seq[1])
>>> print(seq[2])

>>> print(seq[6:10]) # przycinanie
Pyth

>>> print(seq[-1])
>>> print(seq[-2])

>>> print(seq[-12:-7])
Monty
```

Przycinanie obywa się wg. wzoru: `[start:stop:krok]` albo `[-od_tylu]`
# zawsze od zera!

Przeanalizuj kolejne linie kodu, każdą wyświetl:

```python
cool_string = "The quick brown fox jumped over the lazy dog"

# sprawdź długość - liczbę znaków
length = len(cool_string)  # 44

index0 = cool_string[0]  # litera: 'T'
index5 = cool_string[5]  # litera: 'u'

# znajdź ostatnią literę
index_last = len(cool_string) - 1 # dlaczego musmy odjąć 1?
last_char = cool_string[index_last]  # litera: 'g'

cool_slice_to_end = cool_string[4:]  # 'quick brown fox jumped over the lazy dog'

reversed_string = cool_string[::-1]  # odwraca kolejność liter
```

### 🧪 Zadanie

1. Stwórz zmienną z tekstem:

        "Words are, in my not-so-humble opinion, our most inexhaustible source of magic. Capable of both inflicting injury, and remedying it."

2. Znajdź:
   - pierwszą literę
   - piątą literę
   - ostatnią literę na dwa sposoby (użyj długości jak i indeksowania znaków)
   - odwrócony ciąg 
   - długość napisu

---

## 🔄 Konwersja typów

Funkcja `input()` zawsze zwraca **tekst (`str`)**, nawet jeśli wpiszesz liczbę.
```python
    number = input("Wpisz tu 3: ")
    print(3 == number)         # False!
    print(type(number))        # <class 'str'>
```
Aby porównać z liczbą, musimy przekonwertować dane:
```
    number = int(number)
    print(3 == number)         # True
```
---

## 🧪 Przetestuj

1. Stwórz zmienne:
```python
        a = 20
        c = "30"
```
2. Spróbuj:
```python
        print(a + c)      # Błąd!
```
3. Napraw to:
```python
        c = int(c)
        print(a + c)
```
4. Zamień `c` na `float` i dodaj z `a`

Patrząc na te przykłady... na czym polega konwersja typów? 

### 🔎 Mini projekt: czyszczenie tekstu

Stwórz zmienną z tekstem:
```
    txt = "Happiness can be found even in the darkest of times, if one only remembers to turn on the light."
```

**Możesz skorzystać z Google, nie pytaj jednak o rozwiązanie AI - spróbuj ruszyć głową!** 💡 


1. Wyświetl długość tekstu (liczbę znaków)  
2. Wyświetl pierwszą i ostatnią literę tekstu  
3. Wytnij słowo `"light"` za pomocą indeksowania  
4. Usuń z tekstu wszystkie litery `"a"`  
5. Zastąp przecinki (`,`) kropkami (`.`)  
6. Sprawdź, na której pozycji pojawia się pierwsze wystąpienie litery `"e"`  
7. Policz, ile razy litera `"o"` występuje w tekście  
8. Zamień wszystkie litery na wielkie  
9. Odwróć cały ciąg znaków  
10. Utwórz nową zmienną `txt_clean`, w której:
    - nie ma żadnych przecinków,  
    - by w tekście kazde słowo zaczynało się z duzej litery,  
    - kończy się wykorzyknikiem (nawet jeśli wcześniej go tam nie było)  
11. Sprawdź, czy tekst zawiera słowo `"darkest"`  
12. Podziel tekst na wyrazy i zapisz je jako listę

💡 Pamiętaj, że możesz tworzyć zmienne pomocnicze, by nie nadpisywać `txt`.

---

W kolejnej lekcji nauczymy się podejmować decyzje w kodzie – czyli jak powiedzieć Pythonowi:  
*„jeśli użytkownik wpisał więcej niż 18 – wyświetl >>Możesz wejść<<”*  
Czas na `if`, `else` i instrukcje warunkowe!
