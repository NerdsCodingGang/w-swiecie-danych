---
title: 11. Projekt grupowy
layout: post
---

Czas na wspólne wyzwanie! 
W małych grupach przygotujcie **prosty model uczenia maszynowego**, który spróbuje przewidzieć pewną cechę utworu.  
To Wasz pierwszy mini-projekt ML-owy.

---

## 👉 Cel zadania

Każda grupa:
- wybiera jedno pytanie badawcze,  
- trenuje prosty model ML na danych Spotify,  
- sprawdza wynik (np. R² lub accuracy),  
- tworzy wizualizację i krótki opis wniosków (2–3 zdania).

## 👉 Propozycje zadań

Każda grupa może wybrać jeden z poniższych kierunków:

| Typ zadania | Przykładowe pytanie | Model do użycia | Co przewidujemy |
|--------------|--------------------|-----------------|-----------------|
| **Regresja liniowa** | Czy można przewidzieć popularność na podstawie energii i taneczności? | `LinearRegression()` | `popularity` |
| **Regresja wielowymiarowa** | Czy kilka cech naraz (np. tempo, energia, taneczność) lepiej przewiduje popularność niż jedna? | `LinearRegression()` | `popularity` |
| **Klasyfikacja (binarny podział)** | Czy na podstawie energii można rozpoznać, czy utwór jest popularny (np. powyżej 70 pkt)? | `LogisticRegression()` | `popular / niepopular` |
| **Klasyfikacja gatunku (opcjonalnie)** | Czy na podstawie energii i taneczności można odgadnąć gatunek muzyki? | `DecisionTreeClassifier()` | `track_genre` (tylko kilka gatunków) |



## 👉 Narzędzia, które wykorzystacie

- `scikit-learn` – do budowy modeli (`LinearRegression`, `LogisticRegression`, `DecisionTreeClassifier`)  
- `matplotlib` – do tworzenia wykresów porównawczych (np. przewidywana vs rzeczywista popularność)


## 👉 Przebieg pracy

1️⃣ **Przygotuj dane**  
   Wybierz tylko potrzebne kolumny i usuń brakujące wartości.  
   > .dropna()

2️⃣ **Podziel dane na wejście i wyjście**  

3️⃣ **Zbuduj i wytrenuj model**  

4️⃣ **Sprawdź wynik modelu (score)**  

5️⃣ **Zrób wykres porównawczy**  
   Na osi X mogą być rzeczywiste wartości, a na osi Y – przewidywane przez model.  
   `plt.scatter(y, model.predict(X), alpha=0.5)`

---

## 👉 Dla ambitnych grup

Spróbujcie porównać dwa modele na tych samych danych, np.  
`LinearRegression` i `DecisionTreeRegressor`.  

Wypiszcie ich wyniki (`R²`) i sprawdźcie, który lepiej dopasowuje dane.  
```
print(model1.score(X, y))  
print(model2.score(X, y))
```

## 👉 Prezentacja wyników

Każda grupa przygotowuje:
- tytuł projektu i pytanie badawcze,  
- krótki opis modelu (jakie dane, jaki typ modelu),  
- 1–2 wykresy,  
- krótkie wnioski (2–3 zdania: co odkryliście, co zaskoczyło, co można by poprawić).


## 👉 Dla prowadzących

Jeśli grupy skończą wcześniej, można je poprosić o:
- porównanie różnych cech wejściowych,  
- zmianę modelu z `LinearRegression` na `DecisionTreeClassifier`,  
- opisanie, dlaczego model się myli lub co mogłoby poprawić wyniki.

## 👉 Jak ocenić działanie modelu

W zależności od rodzaju modelu, używamy różnych miar jakości:

| Typ modelu | Co przewiduje | Miara jakości | Co oznacza |
|-------------|----------------|----------------|-------------|
| **Regresja (np. LinearRegression)** | Liczbę (np. popularność) | `R²` – współczynnik dopasowania | Jak dobrze linia opisuje dane; im bliżej 1, tym lepiej |
| **Klasyfikacja (np. LogisticRegression, DecisionTreeClassifier)** | Kategorię (np. popularny / niepopularny) | `accuracy_score` – dokładność klasyfikacji | Jaki procent przypadków model odgadł poprawnie |

---

## 👉 (opcjonalnie) 

Każda grupa pokazuje swój notebook w Colabie i opowiada:
> „Co chcieliśmy sprawdzić?”  
> „Jak to zrobiliśmy?”  
> „Co wyszło?”  
> „Co byśmy poprawili następnym razem?”


![magic]({{ site.baseurl }}/assets/magic.gif){:title="magic" class="img-responsive"}
