---
title: 12. Jak działa uczenie maszynowe od środka?
layout: post
---

W tej lekcji zajrzymy trochę głębiej pod powierzchnię tego, co robi model ML, kiedy „uczy się” na danych.  Do tej pory trenowałyśmy modele tak po prostu – kilka komend i działa. Teraz zobaczymy, **co naprawdę dzieje się w środku**.

Nie chcemy traktować modelu jak czarnej skrzynki, spróbujemy zrozumieć, *dlaczego coś działa*, *dlaczego czasem nie działa* i *co można poprawić?*.

## Uczenie Maszynowe

Machine learning, czyli uczenie maszynowe, to tak naprawdę **bardzo uporządkowany sposób uczenia komputerów na podstawie doświadczenia**.

W praktyce wygląda to tak, jakbyśmy dali maszynie dużą liczbę przykładów i pozwolili jej samodzielnie odkryć wzorce, które rządzą danymi. Komputer nie dostaje gotowej instrukcji „jak dokładnie coś zrobić”. Zamiast tego uczy się, **co działa najlepiej**, obserwując wyniki swoich własnych prób.

![ML]({{ site.baseurl }}/assets/intro-machine-learning.png){:title="machine learning" class="img-responsive"}


W uczeniu maszynowym kluczowe są trzy elementy:

🟣 **1. Dane**  
To nasz materiał treningowy — im lepszy i bardziej różnorodny, tym trafniejsze wnioski.

🟣 **2. Model**  
To matematyczna konstrukcja, która próbuje dopasować reguły do danych. Na początku jest „pusta”, nie wie nic.

🟣 **3. Trenowanie**  
To proces, w którym model robi prognozę, porównuje ją z prawdą i poprawia swoje wewnętrzne ustawienia, aby następnym razem przewidzieć lepiej.


Cały mechanizm polega na nieustannym **uczeniu się na błędach**.  
Model po każdej iteracji mierzy, jak bardzo się pomylił (to jest tzw. *strata*), a następnie — dzięki metodzie **gradientu** — przesuwa swoje parametry tak, aby błąd spadał. Małymi krokami, ale konsekwentnie.

Dlatego mówimy, że uczenie maszynowe to **systematyczne zmniejszanie błędu**, aż model stanie się na tyle precyzyjny, że możemy go wykorzystać do przewidywania nowych, nieznanych danych.

### Czy widziesz, jak wszystko co do tej pory robimy zaczna się zaczyna łączyć się w całość? 

Wcześniej naszym zadaniem było poznanie dane, oczyszczenie je, policzenie statystyk, zrobienie wykresów, szukanie zależności. Wiemy jak stworzyć mini-raport. 
W rozdziale 10 było przejście przez trenowanie „krok po kroku”. Ten etap miał pokazać, **jak wygląda praca z modelem od strony użytkownika**.

Teraz widać, że wszystkie wcześniejsze ćwiczenia miały sens:  to właśnie one tworzą **podstawę, na której model może się uczyć**.

Uczenie maszynowe to w gruncie rzeczy **systematyczne zmniejszanie błędu** — powoli, iteracyjnie, aż model zaczyna przewidywać coraz dokładniej.  
Każdy krok wykonany wcześniej był przygotowaniem do tego momentu.

---

## 👉 Cechy i etykieta – dwa filary ML

Każdy model ML działa na bardzo prostym założeniu:

- **cechy (features)** – to dane wejściowe,  
- **etykieta (label)** – to wartość, którą model ma przewidzieć.

Przykłady z naszych danych:

🎵 **Spotify – cechy**
- tempo  
- energia  
- taneczność  

 🎵 **Spotify – etykieta**
- popularność  

 🎬 **Filmy – cechy**
- czas trwania  
- Meta_score  
- liczba głosów  

🎬 **Filmy – etykieta**
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


### ... trudne do wyobrażenia?

Wiemy!

Dlaczego tak trudno nam sobie tę granicę wyobrazić? Bo model ustala tę granicę **nie na oko**, tylko na podstawie danych.  

Model "zastanawia się:
_W którym miejscu najlepiej oddzielić jedną grupę od drugiej?_

