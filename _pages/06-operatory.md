---
title: 6. Operatory
layout: post
---

Python – jak każdy język programowania – pozwala nam wykonywać różne **operacje** na danych.  
Do tego służą **operatory** – czyli symbole takie jak `+`, `*`, `%`, `==`, itp.

W tej lekcji uporządkujemy sobie te symbole i pokażemy, do czego służą.


## 🔢 Operatory arytmetyczne

| Operator | Opis           | Przykład       | Wynik |
|----------|----------------|----------------|-------|
| `+`      | dodawanie      | `3 + 2`        | `5`   |
| `-`      | odejmowanie    | `7 - 5`        | `2`   |
| `*`      | mnożenie       | `4 * 3`        | `12`  |
| `/`      | dzielenie      | `8 / 2`        | `4.0` |
| `//`     | dzielenie całkowite | `7 // 2`  | `3`   |
| `%`      | reszta z dzielenia (modulo) | `5 % 2` | `1` |
| `**`     | potęgowanie    | `2 ** 3`       | `8`   |



## 🤔 Co to jest operator modulo `%`?

Może nie znasz go ze szkoły – ale jest bardzo przydatny!

Zwraca **resztę z dzielenia** jednej liczby przez drugą:
```python
    print(5 % 2)  # 1
    print(5 % 3)  # 2
    print(5 % 4)  # 1
    print(10 % 5) # 0
```

📌 Jeśli wynik to `0`, oznacza to, że liczba dzieli się bez reszty.


## 🧠 Ciekawostka: skąd `*` i `/` zamiast `×` i `÷`?

Na pierwszych klawiaturach komputerowych nie było symboli `×` ani `÷`.  
Dlatego programiści przyjęli umowne znaki:

- `*` zamiast mnożenia
- `/` zamiast dzielenia

To **dziedzictwo maszyn do pisania** – prosto z lat 60.!



## 🧪 Zadania z operatorami arytmetycznymi

1. Ile godzin ma rok?
2. Ile sekund ma dekada?
3. Ile skrzydeł mają dwanaście tuzinów ważek?

## 🔍 Operatory porównania

Te operatory pozwalają porównywać wartości:

| Operator | Znaczenie            | Przykład       | Wynik   |
|----------|----------------------|----------------|---------|
| `==`     | równe                | `5 == 5`       | `True`  |
| `!=`     | różne                | `5 != 3`       | `True`  |
| `>`      | większe              | `5 > 2`        | `True`  |
| `<`      | mniejsze             | `3 < 1`        | `False` |
| `>=`     | większe lub równe    | `3 >= 3`       | `True`  |
| `<=`     | mniejsze lub równe   | `4 <= 2`       | `False` |

Spróbuj:
```python
    print(23 + 3 == 15 + 12)   # False
    print(29 // 7 == 5)        # False
    print(27 % 8 == 3)         # True
```


## 🧠 Czy Python rozumie logikę?

Tak! W Pythonie mamy typ `bool`, który przyjmuje dwie wartości:

- `True` – prawda
- `False` – fałsz

Możesz je też porównywać:

```python
    print(True == True)     # True
    print(False < True)     # True
    print(False == 0)       # True
```

## Zadania logiczne 🎯

Niech python odpowie nam `True` or `False` 

1. Czy 5012 jest podzielne przez 4 bez reszty?
2. Czy `5 ** 2` to więcej niż `20 + 3`?
3. Czy długość imienia `"Kasia"` jest większa niż 4?