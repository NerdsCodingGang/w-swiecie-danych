---
title: 5. Typy danych
layout: post
---

Do tej pory pracowałyśmy ze zmiennymi zawierającymi liczby. Ale Python – podobnie jak inne języki – obsługuje różne **typy danych**.

Typ danych określa, **jakiego rodzaju wartość** przechowujemy w zmiennej.  
Spójrzmy na najczęściej używane:

---

## Podstawowe typy danych w Pythonie

- `int` – liczby całkowite, np. `7`, `-42`, `0`
- `float` – liczby zmiennoprzecinkowe, np. `3.14`, `2.0`
- `str` – tekst, czyli ciąg znaków (ang. *string*), np. `"Python"` albo `'Hello!'`
- `bool` – zmienne logiczne: `True` lub `False`
- `None` – specjalny typ oznaczający brak wartości (odpowiednik `null`)


## Jak sprawdzić typ zmiennej?

W Pythonie służy do tego funkcja `type()`:

```python
    liczba = 42
    print(type(liczba))  # <class 'int'>

    tekst = "Cześć!"
    print(type(tekst))   # <class 'str'>
```


## Przykład: Twoje imię i jego typ

Stwórz zmienną ze swoim imieniem:
```python
    name = "Ala"
    print(name)
    print(type(name))
```

Wynik będzie:

```
    Ala
    <class 'str'>
```

## Operacje na liczbach

Python umożliwia wykonywanie działań matematycznych podobnie jak kalkulator:

```python
    a = 8
    b = 4

    print(a + b)   # dodawanie
    print(a - b)   # odejmowanie
    print(a * b)   # mnożenie
    print(a / b)   # dzielenie
    print(a % 3)   # reszta z dzielenia
    print(a ** 2)  # potęgowanie
```

📌 W Pythonie nie używamy `++` ani `--` – zamiast tego robimy np. `a = a + 1`


## Operacje na tekstach (stringach)

Teksty możemy **łączyć** (nazywa się to konkatenacją):

```python
    first_name = "Ala"
    last_name = "Nowak"
    full_name = first_name + " " + last_name
    print(full_name)  # Ala Nowak
```

### Długość tekstu

Aby sprawdzić, ile znaków ma tekst, używamy `len()`:

```python
    print(len(full_name))  # 9
```

### Zmiana wielkości liter
```python
    print(full_name.upper())   # ALA NOWAK
    print(full_name.lower())   # ala nowak
```


### Szukanie fragmentu tekstu
```python
    print(full_name.find("a"))      # 1 – pierwsza litera "a"
    print(full_name.find("xyz"))    # -1 – brak wyniku
```


### Zamiana fragmentu tekstu
```python
    powitanie = "Hello, Ala!"
    nowe = powitanie.replace("Ala", "Python")
    print(nowe)  # Hello, Python!
```


## Zadanie 🎯

1. Stwórz zmienną `hello` z tekstem `"Hello, [TwojeImię]!"`  
2. Użyj metody `.replace()`, aby zamienić swoje imię na `"Python"`  
3. Wypisz wynik na ekranie


### Dokumentacja 

Zajrzyj do dokumentacji - metody String. Możesz skorzystać z Google, nie pytaj jednak o rozwiązanie AI - spróbuj ruszyć głową!

{% include bookmark.html 
    url="https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str"
    title="Text Sequence Type – str"
    desc="Dokumentacja typu tekstowego w Pythonie"
%}

- Utwórz zmienną, która będzie przechowywać imię pupila, a następnie wyświetl informację "Pogłaszcz {imie_pupila}, ucieszy się".
- Zapisz swoje imię i nazwisko do dowolnej zmiennej. Ile znaków ma Twoje imię i nazwisko?
- Zmień wszystkie litery imienia i nazwiska na drukowane.
- Jaką metodą usunąć z ciągu znaków “Programujemy w Pythonie” literę a?
- ⭐ W jaki sposób zamienić ciąg znaków “123” na liczbę 123?


## 🧙 Zadanie: Ile pieniędzy zabrać do Hogsmeade?

> "The gold ones are Galleons. Seventeen silver Sickles to a Galleon and twenty-nine Knuts to a Sickle, it's easy enough."

Czy zastanawialiście się kiedyś, ile złotówek musielibyście zabrać do Hogsmeade, żeby zrobić tam zakupy?
W książce *„Quidditch przez wieki”* (wyd. Media Rodzina) sugerowana cena to 10 złotych, a obok podano 9 sykli i 7 knutów.  
Na tej podstawie oszacowano wartość czarodziejskiej waluty:

- 🟤 **1 knut ≈ 0,04 zł (4 grosze)**  
- ⚪ **1 sykl = 29 knutów = 1,16 zł**  
- 🟡 **1 galeon = 17 sykli = 19,72 zł**



Na tej podstawie odpowiedz na poniższe pytania:

**Zadania**

1. Ile zapłacisz w złotówkach za różdżkę, która kosztuje **7 galeonów**?

2. Ile kosztuje w złotówkach **gazeta** za **25 knutów**?

3. Jaką wartość ma **nagroda 700 galeonów**, którą wygrała rodzina czarodziejów w przeliczeniu na PLN?

4. Masz do dyspozycji **350 złotych**. Ile czarodziejskich monet możesz za to otrzymać, rozmienione od największych (najpierw galeony, potem sykle, na końcu knuty)?
   - Wynik podaj w formacie: **X galeonów, Y sykli, Z knutów**
   - Oblicz też, ile Ci zostanie (**reszta** w złotych).


```python
# wartości walut w złotówkach
wartosc_knuta = 0.04
wartosc_sykla = ...
wartosc_galeona = ...

# 🪄 1. Cena różdżki 
rozdzka_cena = 
print("Cena różdżki: ... zł")

# 🗞️ 2. Cena gazety


# 🏆 3. Nagroda 

# 💰 4. Masz 350 zł – ile to galeonów, sykli i knutów?

# najpierw liczymy galeony

# potem sykle

# na końcu knuty

print("Za 350 zł dostaniesz:")
print( "X galeonów,", "Y sykli,", "Z knutów")

# reszta w złotówkach
print("Reszta: ... ")

```