Przy jednej cesze granica to *po prostu jedna liczba X*.  
Przy dwóch — linia na wykresie.  
Przy trzech — płaszczyzna.  
Przy piętnastu — czego już nie da się narysować, ale działa dokładnie tak samo.

---

###  Przykład z 2 cechami

Załóżmy, że bierzemy dwie cechy:  
`energy` i `danceability`.

Każdy utwór to jeden punkt na wykresie.  
Jeśli oznaczymy:

- popularne utwory na fioletowo  
- niepopularne na szaro

możemy spróbować **od ręki** narysować linię, która oddzieli te dwie grupy.

Model robi to samo — tylko precyzyjniej.


---

Poniższy kod jest dość prosty.  
Nie rysuje jeszcze tła ani mapy decyzji, tylko pokazuje:

1. dane na scatterze  
2. linię graniczną, jaką znalazł model


![granica]({{ site.baseurl }}/assets/energy-dance.png){:title="granica decyzji" class="img-responsive"}



```python
from sklearn.linear_model import LogisticRegression  
import numpy as np  
import matplotlib.pyplot as plt  
 
print("Bierzemy tylko dwie cechy")
X = df_small[["energy", "danceability"]]  
y = (df_small["popularity"] > 70).astype(int)  
  
model = LogisticRegression()  
model.fit(X, y)  
  
print("Rysowanie punktów") 
plt.scatter(df_small["energy"], df_small["danceability"], c=y, cmap="coolwarm", alpha=0.5)  
  
print("Tworzymy prostą linię graniczną")
x_vals = np.linspace(X["energy"].min(), X["energy"].max(), 100)  
y_vals = -(model.coef_[0][0] * x_vals + model.intercept_[0]) / model.coef_[0][1]  

plt.plot(x_vals, y_vals, color="black")  
plt.xlabel("energy")  
plt.ylabel("danceability")  
plt.title("Granica decyzji dla LogisticRegression")  
plt.show()
```


- `model.fit(X, y)`  -  Model nauczył się, gdzie znajdują się „fioletowe” i „szare” punkty.

- `model.coef_ + model.intercept_` - To właśnie liczby, które definiują granicę między klasami. Nie musisz ich teraz analizować — chodzi o to, że model ich używa.

- `plot(x_vals, y_vals)`  - Rysujemy linię, która według modelu najlepiej oddziela dwie grupy.

Po uruchomieniu kodu zobaczysz wykres:  
punkty + czarna linia, która jest właśnie **decision boundary**.

Od tego momentu model może podjąć decyzję dla *nowego utworu*, którego nigdy wcześniej nie widział:

- jeśli znajdzie się „po tej stronie linii” → popularny  
- jeśli po drugiej → niepopularny

To jest cała istota klasyfikacji.

Zrozumienie granicy decyzji sprawia, że zaczynamy widzieć ML nie jako „czarną skrzynkę”,  
ale jako **system, który szuka najlepszego sposobu oddzielenia jednych punktów od drugich**.


---

## 👉 Nowe narzędzia, które pokazują, jak model myśli

### **1. `model.coef_`**
Pokazuje wpływ każdej cechy (dla regresji liniowej).  
Dzięki temu można zobaczyć, które cechy są ważniejsze.

> model.coef_

Przykład interpretacji:  
> Analizując wpływ cech na ocenę filmu IMDb:
> jeśli `coef_` dla `No_of_Votes` jest większe niż dla `Duration`,  
> to liczba głosów mocniej wpływa na ocenę niż długość filmu.

Spójrzmy na utwory

```python
from sklearn.linear_model import LinearRegression

X = df_small[["duration_ms", "energy", "danceability"]]
y = df_small["popularity"]

model = LinearRegression()
model.fit(X, y)

for feature, coef in zip(X.columns, model.coef_):
    print(feature, "→", coef)
```


- `X` – cechy, czyli dane wejściowe (tu: 3 kolumny Spotify)
- `y` – etykieta, czyli to, co przewidujemy (popularność)
- `model.fit(X, y)` – trening modelu
- `model.coef_` – liczby, które pokazują wpływ każdej cechy
- pętla `for` – wypisuje nazwy cech i ich współczynniki

---

### **2. `model.intercept_`**

