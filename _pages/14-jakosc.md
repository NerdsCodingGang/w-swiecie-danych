---
title: 14. Porównywanie modeli i ocena jakości
layout: post
---

Do tej pory trenowaliśmy pojedyncze modele i sprawdzaliśmy, jak przewidują popularność utworów.  
Teraz zrobimy coś, co w pracy analitycznej jest absolutnie kluczowe:

**sprawdzimy, który model radzi sobie z zadaniem najlepiej oraz dlaczego.**

To bardzo ważny moment, bo w świecie ML nie istnieje coś takiego jak najlepszy model do wszystkiego, uniwersalnych rozwiązań nie ma... ;)  
Czasem działa liniowy, czasem drzewo decyzyjne, czasem model zespołowy (taki jak RandomForest).  
Dlatego musimy nauczyć się **porównywać ich skuteczność**.

---

## Train/Test split 🤔 po co dzielimy dane?

Kiedy model uczymy na *wszystkich danych*, to może wydawać się świetny,  
ale w rzeczywistości mógł po prostu „nauczyć się na pamięć”.

Żeby temu zapobiec, dzielimy dane na dwie części:

- **train** – do nauki modelu  
- **test** – do sprawdzenia, jak model radzi sobie na danych, których *nigdy jeszcze nie widział*

Załóżmy sytuację, że posiadasz ogromną bazę obrazków. W tej bazie mamy obrazki piesków i kotków, baza ma tysiące zdjęć, model zaczyna uczyć się perfekcyjnie na danych treningowych. Potem okazuje się, że model wcale tak świetnie nie radzi sobie na danych testowych. 

Dlaczego? 

Może w danych treningowych pojawiły się podpisy, albo metadane np. wszystkie pliki pies miały nazwę `IMG_DOG_5134324.png` w takim wypadku model wystarczyło, że nauczył się, że nazwa zawiera pewne słowo... takich sytuacji może być więcej, w naszym obowiązku jest zadbanie o to, że nasz model został przetestowany przeciwko prawdziwej rzeczywistości.


A tylko **test** pokazuje rzeczywistą jakość modelu.

W Pythonie wygląda to tak:

```python
from sklearn.model_selection import train_test_split  

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

To oznacza:

- 80 procent danych → trenowanie  
- 20 procent danych → testowanie

---

## Jakie modele porównamy?

Zrobimy trzy modele przewidujące popularność utworów:

1. **LinearRegression** – model liniowy  
2. **DecisionTreeRegressor** – drzewo decyzyjne  
3. **RandomForestRegressor** – wiele drzew połączonych w jeden model  

Każdy model działa inaczej, ma inne mocne strony i inne słabości.

---

## Jak oceniać jakość modeli?

Użyjemy trzech wskaźników jakości:

### 👉  MAE – Mean Absolute Error  
Średnia różnica między przewidywaną a prawdziwą wartością.  
Im mniejsza, tym lepiej.  
Łatwe do zrozumienia: „o ile model się myli *średnio*”.

### 👉 MSE – Mean Squared Error  
To samo co MAE, ale bardziej karze większe błędy.  
Również – im mniejsza, tym lepiej.

### 👉 R² – współczynnik dopasowania  
Już kolejny nam się pojawia. Wartość od 0 do 1.  
Im bliżej 1, tym lepiej model wyjaśnia zmienność danych.

R² jest najczęściej używany, ale najlepiej patrzeć na wszystkie trzy miary.



## Trzy modele, jeden podział danych, trzy wyniki

```python
from sklearn.linear_model import LinearRegression
from sklearn.tree import DecisionTreeRegressor
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score

# Dane
X = df_small[["tempo", "energy", "danceability"]]
y = df_small["popularity"]

# Train/Test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

models = {
    "LinearRegression": LinearRegression(),
    "DecisionTree": DecisionTreeRegressor(),
    "RandomForest": RandomForestRegressor()
}

for name, model in models.items():
    model.fit(X_train, y_train)
    predictions = model.predict(X_test)

    mae = mean_absolute_error(y_test, predictions)
    mse = mean_squared_error(y_test, predictions)
    r2 = r2_score(y_test, predictions)

    print(f"\n=== {name} ===")
    print("MAE:", mae)
    print("MSE:", mse)
    print("R²:", r2)
```

###  Jak interpretować wyniki?

Po uruchomieniu kodu zobaczysz 3 zestawy liczb.  

Przykładowo Twoje wnioski 

- `LinearRegression` – działa stabilnie, ale może nie uchwycić skomplikowanych zależności  
- `DecisionTree` – może radzić sobie świetnie na train, ale gorzej na test (to typowy overfitting)  
- `RandomForest` – zwykle najbardziej praktyczny, bo uśrednia wynik wielu drzew, nie zawsze tego chcemy

Najważniejsze:
**porównujemy modele po tych samych danych i tej samej miarze jakości.**

wiemy, że:

- jeden model nie dominuje zawsze  
- każdy ma swoje ograniczenia  
- warto je porównywać i myśleć o kompromisach, kosztach i zyskach
- dopiero sprawdzenie na jakości testowej pokazuje prawdziwą skuteczność


## ZADANIE - który model działa najlepiej?

Teraz czas przećwiczyć to samodzielnie.  
Skoro porównaliśmy trzy modele na naszych danych Spotify, zróbmy mały krok dalej.

Twoim zadaniem będzie:

🟣**1. Wybrać **jedną dodatkową cechę** do modelu**
Możesz wybrać np.:

- `loudness`  
- `valence`  
- `duration_ms`  
- `acousticness`

Dodaj ją do tabeli `X`.  
Zastanów się:  czy ta cecha *może* mieć wpływ na popularność?


🟣 **2. Ponownie uruchomić trzy modele**
LinearRegression, DecisionTreeRegressor, RandomForestRegressor  
— tak jak w przykładzie powyżej, ale z nową cechą w `X`.

Nic nie zmieniasz oprócz listy cech.


🟣 **3. Porównać wyniki (MAE, MSE, R²)**
Zapisz w komórce tekstowej:

- który model działa najlepiej,  
- który najsłabiej,  
- czy dodanie cechy pomogło, czy nie?


🟣 **4. Dodatkowo (opcjonalnie)**

Narysuj wykres słupkowy z wartościami R² dla trzech modeli.

Podpowiedź:

> plt.bar(nazwy_modeli, wyniki_r2)


---
## Gratulacje 🎉 

Jeśli coś z tych 2-dni naprawdę warto zapamiętać, to to, że w pracy z danymi nie chodzi o perfekcje (nie zawsze) i często wcale nie perfekcyjność, a dość dobrze, tak by zrozumieć ukrytą informację! W dużych danych trudno o perfekcje, tylko o umiejętność zadawania właściwych pytań i sprawdzania ich na faktach.

Właśnie zrobiliście to, co robią osoby pracujące w data science na co dzień: wzięliście dane, zadaliście im pytania, zbudowaliście modele i oceniliście ich jakość!


![applause]({{ site.baseurl }}/assets/applause.gif){:title="brawo" class="img-responsive"}
