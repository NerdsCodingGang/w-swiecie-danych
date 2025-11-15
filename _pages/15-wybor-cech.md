---
title: 15. Wybór cech (feature selection)
layout: post
---

Wy jeszcze tutaj zaglądacie…? 👀  

no to naprawdę nie macie dość naszych warsztatów.  
Serce rośnie! 💜

W tym rozdziale zrobimy coś bardzo extra!
 ~  sprawdzimy **które cechy naprawdę mają znaczenie**, a które tylko udają, że coś wnoszą.



To ważny krok, bo model **nie potrzebuje wszystkiego**.  
Czasem dwie cechy są prawie identyczne.  
Czasem jedna jest kompletnie bezużyteczna.  
Czasem dodanie większej liczby cech *psuje* wynik.

Czas trochę zamieszać w naszych danych i sprawdzić, co tak pomaga modelowi przewidywać popularność utworów na Spotify

![salem]({{ site.baseurl }}/assets/salem-mix.gif){:title="mieszamy" class="img-responsive"}


---

## Dlaczego wybór cech jest interesujący?

Modele uczą się z danych.  
Jeśli mają za dużo szumu, mogą:

- mylić się częściej,  
- działać wolniej,  
- „uczyć się na pamięć” (overfitting),  
- dawać mniej stabilne wyniki.

Dlatego dobry Data Scientist zawsze zadaje pytanie:

> "Które kolumny faktycznie pomagają przewidywać to, co mnie interesuje?”

---

## Krok 1: sprawdźmy korelacje między cechami

Zacznijmy od podstaw: korelacja pokazuje, które kolumny **rosną lub maleją razem**.

`df_small[["tempo", "energy", "danceability", "valence", "loudness", "popularity"]].corr()`

To szybki sposób, żeby zobaczyć:

- które cechy są ze sobą podobne,  
- które mogą przewidywać popularność,  
- które można pominąć.

Podpowiedź do analizy:
- wartości bliskie **1** → cechy bardzo powiązane  
- wartości bliskie **0** → związek słaby  
- wartości **ujemne** → im więcej jednej cechy, tym mniej drugiej  

---

## Krok 2: sprawdzamy znaczenie cech (feature_importances_)

Modele drzewiaste, takie jak `DecisionTreeRegressor` czy `RandomForestRegressor`, mają bardzo wygodną właściwość:

`model.feature_importances_`

To liczby mówiące, **jak mocno każda cecha wpływa na przewidywanie**.

Zróbmy mały przykład na Spotify:
```python
from sklearn.ensemble import RandomForestRegressor

X = df_small[["tempo", "energy", "danceability", "valence", "loudness", "duration_ms"]]  
y = df_small["popularity"]  
  
model = RandomForestRegressor()  
model.fit(X, y)  

for feature, score in zip(X.columns, model.feature_importances_):  
    print(feature, "→", score)
```

**Jak to zinterpretować?**

- im wyższy wynik, tym **ważniejsza cecha**,  
- wyniki sumują się do 1,  
- możesz porównać, które cechy naprawdę „ciągną” model.

---

## Krok 3: porównujemy model z 3 cechami vs z 6

To bardzo praktyczne ćwiczenie, by rozumieć jak dodawanie cech wpływa na model.

Najpierw model z trzema cechami:

> X3 = df_small[["tempo", "energy", "danceability"]]

Potem model z sześcioma cechami:

> X6 = df_small[["tempo", "energy", "danceability", "valence", "loudness", "duration_ms"]]

Następnie mierzysz ich jakość:

- MAE  
- MSE  
- R²  

i porównujesz wyniki!

```python
# tu już czas na Twój kod! 
```

To pokaże Ci bardzo szybko:

- czy dodatkowe cechy faktycznie pomagają,  
- czy tylko dodają szumu,  
- czy model staje się stabilniejszy.

---

## 👉 Mini zadanie (dla Ciebie!)

Spróbuj teraz:

1. policzyć korelacje wybranych sześciu cech z `popularity`,  
2. uruchomić RandomForest na 3 cechach i na 6,  
3. porównać wyniki,  
4. napisać jedno krótkie zdanie:  
   **„Największy wpływ ma…”** albo **„Dodanie cech X i Y poprawiło/pogorszyło wynik modelu.”**

To jest dokładnie ten sposób myślenia, który buduje dobre projekty!


_Jeśli masz Githuba pobierz plik ipynb z tego rozdziału możesz go wgrać jako element Twojego przyszłego portfolio i pokazać, że rozumiesz wybór cech w ML!_