`model.intercept_` to **wartość początkowa modelu**, czyli liczba, od której model „zaczyna przewidywanie”, zanim weźmie pod uwagę jakiekolwiek cechy.

Można to traktować jako:
**„przewidywana wartość wtedy, gdy wszystkie cechy mają wartość zero”.**

To brzmi abstrakcyjnie, więc zobaczmy to na przykładzie z danymi Spotify.

---

####  Co oznacza intercept w praktyce?

Załóżmy, że trenujemy model, który przewiduje popularność na podstawie:

- tempo  
- energia  
- taneczność  

Model musi mieć jakiś **punkt startowy**.  
Nawet jeśli wszystkie cechy = 0 (co w muzyce nie jest realistyczne, ale matematycznie konieczne), model powinien móc zwrócić jakąś wartość.

Tą wartością jest **intercept**.

To takie „przesunięcie” całej funkcji w górę lub w dół, żeby dopasować ją do rzeczywistych danych.


---

### **3. `model.predict()`**

Predykcja to moment, w którym model **zastosowuje to, czego się nauczył**, do konkretnych danych.  
Do tej pory model tylko trenował: porównywał swoje wyniki z prawdą i poprawiał parametry.  
Teraz po prostu dostaje wiersz danych i odpowiada:

**„Na podstawie tych cech przewiduję, że wynik będzie taki.”**

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

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression, LogisticRegression

# --- 1. Dane: wybieramy cechy i etykietę ---------------------------
X = df_small[["tempo", "energy", "danceability"]]
y = df_small["popularność"]

# Binarna wersja popularności (do decision boundary)
y_class = (df_small["popularność"] > 70).astype(int)

# --- 2. Model regresyjny (przewiduje liczbę) -----------------------
reg = LinearRegression()
reg.fit(X, y)

print("WSPÓŁCZYNNIKI (coef_):")
for feature, coef in zip(X.columns, reg.coef_):
    print(f"{feature} → {coef:.4f}")

print("\nINTERCEPT:")
print(reg.intercept_)

print("\nPREDYKCJE DLA 3 PIERWSZYCH UTWORÓW:")
print(reg.predict(X.iloc[:3]))

# --- 3. Model klasyfikacji (potrzebny do decision boundary) --------
clf = LogisticRegression()
clf.fit(X[["energy", "danceability"]], y_class)

# --- 4. Wizualizacja granicy decyzji ------------------------------

# Tworzymy siatkę punktów (energia i taneczność)
x_min, x_max = X["energy"].min(), X["energy"].max()
y_min, y_max = X["danceability"].min(), X["danceability"].max()
xx, yy = np.meshgrid(
    np.linspace(x_min, x_max, 200),
    np.linspace(y_min, y_max, 200)
)

# Przewidywanie dla każdego punktu siatki
Z = clf.predict(np.c_[xx.ravel(), yy.ravel()])
Z = Z.reshape(xx.shape)

# Rysujemy obszary decyzji
plt.contourf(xx, yy, Z, alpha=0.3, cmap="coolwarm")

# Dodajemy prawdziwe punkty
plt.scatter(X["energy"], X["danceability"], c=y_class, cmap="coolwarm", edgecolor="k")

plt.xlabel("energy")
plt.ylabel("danceability")
plt.title("Granica decyzji modelu (popularne vs niepopularne)")
plt.show()
```

---

## 🎉  WOW!

Uczenie maszynowe pod spodem zawiera wiele informacji, które "my" jako ludzie rozumiemy, ale nie chcemy ogarniać ich ręcznie: 

Mały słowniczek pojęć:
- cechy → dane wejściowe  
- etykieta → odpowiedź, której model musi się nauczyć  
- błąd → różnica między tym, co przewidział, a prawdą  
- iteracje → ciągłe poprawianie modelu  
- decision boundary → granica klasyfikacji  
- coef_ i intercept_ → wskazówki, co ma największy wpływ  
- contourf + meshgrid → wizualizacja decyzji w klasyfikacji 2D

Jak wykorzystać tę wiedzę, kiedy zaczniemy porównywać różne modele i sprawdzać, dlaczego jeden działa lepiej niż drugi.
