---
title: 7. Opowiedz dane obrazem
layout: post
---

Dane liczbowe są ważne, ale na większości z nas zupełnie nieczytelne. Trudno nam skupić się na samych liczbach, dopiero wykresy sprawiają, że zaczynamy je naprawdę rozumieć. Możemy recytować wartość bitcoina w złotówkach z ostatnich z lat 2015-2025 lat, ale pokazując wykres... wykres mówi nam więcej niż same liczby. 
Człowiek szybciej dostrzega kształty, kolory i różnice niż rzędy liczb w tabeli.  

Dzisiaj nauczysz się, jak z danych zrobić obraz, który mówi sam za siebie.  
Dlatego wracamy do naszych danych o utworach Spotify.

W tym rozdziale:

1. Poznasz bibliotekę `matplotlib`, która służy do rysowania wykresów.  
2. Narysujesz swój pierwszy wykres słupkowy.  
3. Porównasz popularność gatunków muzycznych.  
4. Zobaczysz, jak tempo i energia łączą się na wykresie punktowym.  

---

## 📊 Pierwszy wykres: popularność gatunków

Zaczniemy od pokazania średniej popularności dla 10 najpopularniejszych gatunków.  
W poprzednim rozdziale liczyliśmy już te dane, teraz tylko je narysujemy.


```python
import matplotlib.pyplot as plt  

top_genres = df_small.groupby("track_genre")["popularity"].mean().sort_values(ascending=False).head(10)  
plt.figure(figsize=(10,5))  
top_genres.plot(kind="bar", color="mediumseagreen")  
plt.title("Najbardziej popularne gatunki muzyczne")  
plt.xlabel("Gatunek")  
plt.ylabel("Średnia popularność")  
plt.show()
```

## Jak działa ten kod?

> import matplotlib.pyplot as plt

Jesli przypomina `import pandas` to bardzo dobrze, bo to polecenie "importujące" czyluł **włącza bibliotekę matplotlib**, która służy do rysowania wykresów.  
Potem słowo `as` - czyli dodaj alias, dzięki temu możemy używać skrótu `plt`, zamiast pisać za każdym razem pełną nazwę.  

*„hej, Pythonie 🐍, chcę rysować wykresy”*


> top_genres = df_small.groupby("track_genre")["popularity"].mean().sort_values(ascending=False).head(10)

Tutaj tworzymy dane, które za chwilę narysujemy.  

- `groupby("track_genre")` – łączy utwory w grupy według gatunku,  
- `["popularity"].mean()` – dla każdej grupy liczy średnią popularność,  
- `sort_values(ascending=False)` – ustawia wyniki od najwyższej do najniższej,  
- `head(10)` – zostawia tylko 10 pierwszych (najpopularniejszych) gatunków.  

Wszystko to zapisujemy w nowej zmiennej `top_genres`, żeby móc z nią dalej pracować.

W kolejnej linii mamy:

> plt.figure(figsize=(10,5))

To mówi Pythonowi, jak duży ma być wykres.  Wartości w nawiasie to szerokość i wysokość. Dzięki temu wykres mieści się ładnie w oknie Colaba. Możesz pokombinować z rozmiarami okna, zobaczyć jak zmieni się wykres jeśli zmienisz te wartości.


> top_genres.plot(kind="bar", color="mediumseagreen")

Tu dzieje się cała magia rysowania, inaczej *plotowania* wykresu.
Funkcja `plot` rysuje wykres słupkowy (`kind="bar"`) z naszych danych.  
Kolor `mediumseagreen` to po prostu zieleń, ale możesz wpisać dowolny inny kolor, np. `"skyblue"` lub `"salmon"`. 


{% include bookmark.html 
    url=" https://matplotlib.org/stable/gallery/color/named_colors.html#base-colors"
    title="Dokumentacja matplotlib"
    desc="Lista kolorów wg. nazw"
%}

> plt.title("Najbardziej popularne gatunki muzyczne")  
> plt.xlabel("Gatunek")  
> plt.ylabel("Średnia popularność")

Te trzy linijki dodają podpisy:
- `title` – tytuł wykresu,  
- `xlabel` – opis osi poziomej (X),  
- `ylabel` – opis osi pionowej (Y).  

Bez tego wykres byłby pusty i nieczytelny.


> plt.show()

Ostatni krok – **pokaż wykres!**  
To polecenie wyświetla gotowy obraz pod komórką w Colabie. 

Na wykresie słupkowym każdy słupek to jeden gatunek. Wysokość słupka pokazuje średnią popularność utworów w tym gatunku.  

Jeśli widzisz, że niektóre gatunki wystają, to znaczy, że rzeczywiście dominują na Spotify.

Spróbuj wyciągnąć tylko top 5, albo jednak top 20 gatunków. Przyjrzyj się wynikom.

---

## 🎵 Wykres: tempo a energia

Teraz spróbujmy zobaczyć, czy szybsze utwory są bardziej energetyczne.  
Do tego najlepiej pasuje wykres punktowy (ang. *scatter plot*).

```python
plt.figure(figsize=(8,5))  
plt.scatter(df_small["tempo"], df_small["energy"], alpha=0.5, color="cornflowerblue")  
plt.title("Tempo a energia utworów")  
plt.xlabel("Tempo (BPM)")  
plt.ylabel("Energia")  
plt.show()
```

Wykres pokazuje **zależność między tempem utworów a ich energią**. Każdy punkt na wykresie to jeden utwór ze zbioru danych. 

> plt.scatter(df_small["tempo"], df_small["energy"], alpha=0.5, color="cornflowerblue")

To najważniejsza część  → rysujemy punkty!  

