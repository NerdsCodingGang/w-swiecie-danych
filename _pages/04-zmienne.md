---
title: 4. Zmienne
layout: post
---

Pisanie kodu w trybie interaktywnym jest dobre na start, jednak nie nadaje się do tworzenia większych programów. 

Przechodzimy więc do używania edytora. Otwórz swój Visual Studio Code i będziemy w nim pisać! 

Pisanie kodu w trybie interaktywnym jest dobre na start, jednak nie nadaje się do tworzenia większych programów. Przechodzimy więc do używania edytora.

Niestety, normalne edytory tekstu (właściwie procesory tekstu) jak Microsoft Word, Apple Page czy Google Docs nie nadają się do edycji kodu źródłowego strony web.

Nie używamy programu do edycji dokumentów tekstowych (np. Word), ponieważ tego typu programy zapisują do plików znacznie więcej informacji niż tylko czysty tekst. W formatach dokumentów pojawiają się niewidoczne dla nas informacje o formatowaniu treści (styl tekstu, czcionka, rozkład marginesów itp.) zbędnych dla pliku pisanego w html. Niektóre z edytorów owszem, pozwalają na zapisanie pliku na potrzeby webowe, ale wynik będzie daleki od oczekiwanego.

![VSC]({{ site.baseurl }}/assets/vsc-python.png){:title="VSC wtyczka Python" class="img-responsive"}
Program, którego potrzebujesz to edytor tekstu lub edytor kodu. Na start polecamy przyjazny początkującym program VSC.

Na pulpicie (lub w dowolnej innej lokalizacji) utwórz folder dla dzisiejszych zajęć o nazwie `python_od_podstaw`.

Otwórz edytor. Wybierz Open > twój folder. Utwórz nowy plik z rozszerzeniem `.py`

---

W poprzednim rozdziale pisałyśmy proste działania matematyczne, np. `33 + 5`.  
Ale co, jeśli chcemy tego samego działania użyć kilka razy?  
Wpisywanie wszystkiego od nowa byłoby niewygodne i mało czytelne.  
Na szczęście mamy **zmienne**!

## Co to jest zmienna?

Zmienna to „etykietka” dla jakiejś wartości.  
Możemy jej nadać nazwę, pod którą przechowamy liczby, teksty lub inne dane, i potem używać tej nazwy wielokrotnie.

Przykład:
```python
 wynik = 33 + 5
```
W tym przypadku:

- `wynik` to nazwa naszej zmiennej,
- `33 + 5` to wartość, którą przypisujemy,
- po wykonaniu tej linii `wynik` **zawiera wartość 38**.

Sprawdźmy:
```python
print(wynik)
```
Python wypisze:

    38

---

## Ważne zasady:

- W Pythonie po prostu piszemy `nazwa = wartość`
- Nazwy zmiennych nie mogą zawierać spacji ani zaczynać się od cyfry
- Warto, żeby były **opisowe**, np. `cena`, `dlugosc_trasy`, `suma_punktow`
- Pamiętaj tez, ze programiści piszą kod po angielsku

---

## Zmienne można nadpisywać

Zmienna nie musi mieć tej samej wartości przez cały czas.  
Możemy przypisać nową wartość:
```python
wynik = 99
print(wynik)
```

Efekt:

    99

---

## Czy w Pythonie są stałe?

Python nie ma specjalnego słowa kluczowego dla stałych (jak `const` w JavaScript).  
Ale przyjętą konwencją jest pisanie nazw stałych WIELKIMI_LITERAMI:

    PI = 3.14159

Technicznie – można ją nadpisać:

    PI = 5  # Python nie pokaże błędu

Ale to **nie jest zalecane**. Duże litery to umowa: „nie zmieniam tej wartości”.

---

## Zadanie 🎯

1. Utwórz dwie zmienne: `a` i `b`, np.:
```python
a = 10
b = 5
```

2. Wypisz ich sumę:
```python
print(a + b)
```
3. Nadpisz jedną z nich i wypisz sumę ponownie:

    a = 100
    print(a + b)

4. Stwórz zmienną `PRZELICZNIK = 1.2` i **nie zmieniaj jej wartości** – to będzie Twoja stała.
5. Policz ile a+b wynosi pomonozone przez przelicznik? 


#### Zapamiętaj:
Zmienna to po prostu sposób na zapamiętanie czegoś w programie.  
Dzięki nim nasz kod będzie **bardziej czytelny**, **krótszy** i **łatwiejszy do modyfikacji**.


W kolejnym kroku poznamy **typy danych** – czyli co dokładnie możemy przechowywać w zmiennych 🧠


