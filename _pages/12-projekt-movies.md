---
title: 12. Modelowanie na danych filmowych
layout: post
---

Tym razem znowu przeskoczymy z muzyki do świata filmu.  
Pamiętacie nasz **zbiór danych — TOP 1000 filmów z IMDb**? Wracamy do niego! Spróbujcie zbudować prosty model, który przewidzi pewną cechę filmu.

Dane są większe, ciekawsze i bardziej zróżnicowane niż Spotify, więc czeka Was trochę więcej myślenia i szukania… ale właśnie o to chodzi 😊

---

## 👉 Skąd pobrać dane

Możesz pobrać plik z:
- Kaggle: https://www.kaggle.com/datasets/harshitshankhdhar/imdb-dataset-of-top-1000-movies-and-tv-shows/data  
- naszego repozytorium GitHub: https://github.com/NerdsCodingGang/w-swiecie-danych/tree/main/data

Plik ma nazwę:
- `imdb_top_1000.csv`

---

## 👉 Jak wyglądają dane?

Jaką komendą sprawdzisz co zawierają dane?

W środku znajdziesz między innymi:

- **Series_Title** – tytuł filmu  
- **Released_Year** – rok  
- **Duration** – czas trwania (w minutach)  
- **Genre** – gatunek (czasem 2–3 w jednej komórce)  
- **IMDB_Rating** – ocena IMDb  
- **Meta_score** – ocena krytyków  
- **Director**  
- **Stars** (4 aktorów/aktorek)  
- **No_of_Votes** – liczba głosów  
- **Gross** – przychód  
- **Number_of_Movies** – zawsze 1 (nie używać)

To idealny zbiór, żeby robić **predykcję ocen filmów, analizę gatunków albo popularności**.

---

## 👉 Cel projektu

Grupa:
- wybiera 1-2 pytania badawcze,  
- buduje prosty model ML na danych filmowych,  
- ocenia wynik (`R²` lub `accuracy`),  
- tworzy wykres(y),  
- pisze krótkie wnioski (2–3 zdania).

Tak, to zadanko jest **analogiczne** do poprzedniego projektu ze Spotify,  
ale tym razem sami musicie sobie przypomnieć *jakich funkcji użyć*  lub dopytać osoby mentorskiej 😉

---

## 👉 Propozycje zadań (do wyboru)

Poniżej masz 4 kierunki — wszystkie realne i do zrobienia w ok. 45–60 minut.

| Typ zadania | Pytanie badawcze | Model | Co przewidujemy |
|--------------|------------------|--------|-----------------|
| **Regresja liniowa** | Czy na podstawie **czasu trwania** i **liczby głosów** można przewidzieć ocenę IMDb? | `LinearRegression()` | `IMDB_Rating` |
| **Regresja wielocechowa** | Czy połączenie: czas trwania + rok premiery + Meta_score daje lepsze przewidywanie oceny? | `LinearRegression()` | `IMDB_Rating` |
| **Klasyfikacja (popularny / niepopularny)** | Czy na podstawie liczby głosów można odgadnąć, czy film jest „popularny”? (np. `No_of_Votes > median` → 1, inaczej 0) | `LogisticRegression()` | kategoria 0/1 |
| **Klasyfikacja gatunku (uproszczona)** | Czy na podstawie oceny i Meta_score da się rozpoznać gatunek? (wybierzcie tylko 3 gatunki!) | `DecisionTreeClassifier()` | `Genre` (tylko 3 wybrane gatunki) |

---

## 👉 Przebieg pracy 

Znowu, jeśli coś wydaje się nie jasne, wróć do poprzedniego, 11 rozdziału z muzyką! 

1️⃣ **Wczytaj dane do ramki `df`**  
    (użyj funkcji z poprzedniej lekcji, celowo nie dajemy jej tutaj — macie sobie przypomnieć 😉)

2️⃣ **Oczyść podstawowe kolumny**
- usuń brakujące wartości  
- usuń przecinki np. z kolumny `Gross` i zamień na liczbę  
- jeśli potrzebujesz: rozdziel gatunki po przecinku

3️⃣ **Wybierz interesujące kolumny**  
   Przykład zestawu (do regresji):
   - `IMDB_Rating`  
   - `Duration`  
   - `Meta_score`  
   - `No_of_Votes`  

4️⃣ **Podziel dane na X i y**  
   👉 X – kolumny wejściowe  
   👉 y – kolumna, którą przewidujemy  

5️⃣ **Zbuduj i wytrenuj model (`fit`)**

6️⃣ **Sprawdź wynik modelu (`score`)**  
   - regresja → `R²`  
   - klasyfikacja → `accuracy_score`

7️⃣ **Zrób wykres porównawczy**  
   Przykład, który możesz odtworzyć:
   - scatter: rzeczywista ocena vs przewidywana  
   - barh: 10 filmów, gdzie model pomylił się najbardziej  

8️⃣ **Napisz krótkie wnioski**  
   👉 Co model przewidział dobrze?  
   👉 Gdzie się myli?  
   👉 Jaka cecha okazała się najważniejsza?

---

## 👉 Wskazówki 

bez gotowych rozwiązań!!!

- Jeśli model „wariuje” – sprawdź typy danych (`dtype`).  
- Kolumny tekstowe trzeba pominąć lub zakodować — nie używaj ich bez obróbki.  
- Liczba głosów (`No_of_Votes`) ma **dużo większą skalę** niż inne – możesz użyć logarytmu.  
- Możesz porównać film z największym przychodem (`Gross`) z filmem o najwyższym ratingu — często to nie to samo!  


---

## 👉 Gotowe!


