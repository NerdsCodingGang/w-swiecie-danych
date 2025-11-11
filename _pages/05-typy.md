---
title: 5. Typy danych
layout: post
---

Zanim pójdziemy dalej, musimy zrozumieć jeszcze jedną rzecz. Dane mają swój TYP czyli Python wie czy dane wartości to liczby a może tekst. Do tej pory pracujemy ze zmiennymi w kolumnach zawierającymi liczby, a przynajmniej tak się nam wydawało. Ale Python – podobnie jak inne języki – obsługuje różne **typy danych**.

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


### Zadanie 🎯

1. Stwórz zmienną `hello` z tekstem `"Hello, [TwojeImię]!"`  a następnie te zmienną wyświetlisz 10 razy.
2. Użyj metody `.replace()`, aby zamienić swoje imię na `"Python"`  
3. Wypisz wynik na ekranie

---

## 🔢 Sprawdź typ kolumny

Najprostszy sposób, by dowiedzieć się, jakie dane są w danej kolumnie, to sprawdzenie jej **typu**.

```python
df["tempo"].dtype
```

`df` to cały nasz zbiór danych (ramka danych).  Możesz też użyć `df_small`, jeśli wcześniej tworzyliśmy mniejszy zestaw:

```python
df_small["tempo"].dtype
```

Jeśli wynik to coś w rodzaju **float64** lub **int64**, oznacza to, że kolumna zawiera liczby.  
`int` to liczby całkowite, a `float` to liczby z przecinkiem (tak zwane liczby zmiennoprzecinkowe).

Jeśli natomiast wynik to **object** lub **string**, oznacza to, że w kolumnie są teksty albo **wartości mieszane**,  
na przykład liczby zapisane jako tekst.

Spróbuj też sprawdzić typ kolumny, w której są nazwy utworów:

```python
df_small["track_name"].dtype
```

Zobaczysz, że ta kolumna ma typ **object**, co jest spodziewane, bo wiemy, że zawiera dane tekstowe.

---

## 🧮 Sprawdź, czy wszystkie wartości są liczbowe

Czasem kolumna wygląda na liczbową, ale nie wszystkie wartości naprawdę są liczbami.  
Na przykład ktoś mógł wpisać słowo zamiast liczby albo zostawić puste pole.  

Możesz to sprawdzić w prosty sposób:

```python
pd.to_numeric(df_small["tempo"], errors="coerce").notna().all()
```

Jeśli wynik to **True**, oznacza to, że wszystkie wartości da się odczytać jako liczby.  
Jeśli **False**, to znaczy, że w tej kolumnie znajdują się jakieś niepoprawne wpisy (np. tekst albo brak danych).

Spróbuj też sprawdzić kolumnę, w której są nazwy utworów:

```python
pd.to_numeric(df_small["track_name"], errors="coerce").notna().all()
```

Tutaj wynik powinien być **False**, bo nazwy utworów to tekst, a nie liczby.

---

💡 Yup!
Dzięki tym dwóm prostym sposobom możesz łatwo sprawdzić, które kolumny są liczbowe, a które tekstowe.  
A to już jest przydatne przed kolejnymi etapami, takimi jak liczenie średnich, grupowanie danych czy tworzenie wykresów. Lepiej upewnić się wcześniej, że typ jest liczbowy, niż później dostać błędy, bo Python nie będzie chciał zrobić np. średiej z typów mieszanych (bo przecież jak zrobić średnią z `5, 2, 4, pies i True`?)

