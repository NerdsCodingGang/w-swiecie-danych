---
title: 7. Filmy 🎬
layout: post
---

Do tej pory pracowaliśmy wspólnie na danych ze Spotify.  
Teraz czas, byś sprawdzić się w pracy samodzielnej.  
W tym rozdziale użyjemy nowego zbioru danych o filmach ma około 1000 wierszy i kilka prostych kolumn.  
To idealny zestaw, żeby poćwiczyć czyszczenie danych.

Pobierz dane z [Kaggle](https://www.kaggle.com/datasets/harshitshankhdhar/imdb-dataset-of-top-1000-movies-and-tv-shows/data)
lub naszego repozytorium na githubie [folder data](https://github.com/NerdsCodingGang/w-swiecie-danych/tree/main/data)

Zestaw danych `movies_sample.csv` pochodzi z publicznych danych i został uproszczony na nasze potrzeby.

---

## Wczytaj dane

Spróbuj samodzielnie wczytać dane do Colaba. Najlepiej utwórz nowy notatnik Colab.  
Nie kopiuj wszystkiego z poprzednich rozdziałów – przypomnij sobie, jak to było robione.

```python
import pandas as pd

url = "path"  
df = pd.read_csv(url)
```

Zobacz kilka pierwszych wierszy:

> df.head()

---


## 👉 Co to właściwie jest EDA?

Zanim zaczniemy cokolwiek przewidywać, trenować modele i sprawdzać wyniki, musimy zrobić jedną ważną rzecz: **poznać dane**.  
Tak zupełnie zwyczajnie spokojnie je obejrzeć, przejrzeć tabelę, sprawdzić, co tam się dzieje.

Ten proces nazywamy **EDA – Exploratory Data Analysis**, czyli eksploracją danych.

Możesz wyobrazić to sobie jak pierwsze spotkanie z nową osobą.  
Nie pytasz jej od razu na dzień dobry o najgłębsze sekrety.  
Najpierw patrzysz, kim jest, o czym opowiada, jak się przedstawia... i dokładnie tak samo robimy z danymi.

---

## 👉 Po co robić EDA?

EDA pomaga odpowiedzieć na podstawowe pytania:

- **Co znajduje się w zbiorze?**  
  Ile jest kolumn, jakie mają nazwy, jakie typy danych.

- **Czy coś wymaga naprawy?**  
  Braki danych, dziwne wartości, przecinki w liczbach, błędne daty.

- **Jak wyglądają rozkłady wartości?**  
  Czy oceny filmów mieszczą się między 1 a 10?  
  Czy długości filmów są podobne, czy bardzo różne?

- **Czy widać jakieś ciekawe zależności?**  
  Czy filmy z większą liczbą głosów mają wyższe oceny?  
  Czy dramaty są dłuższe niż komedie?  
  Czy oceny krytyków (Meta_score) pokrywają się z oceną widzów (IMDb)?

To wszystko pomaga Ci **zrozumieć, z czym pracujesz**, zanim przejdziesz dalej.

---

## 👉 Jak wygląda EDA w praktyce?

Najpierw oglądamy dane:
- kilka pierwszych wierszy,  
- podgląd typów danych (np. liczba, tekst),  
- podsumowanie statystyk (`describe()`),  
- liczbę braków (`isnull().sum()`).

Potem zadajemy dane pierwsze, drobne pytania:
- które gatunki pojawiają się najczęściej?  
- jaki jest najdłuższy film w zestawieniu?  
- czy w kolumnie `Gross` nie ma przypadkiem przecinków? (tak, ma 😉)  
- jak wyglądają oceny IMDb — czy większość filmów ma 7–8, czy może jakieś skrajności?

A na końcu pojawiają się **pierwsze wykresy**:
- histogram czasu trwania filmów,  
- ranking gatunków,  
- zależność liczby głosów od oceny,  
- porównanie Meta_score i IMDb Rating na scatterze.

Nic wielkiego.  
Nic jeszcze „smart”.  
Po prostu... patrzenie na dane.

---

## 👉 Dlaczego to jest takie ważne?

Bo model uczenia maszynowego — nawet najprostszy — nie zrobi za Ciebie „magii”,  
jeśli na wejściu dostanie:
- błędne typy danych,  
- brakujące wartości,  
- tekst zamiast liczb,  
- albo kolumny, które są niepotrzebne.

EDA chroni Cię przed błędami, które później kosztują najwięcej czasu.

To trochę jak generalne rozeznanie:  
„Zanim zacznę przewidywać oceny filmów, sprawdźmy, czy te oceny w ogóle mają sens.”

---

## 👉 Najważniejsze, co warto zapamiętać

EDA to:
- **poznawanie danych**,  
- **sprawdzanie jakości**,  
- **zadawanie pierwszych pytań**,  
- **proste wykresy**,  
- **budowanie intuicji**.

I dopiero kiedy wiesz, z czym masz do czynienia, możesz przejść do kolejnego etapu:  
czyli zbudowania swojego pierwszego modelu ML na danych filmowych.

W kolejnym rozdziale dokładnie to zrobimy.

---

## Pierwsze sprawdzenie

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

## Braki danych

Sprawdź, ile danych brakuje w każdej kolumnie (`df.isna().sum()`)

Jeśli chcesz usunąć wiersze, w których brakuje ważnych informacji (np. brak tytułu lub oceny), możesz użyć:

```python
df = df.dropna(subset=["title", "rating"])  
```

Teraz zobacz, czy liczba braków się zmniejszyła (`df.isna().sum()`)

---

## Konwersja typów

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
