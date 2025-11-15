---
title: 13. Jak działa uczenie maszynowe od środka?
layout: post
---

W tej lekcji zajrzymy trochę głębiej pod powierzchnię tego, co robi model ML, kiedy „uczy się” na danych.  Do tej pory trenowałyśmy modele tak po prostu – kilka komend i działa. Teraz zobaczymy, **co naprawdę dzieje się w środku**.

Nie chcemy traktować modelu jak czarnej skrzynki, spróbujemy zrozumieć, *dlaczego coś działa*, *dlaczego czasem nie działa* i *co można poprawić?*.

## Uczenie Maszynowe

Machine learning, czyli uczenie maszynowe, to tak naprawdę **bardzo uporządkowany sposób uczenia komputerów na podstawie doświadczenia**.

W praktyce wygląda to tak, jakbyśmy dali maszynie dużą liczbę przykładów i pozwolili jej samodzielnie odkryć wzorce, które rządzą danymi. Komputer nie dostaje gotowej instrukcji „jak dokładnie coś zrobić”. Zamiast tego uczy się, **co działa najlepiej**, obserwując wyniki swoich własnych prób.

![ML]({{ site.baseurl }}/assets/intro-machine-learning.png){:title="machine learning" class="img-responsive"}


W uczeniu maszynowym kluczowe są trzy elementy:

**1. Dane**  
To nasz materiał treningowy — im lepszy i bardziej różnorodny, tym trafniejsze wnioski.

**2. Model**  
To matematyczna konstrukcja, która próbuje dopasować reguły do danych. Na początku jest „pusta”, nie wie nic.

**3. Trenowanie**  
To proces, w którym model robi prognozę, porównuje ją z prawdą i poprawia swoje wewnętrzne ustawienia, aby następnym razem przewidzieć lepiej.


Cały mechanizm polega na nieustannym **uczeniu się na błędach**.  
Model po każdej iteracji mierzy, jak bardzo się pomylił (to jest tzw. *strata*), a następnie — dzięki metodzie **gradientu** — przesuwa swoje parametry tak, aby błąd spadał. Małymi krokami, ale konsekwentnie.

Dlatego mówimy, że uczenie maszynowe to **systematyczne zmniejszanie błędu**, aż model stanie się na tyle precyzyjny, że możemy go wykorzystać do przewidywania nowych, nieznanych danych.

Czy widziesz, jak wszystko zaczyna łączyć się w całość? 

---

## 👉 Cechy i etykieta – dwa filary ML

Każdy model ML działa na bardzo prostym założeniu:

- **cechy (features)** – to dane wejściowe,  
- **etykieta (label)** – to wartość, którą model ma przewidzieć.

Przykłady z naszych danych:

**Spotify – cechy**
- tempo  
- energia  
- taneczność  

**Spotify – etykieta**
- popularność  

**Filmy – cechy**
- czas trwania  
- Meta_score  
- liczba głosów  

**Filmy – etykieta**
- ocena IMDb  

Model zawsze szuka **zależności** między zestawem cech a etykietą.

---

## 👉 Co to znaczy, że model się „uczy”?

Podczas treningu składa się to z kilku kroków:

1. model próbuje stworzyć jakiś wzór,  
2. sprawdza, **jak bardzo się myli**,  
3. próbuje poprawić ten wzór,  
4. znowu mierzy błąd,  
5. poprawia wzór jeszcze trochę…

Tak działa „uczenie się na błędach”.  
Model sprawdza każdą próbę, ocenia ją, a potem minimalnie zmienia strategię.  
W `scikit-learn` nie widzimy tych kroków, ale one tam są.  Ten proces powtarza się wiele razy i nazywamy go **iteracjami**.

---

## 👉 Co to jest błąd modelu?

Załóżmy, że model przewidział popularność utworu:

- przewidywana wartość: `55`  
- prawdziwa wartość: `60` 

`Błąd = 60 – 55 = 5`

Im mniejszy błąd, tym lepszy model.  

Uczenie polega na tym, że model **stara się te błędy minimalizować**.

