---
title: 4. Pierwsze sprzątanie danych
layout: post
---

W poprzednim rozdziale udało Ci się wczytać pierwszy zbiór danych `spotify_sample.csv` do zmiennej `df`.  
Teraz zobaczymy, jak sprawdzić, czy te dane nadają się do pracy.
Zanim jednak przejdziemy dalej, możesz się zastanawiać, **dlaczego użyliśmy `pandas` i czym jest tajemnicze `df`?**

---

## 🐼 Co to jest pandas?

`pandas` to jedna z najpopularniejszych bibliotek w Pythonie.  
Pomaga pracować z danymi zapisanymi w tabelach podobnie jak w Excelu czy Google Sheets, ale w wersji *programistycznej*.

Dzięki `pandas` można:
- wczytać dane z pliku CSV,
- sprawdzić, ile jest wierszy i kolumn,
- policzyć średnią, minimum, maksimum, wykonać inne operacje matematyczne
- tworzyć nowe kolumny i porównywać wartości.

W skrócie: `pandas` to narzędzie, które pozwala **zrozumieć dane zanim zaczniemy z nimi coś robić.**

---

## 📘 A co to jest `df`?

`df` to skrót od *DataFrame*.  
To obiekt, który trzyma nasze dane w postaci tabeli:  
wiersze to pojedyncze utwory, a kolumny to ich cechy, takie jak tempo, energia, popularność.

Kiedy piszemy:

```python
df = pd.read_csv("spotify_sample.csv")
```

to tak, jakbyśmy powiedzieli:
„Weź dane z pliku i zapisz je w tabeli o nazwie df”.

Od tej pory wszystko, co robimy z danymi, wykonujemy właśnie na `df`.

---

Teraz przyjrzymy się, jak duży jest nasz zbiór danych, zobaczymy, jakie ma kolumny i jakiego są typu, poszukamy braków lub błędnych wartości, przygotujemy dane tak, by łatwiej było z nimi pracować dalej.

Nie będziemy jeszcze niczego modelować ani rysować. To etap „porządku w danych” coś jak sprawdzenie, czy nasza kuchnia jest gotowa, zanim zaczniemy gotować.


## 📊 Zaczynamy od sprawdzenia danych

1. Najpierw zobacz, jak duży jest Twój zbiór danych.

Która komenda za to odpowiadała? Podpowiadamy szukamy **"kształtu danych"**

Ta komenda zwraca dwie liczby - pierwsza to liczba wierszy, druga to liczba kolumn.  
Na przykład wynik `(300, 10)` oznacza, że masz 300 utworów, z których każdy opisany jest przez 10 cech.  
To prosta informacja, ale bardzo ważna bo wiesz, z jaką skalą danych pracujesz.


2. Zobacz, jakie kolumny są w Twoim zbiorze danych.

W przypadku danych Spotify mogą to być m.in.:

- track_name  
- artists  
- popularity  
- danceability  
- energy  
- tempo  
- duration_ms  
- track_genre  

Każda kolumna to jedno pytanie o utwór.  

Na przykład: *jak szybki jest utwór?*, *czy jest taneczny?*, *jak bardzo jest popularny?*

---

### Co oznacza info()

Kiedy już wiesz, jakie masz kolumny, możesz sprawdzić, **jakiego typu są dane** i czy nie ma w nich braków.

```python
df.info()
```

Jeśli widzisz, że jakaś kolumna ma mniej wartości niż reszta, a to znaczy, że brakuje tam informacji.  
Takie sytuacje są normalne, ale warto wiedzieć, gdzie występują.

---

### Szukanie brakujących danych

Braki danych to jedna z najczęstszych rzeczy, które spotkasz w analizie.  
Czasem ludzie nie wypełniają pól w formularzu, czasem API nie zwróci wartości.

Zobacz, gdzie w Twoich danych są luki.

```python
df.isna().sum()
```

Ta komenda pokazuje, ile wartości brakuje w każdej kolumnie. Nie trzeba jeszcze nic poprawiać, po prostu najpierw chcemy zobaczyć, czy w ogóle występują braki.

---

### Wybieramy kolumny do dalszej pracy

Aby łatwiej pracować, wybierz kilka kolumn, które są najbardziej interesujące. Dlatego zrobimy mniejszą tabelkę z tabeli głównej, którą mamy czyli mniejsza ramka danych z większej ramki danych.

