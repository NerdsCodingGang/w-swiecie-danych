---
title: 6. Filmy 🎬
layout: post
---

Do tej pory pracowaliśmy wspólnie na danych ze Spotify.  
Teraz czas, byś sprawdzić się w pracy samodzielnej.  
W tym rozdziale użyjemy nowego zbioru danych o filmach ma około 1000 wierszy i kilka prostych kolumn.  
To idealny zestaw, żeby poćwiczyć czyszczenie danych.

Pobierz dane z repozytorium na githubie https://github.com/NerdsCodingGang/w-swiecie-danych/tree/main/data

Zestaw danych `movies_sample.csv` pochodzi z publicznych danych i został uproszczony na nasze potrzeby.

---

## 📥 Wczytaj dane

Spróbuj samodzielnie wczytać dane do Colaba.  
Nie kopiuj wszystkiego z poprzednich rozdziałów – przypomnij sobie, jak to było robione.

```python
import pandas as pd

url = "path"  
df = pd.read_csv(url)
```

Zobacz kilka pierwszych wierszy:

> df.head()

---

## 🧭 Pierwsze sprawdzenie

Zanim zaczniesz sprzątać dane, upewnij się, że rozumiesz, co masz przed sobą.

> df.shape  
> df.columns  
> df.info()

Pamiętaj: jeśli widzisz typ **object**, to może oznaczać tekst lub liczby zapisane jako tekst.  
Zwróć też uwagę, czy w którejś kolumnie brakuje wartości.

Zredukuj wielkość do podstawowych informacji, by operować na mniejszej ramce danych

- tytuł filmu  
- rok premiery  
- gatunek  
- średnia ocena użytkowników  
- liczba głosów  
- długość filmu w minutach  

---

## 🕳️ Braki danych

Sprawdź, ile danych brakuje w każdej kolumnie (`df.isna().sum()`)

Jeśli chcesz usunąć wiersze, w których brakuje ważnych informacji (np. brak tytułu lub oceny), możesz użyć:

```python
df = df.dropna(subset=["title", "rating"])  
```

Teraz zobacz, czy liczba braków się zmniejszyła (`df.isna().sum()`)

---

## 🔢 Konwersja typów

Czasem kolumna zawiera liczby, ale zapisane są jako tekst.  
Spróbuj zmienić typ danych w kolumnie `year` lub `votes` aby mieć pewność, że są poprawne

```python
df["year"] = pd.to_numeric(df["year"], errors="coerce")  
df["votes"] = pd.to_numeric(df["votes"], errors="coerce")
```
Sprawdź wynik (`df.info()`)

Czy wszystko poszło dobrze? Jaki typ widzisz?

---

## 🔍 Filtrowanie danych

Spróbuj teraz znaleźć filmy z wybranym kryterium, na przykład te z oceną powyżej 8.

```python
df[df["rating"] > 8].head()
```

Możesz też spróbować:

```python
df[df["genre"] == "Action"].head()
```

Dzięki filtrowaniu możesz szybko wybrać tylko to, co Cię interesuje.

---

## Kolumny pochodne

Czasem warto dodać kolumnę, która coś ułatwi.  
Na przykład sprawdź, które filmy trwają ponad dwie godziny:

```python
df["long_movie"] = df["duration_min"] > 120 
```
Co zawiera kolumna `long_movie` ? 
```
df[["title", "duration_min", "long_movie"]].head()
```

Kolumna `long_movie` zawiera teraz wartości **True** lub **False** – to tzw. kolumna logiczna.  
Można jej potem użyć do liczenia lub grupowania.

---

W ramach analizy sprawdź, ile procent filmów to długie filmy. Jak duża część filmów trwa ponad dwie godziny?


```python
df["long_movie"].value_counts(normalize=True) * 100
```


### Zadanie 

~ dla Ciebie lub waszej grupy

Przypomnij sobie co robią `describe()`, `groupby()`, `value_counts()`, `mean()` itp.

1. Sprawdź, ile gatunków filmowych znajduje się w kolumnie `genre`.  
2. Policz średnią ocenę filmów w każdym gatunku?
3. Zastanów się, czy dłuższe filmy mają wyższe ocen?

Spróbuj zapisać swoje wnioski w komórce tekstowej w Colabie – nie kodem, tylko faktycznie zdaniami. To dobra praktyka przyszłych Data Scientistów.

---

🎉 Świetnie!  

Znasz już proces: wczytanie, sprawdzenie, czyszczenie, filtrowanie i tworzenie nowych kolumn.  
W następnym rozdziale zajmiemy się **wizualizacją danych** – czyli pokażemy te informacje na wykresach.