To, jak bardzo model się myli, jest mierzone różnymi wskaźnikami, np.:

- R² dla regresji  
- `accuracy` dla klasyfikacji  

---

## 👉 Decision boundary – granica decyzji

Gdy model klasyfikuje dane (np. popularny / niepopularny), potrzebuje ustalić miejsce, w którym „podejmuje decyzję”.

Najprostszy przypadek:

- jeśli energia > X → popularny
- jeśli energia <= X → niepopularny


To miejsce X jest **granicą decyzji**.  

Przy dwóch cechach taka granica staje się linią na wykresie.  

Przy trzech – płaszczyzną.  

Przy piętnastu – czymś, czego nie da się narysować, ale działa tak samo.

---

## 👉 Nowe narzędzia, które pokazują, jak model myśli

### **1. `model.coef_`**
Pokazuje wpływ każdej cechy (dla regresji liniowej).  
Dzięki temu można zobaczyć, które cechy są ważniejsze.

> model.coef_

Przykład interpretacji:  
jeśli `coef_` dla `No_of_Votes` jest większe niż dla `Duration`,  
to liczba głosów mocniej wpływa na ocenę niż długość filmu.

```python
from sklearn.linear_model import LinearRegression

X = df_small[["duration_ms", "energy", "danceability"]]
y = df_small["popularity"]

model = LinearRegression()
model.fit(X, y)

for feature, coef in zip(X.columns, model.coef_):
    print(feature, "→", coef)
```

### Co to kod robi?

- `X` – cechy, czyli dane wejściowe (tu: 3 kolumny Spotify)
- `y` – etykieta, czyli to, co przewidujemy (popularność)
- `model.fit(X, y)` – trening modelu
- `model.coef_` – liczby, które pokazują wpływ każdej cechy
- pętla `for` – wypisuje nazwy cech i ich współczynniki

Co wynika z tego kodu, czy widzisz coś ciekawego w wyniku? 

---

### **2. `model.intercept_`**
Punkt startowy modelu – wartość, od której zaczyna.

> model.intercept_

---

### **3. `model.predict()`**
Predykcja dla danych.  
Możesz podejrzeć wynik np. dla 3 pierwszych filmów:

> model.predict(X.iloc[:3])

---

### **4. `plt.contourf()`**  
Nowy rodzaj wizualizacji – koloruje obszar wykresu tak, jak „widzi” go model.  
To pozwala zobaczyć granicę decyzji dla klasyfikacji dwuwymiarowej.

Żeby to zrobić, potrzebna jest jeszcze jedna funkcja:

### **5. `np.meshgrid()`**
Tworzy siatkę punktów w tle wykresu (takie tło, które model „pyta” o decyzję).

Używa się ich razem, żeby zobaczyć, jak model dzieli przestrzeń cech na grupy.

---

## 👉 Co daje taka wiedza?

- rozumiesz, jak powstaje wynik modelu  
- wiesz, dlaczego model może się mylić  
- potrafisz lepiej dobrać cechy  
- łatwiej zauważyć, kiedy model próbuje „nauczyć się za bardzo” (przeuczenie)

To nie są szczegóły matematyczne – to **intuicja**, która określa, kiedy model ma sens, a kiedy nie.

---

## 👉 Krótkie podsumowanie

Uczenie maszynowe w środku zawiera wiele informacji, które "my" jako ludzie rozumiemy, ale nie chcemy ogarniać ich ręcznie: 

- cechy → dane wejściowe  
- etykieta → odpowiedź, której model musi się nauczyć  
- błąd → różnica między tym, co przewidział, a prawdą  
- iteracje → ciągłe poprawianie modelu  
- decision boundary → granica klasyfikacji  
- coef_ i intercept_ → wskazówki, co ma największy wpływ  
- contourf + meshgrid → wizualizacja decyzji w klasyfikacji 2D

W kolejnych zajęciach zobaczymy, jak wykorzystać tę wiedzę, kiedy zaczniemy porównywać różne modele i sprawdzać, dlaczego jeden działa lepiej niż drugi.