```python
df_small = df[["track_name","artists","popularity","tempo","danceability","energy","duration_ms","track_genre"]]
```

Teraz możesz sprawdzić, jak wygląda nowa mniejsza tabela.

```python
df_small.head()
```

Dzięki temu masz przed sobą tylko te dane, które będą nam potrzebne w dalszych analizach, bez pozostałego sporego szumu. Reszta danych owszem moze być ciekawa, ale w tym momencie zupełnie nam nie potrzebna.

---

### Długość utworu w minutach

Kolumna `duration_ms` pokazuje długość utworu w milisekundach. Jednak mało kto z nas mysli o czasie w milisekundach prawda? Nawet sekundy są dla nas raczje mało użyteczne.

Gdybyśmy tak chcieli przeliczyć milisekundy na sekundy a sekundy na czas w minutach? 

Załóżmy utwór trwa `195000 milisekund` ile to sekund? 

195000 trzeba podzielić na 1000 → ms → s

195 trzeba podzielić na 60 → sekundy → minuty 

i jeszcze zostanie nam reszta z dzielenia czyli pozostałe sekundy

```python
# czas utworu w milisekundach
czas_ms = 195000
print("Czas w milisekundach:", czas_ms)

# 1. zamiana milisekund na sekundy
czas_s = czas_ms / 1000
print("Po zamianie na sekundy:", czas_s)

# 2. ile pełnych minut mieści się w tym czasie?
minuty = czas_s // 60
print("Pełne minuty:", minuty)

# 3. ile sekund zostaje po odjęciu pełnych minut?
sekundy = czas_s % 60
print("Pozostałe sekundy:", sekundy)

# 4.  wyświel wynik uzywamy tu f-string oraz konwertujemy dane z wartości dziesiętnych na całkowit3 (integer)
print(f"Czas utworu: {int(minuty)} min i {int(sekundy)} s 🎵")
```

Czyli z ms → do minut przejdziemy dzieląc przez 60000. 

**Stąd:**

Możemy dodać do naszych danych nową kolumnę z długością w minutach, aby było czytelniej.

```python
df_small["duration_min"] = df_small["duration_ms"] / 60000 +
```

Zobacz kilka pierwszych wierszy, aby upewnić się, że wszystko działa:

```python 
df_small[["track_name","duration_ms","duration_min"]].head()
```

Teraz mamy kolumnę `duration_min`, która pokazuje długość utworu w minutach.  
To przykład drobnego sprzątania danych, które czyni je bardziej użytecznymi.

---

### Sprawdzenie wartości podejrzanych

Czasami dane zawierają błędy – na przykład zera tam, gdzie nie powinno ich być, albo liczby tak duże, że trudno w nie uwierzyć.
Zanim pójdziemy dalej, sprawdźmy, czy kolumny z tempem i popularnością wyglądają w miarę normalnie.

```python
df_small["tempo"].describe()
```  

```python
df_small["popularity"].describe()
```

Ta funkcja pokazuje **podstawowe statystyki**: wartości minimalne, maksymalne, średnią i kilka innych.
Na tej podstawie możesz szybko zobaczyć, czy coś wygląda podejrzanie.

Jeśli na przykład tempo utworu wynosi 0, a wiemy, że piosenka musi mieć przynajmniej kilkadziesiąt uderzeń na minutę,
to znak, że coś trzeba będzie później poprawić lub sprawdzić dokładniej.

---

### Mini zadanie

1. Sprawdź, ile gatunków znajduje się w kolumnie `track_genre`.  
   ```python
   df_small["track_genre"].nunique()
   ```

2. Wyświetl kilka przykładów gatunków.  
   ```python
   df_small["track_genre"].unique()[:10]
   ```

3. Zapisz jedno pytanie, które przychodzi Ci do głowy po tym przeglądzie.  
   Na przykład:  
   - które gatunki są najbardziej popularne?
   - czy szybsze gatunki mają wyższą średnią popularność?

Czy jesteście w stanie grupą wymyśleć inne pytania?

---

🎉 Świetnie.  
Znasz już podstawowe kroki w poznawaniu i porządkowaniu danych.  
W następnym rozdziale zaczniemy analizować dane bardziej świadomie i spróbujemy znaleźć odpowiedzi na Twoje pytania.
