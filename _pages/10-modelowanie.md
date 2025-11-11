---
title: 9. Pierwsze modelowanie danych
layout: post
---

Do tej pory poznaliśmy dane od środka: potrafisz je wczytać, oczyścić i opowiedzieć o nich historię.  
Teraz zobaczymy, jak komputer może **sam spróbować przewidzieć** pewne zależności w danych.

Tak zaczyna się **uczenie maszynowe (Machine Learning)**.

## Co znaczy modelowanie danych?

Modelowanie to nic innego jak **próba znalezienia wzoru**, który opisuje związek między danymi.  
Możemy to sobie wyobrazić jako **szukanie linii trendu**:  

> jeśli tempo utworu rośnie, to czy jego popularność też rośnie?

Model „uczy się” na podstawie przykładów, czyli z danych, a potem potrafi **przewidywać** wyniki dla nowych przypadków.  
Choć może brzmieć to trochę magicznie, w rzeczywistości to **matematyka zapisana w kodzie**.  

Model to nic innego jak **matematyczny wzór**, który próbuje znaleźć zależność między danymi wejściowymi a wynikiem.  
W naszym przykładzie — będzie szukał **linii najlepiej dopasowanej** do punktów opisujących relację między tempem utworu a jego popularnością.  

Najprostszy model do takiego zadania to **regresja liniowa**.

---

## Nasz cel

Zbudujemy najprostszy możliwy model: **regresję liniową**, czyli model, który przewiduje jedną liczbę na podstawie innej.

Spróbujemy odpowiedzieć na pytanie:


> Czy na podstawie tempa (`tempo`) można przewidzieć popularność (`popularity`) utworu?



### Krok 1. Przygotowanie danych

Najpierw wybierzemy tylko te kolumny, które są nam potrzebne:

```
df_model = df_small[["tempo", "popularity"]].dropna()
```

Polecenie `dropna()` usuwa wiersze, w których brakuje wartości.

Następnie podzielimy dane na:
- **X** – cechę (tempo),
- **y** – wartość, którą chcemy przewidywać (popularność).

```
X = df_model[["tempo"]]  
y = df_model["popularity"]
```


### Krok 2. Zbudowanie modelu

Do tworzenia modeli użyjemy biblioteki **scikit-learn**, która zawiera gotowe algorytmy ML.

```
from sklearn.linear_model import LinearRegression  

model = LinearRegression()
```

Nadal importujemy w pythonie, ale teraz nie cały sklearn a wybieramy konkretną rzecz, w nazym wypadku 
`LinearRegression()` to prosty model uczący się zależności w postaci linii prostej.

---

### Krok 3. Trenowanie modelu

Model musi się "nauczyć" na danych, czyli znaleźć najlepszą linię, która pasuje do naszych punktów.

```python
model.fit(X, y)
```

Po tej komendzie (nie powinna rzucić błędu) model jest już gotowy do przewidywania.

Jedna komenda? Owszem!
Trenowanie modelu polega na tym, że uczymy go rozpoznawać wzorce na podstawie przykładów.
Jak wspomnieliśmy, biblioteka `scikit-learn` zawiera wiele gotowych narzędzi, które pozwalają **łatwo stosować różne algorytmy uczenia maszynowego**.
Dostarczamy modelowi duży zbiór danych, w którym każda obserwacja ma przypisany wynik lub kategorię.
Model analizuje te dane i próbuje znaleźć zależności między nimi. Z czasem, dzięki powtórzeniom i korektom błędów, uczy się samodzielnie przewidywać wyniki dla nowych, nieznanych wcześniej danych. W skrócie: trening to proces, w którym model przekształca dane w wiedzę.


### Krok 4. Przewidywanie wartości

Sprawdźmy, jakie wyniki model przewiduje dla tych samych danych:

```python
y_pred = model.predict(X)
```

Teraz w `y_pred` mamy przewidywaną popularność każdego utworu na podstawie jego tempa.

---

### Krok 5. Wizualizacja wyniku

Zobaczmy, jak ta „linia trendu” wygląda na wykresie.

```python
plt.figure(figsize=(8,5))  
plt.scatter(X, y, color="lightblue", alpha=0.5, label="dane rzeczywiste")  
plt.plot(X, y_pred, color="red", label="linia regresji")  
plt.xlabel("Tempo utworu")  
plt.ylabel("Popularność")  
plt.title("Regresja liniowa: tempo a popularność")  
plt.legend()  
plt.show()
```


## 🧐 Jak to czytać?

- Niebieskie punkty to **prawdziwe dane** (utwory).  
- Czerwona linia to **model**, który próbuje opisać trend.  

Jeśli linia idzie lekko w górę, to znaczy, że wraz ze wzrostem tempa rośnie też średnia popularność.  
Jeśli jest prawie pozioma tempo nie ma dużego wpływu.

---

## 📊 Dodatkowo: sprawdź dopasowanie modelu

Model potrafi zwrócić tzw. współczynnik dopasowania `R²`,  czyli informację jak dobrze linia tłumaczy dane.

```python
model.score(X, y)
```

Wartość score `R²`. mieści się między 0 a 1.  
- blisko **1** – model dobrze dopasowany,  
- blisko **0** – model nie tłumaczy danych (czyli tempo nie ma znaczenia dla popularności).



## Zadanie

1. Spróbuj zamienić `tempo` na inną kolumnę, np. `energy` lub `danceability`.  
   Czy te cechy lepiej przewidują popularność?  
2. Porównaj wynik `model.score(X, y)` dla różnych cech.  
3. Zastanów się, która z cech ma **największy wpływ na popularność utworu**.


🎉 Yaaay!  

Wiesz jak zbudować najprostszy model ML. Wiesz, co to znaczy „trenować model” i „przewidywać wartości”. Potrafisz zwizualizować wyniki i sprawdzić, jak dobrze model działa.  