Rozbijmy to na kawałki:
- `plt.scatter()` – funkcja, która tworzy **wykres punktowy**.  
- `df_small["tempo"]` – wartości na osi **X** (poziomej). Każdy punkt pokazuje tempo danego utworu.  
- `df_small["energy"]` – wartości na osi **Y** (pionowej). To poziom energii utworu.  
- `alpha=0.5` – przezroczystość punktów (wartość 0–1). Dzięki temu punkty nie zasłaniają się nawzajem, jeśli jest ich dużo.  
- `color="cornflowerblue"` – kolor punktów. Możesz tu wpisać dowolny kolor, np. `"tomato"`, `"orange"`, `"purple"` albo `"skyblue"`.

Każdy punkt na wykresie odpowiada jednemu utworowi, a jego tempo i energia są przedstawione na osiach X i Y.


Zastanów się, czy widzisz jakiś wzór:  
- czy utwory o wyższym tempie mają wyższą energię?  
- czy może związek nie jest aż tak silny?


---

## 🪩 Wykres: tempo i taneczność według gatunków

Spróbujmy jeszcze jednej wizualizacji, tym razem bardziej kolorowej.  
Porównajmy średnie tempo i taneczność różnych gatunków.

```python
grouped = df_small.groupby("track_genre")[["tempo","danceability"]].mean().head(10)  
grouped.plot(kind="bar", figsize=(10,5))  
plt.title("Średnie tempo i taneczność wybranych gatunków")  
plt.xlabel("Gatunek")  
plt.ylabel("Wartości średnie")  
plt.show()
```

Na jednym wykresie zobaczysz dwie cechy jednocześnie – tempo i taneczność.  
To prosty sposób, by zauważyć, które gatunki są bardziej „imprezowe”.

---

## 📊 Najczęściej używane rodzaje wykresów w matplotlib

| Typ wykresu | Funkcja | Do czego służy | Najważniejsze parametry | Przykład |
|--------------|----------|----------------|--------------------------|-----------|
| **Słupkowy (bar)** | `plt.bar(x, y)` | Pokazuje porównanie wartości między grupami, np. popularność gatunków | `color` – kolor słupków<br>`width` – szerokość słupków<br>`alpha` – przezroczystość | > plt.bar(genres, popularity, color="salmon") |
| **Punktowy (scatter)** | `plt.scatter(x, y)` | Pokazuje zależność między dwiema zmiennymi (np. tempo i energia) | `color` – kolor punktów<br>`alpha` – przezroczystość<br>`s` – wielkość punktów<br>`marker` – kształt punktów (np. `"o"`, `"x"`, `"s"`) | > plt.scatter(df["tempo"], df["energy"], alpha=0.5, color="skyblue") |
| **Liniowy (line)** | `plt.plot(x, y)` | Pokazuje zmiany wartości w czasie lub trend | `color` – kolor linii<br>`linestyle` – styl linii (`"-"`, `"--"`, `":"`)<br>`marker` – zaznaczenie punktów na linii | > plt.plot(df["tempo"], color="orange", linestyle="--") |
| **Histogram (hist)** | `plt.hist(x)` | Pokazuje rozkład danych, np. jak często pojawia się dana wartość | `bins` – liczba przedziałów<br>`color` – kolor słupków<br>`alpha` – przezroczystość | > plt.hist(df["tempo"], bins=20, color="green", alpha=0.6) |
| **Wykres kołowy (pie)** | `plt.pie(x, labels=...)` | Pokazuje udział procentowy części w całości | `labels` – etykiety segmentów<br>`autopct` – format procentów<br>`colors` – kolory części | > plt.pie(values, labels=labels, autopct="%1.1f%%") |
| **Boxplot (pudełkowy)** | `plt.boxplot(x)` | Pokazuje rozkład i wartości odstające (outliers) | `vert` – pionowy (`True`) lub poziomy (`False`)<br>`patch_artist` – kolor wnętrza pudełka | > plt.boxplot(df["popularity"], patch_artist=True) |



#### 💡Jak dobrać wykres do danych?

| Cel | Najlepszy wykres |
|------|------------------|
| Porównanie wartości między grupami | słupkowy (`bar`) |
| Zależność między dwiema cechami | punktowy (`scatter`) |
| Trend w czasie | liniowy (`plot`) |
| Rozkład wartości (np. oceny, tempo) | histogram (`hist`) |
| Udziały procentowe | wykres kołowy (`pie`) |
| Wykrywanie wartości odstających | boxplot |



> ##### 💡  Wskazówka 
>
> Reszta przyda się później, gdy zechcesz pokazać dane w różny sposób.  
> Z każdym wykresem możesz też używać tych samych komend opisowych: `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()`.
{: .block-tip }



#### Zadanie

1. Zrób wykres porównujący **średnią energię i popularność** dla kilku gatunków.
2. Zmień kolory wykresu – w `color=` możesz wpisać nazwę koloru np. `"salmon"` lub inny z dostępnych kolorów.  
3. Nie zapomnij dodać tytuł i podpisy osi tak, by ktoś inny wiedział, co ten wykres pokazuje.  

---

> ##### 💡  Wskazówka 
>
> Wizualizacja to nie tylko ozdoba firmowych prezentacji. Zawsze pamiętaj, że wykres jest sposobem, by przekazać wnioski w prosty i czytelny sposób.  
> Dzięki wykresom dane stają się opowieścią, którą każdy może zrozumieć.
{: .block-tip }


---

🎉 Brawo!  
Masz już nie tylko liczby, ale i obrazy, które potrafią coś powiedzieć o muzyce.  
W kolejnym rozdziale spróbujemy połączyć kilka wykresów i przygotować mały raport – prawie jak prawdziwy analityk danych.
