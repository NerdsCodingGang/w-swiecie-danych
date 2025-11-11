---
title: 6. Pierwsze analizy danych
layout: post
---

Rozdział 4 przeprowadził nas przez proces oczyszczania danych czyli sprawdzania, czy wszystko z danymi jest w porządku.  
Czas zrobić coś ciekawszego: policzyć kilka prostych statystyk i spróbować zrozumieć, **co te dane nam mówią.**

---

## 📈 Po co liczymy statystyki?

Statystyki opisowe pomagają szybko zorientować się, jak wyglądają dane:
- jaka jest średnia wartość,
- jak duży jest rozrzut,
- czy coś wygląda nietypowo albo niespodziewanie.

Nie potrzebujemy do tego żadnej matematyki wyższej. Prawda jest taka, że nie będziemy przeciez liczyć na piechotę średniej z setki jak i tysięcy danych prawda? Python ma już to wszystko dla nas przygotowane.

---

## 🔢 Podstawowe statystyki dla kolumn liczbowych

Zacznijmy od tego, by sprawdzić kilka prostych informacji o liczbowych kolumnach, takich jak tempo, popularność i energia.

```
df_small[["tempo", "popularity", "energy"]].describe()
```

Funkcja `describe()` pokazuje najważniejsze liczby:
- **count** – ile wartości jest w kolumnie,  
- **mean** – średnia,  
- **min** i **max** – wartości skrajne,  
- **std** – odchylenie standardowe (czyli jak bardzo dane są rozrzucone).

Jeśli teraz łapiesz się za głowę ile jest tych wszystkich funkcji i poleceń, nie martw się.
Znowu przypominamy: nie musisz nauczyć komend na pamięć, zależy nam by uczyć się **czytać takie tabele** i zauważać różnice.

---

## Średnia, minimum i maksimum

Możesz też obliczyć te wartości pojedynczo, dla jednej kolumny.

> df_small["tempo"].mean()  
> df_small["tempo"].min()  
> df_small["tempo"].max()

Spróbuj to samo zrobić dla popularności:

> df_small["popularity"].mean()  
> df_small["popularity"].min()  
> df_small["popularity"].max()

Pomyśl chwilę, jak można interpretować te liczby:  
czy średnie tempo utworów jest wysokie, czy raczej umiarkowane?  
czy popularność rozkłada się równomiernie, czy większość utworów ma podobny wynik?

---

## 📊 Zależności między kolumnami

Zobaczmy, czy cechy takie jak tempo, energia i taneczność są ze sobą powiązane.

```python
df_small[["tempo", "energy", "danceability"]].corr()
```

`corr()` to funkcja, która liczy **korelację** czyli współzależność między wartościami.  

Wyniki są w przedziale od -1 do 1:
- wartości **bliskie 1** oznaczają silne powiązanie (im większa energia, tym większe tempo),  
- wartości **bliskie 0** oznaczają brak związku,  
- wartości **ujemne** oznaczają, że im jedna rośnie, tym druga maleje.

Słowem niektóre cechy „idą razem”.

---

## 🎶 Grupowanie danych

Teraz spróbujmy porównać różne gatunki muzyczne.  
Zobaczymy, które z nich są najbardziej popularne, oczywiście... średnio.

```python
df_small.groupby("track_genre")["popularity"].mean().sort_values(ascending=False).head(10)
```

Brrrryyy straszna ta komenda co nie? 

Ale przeczytaj jeszcze raz tę komendę jak zupełnie zwykły język angielski.

Ta komenda:
1. grupuje dane według gatunku `groupby`,
2. liczy średnią popularność w każdej grupie `mean`,
3. sortuje wyniki  `sort_values` od najwyższej do najniższej `ascending`
4. `head()` już dobrze znasz!

Wynik to pierwsza mała analiza coś co można pokazać na wykresie albo w raporcie.

---

## Jak interpretować wyniki?

Zobacz, jakie gatunki znalazły się na górze listy.  
Czy są to szybkie i taneczne utwory?  
Czy może spokojniejsze style, ale bardziej popularne wśród słuchaczy?

Brawo! 👏👏👏

Widzimy właśnie moment, w którym dane zaczynają „mówić”.

---

## Zadanie

1. Policz średnią wartość energii dla każdego gatunku:  
   > df_small.groupby("track_genre")["energy"].mean().sort_values(ascending=False).head(10)

2. Zrób to samo dla taneczności:  
   > df_small.groupby("track_genre")["danceability"].mean().sort_values(ascending=False).head(10)

3. Zastanów się, czy gatunki z wysoką energią mają też wysoką taneczność.  
   Możesz o tym napisać jedno lub dwa zdania w komórce tekstowej w Colabie.

---

🎉 Brawo!  
Właśnie masz za sobą pierwszą prawdziwą analizę danych.  
Umiesz już policzyć podstawowe statystyki, porównać grupy i zauważyć zależności.  
Niedługo dowiesz się jak to wszystko pięknie **zwizualizować** na wykresach.
