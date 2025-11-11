---
title: 8. Twój raport
layout: post
---

 
Dotarliście naprawdę daleko, dlatego teraz spróbujemy połączyć wszystko, czego się nauczyliśmy — i przygotować **mini-raport z analizy danych o utworach ze Spotify**.
Czas opowiedzieć opowiedzieć historię za pomocą danych.

Co zrobimy?

1. Wybierzesz jedno pytanie badawcze.  
2. Zrobisz proste obliczenia.  
3. Narysujesz 2–3 wykresy, które pokażą Twoje wnioski.  
4. Napiszesz krótkie podsumowanie — tak jak zrobiłby to analityk danych w raporcie.  



## Wybierz jedno pytanie badawcze

Oto kilka przykładów, które możesz wykorzystać (albo wymyśl własne):

- Czy szybsze utwory są bardziej popularne?  
- Które gatunki mają najbardziej energetyczne utwory?  
- Czy taneczność utworów rośnie wraz z energią?  
- Jakie gatunki dominują w całym zbiorze danych?  

Zapisz swoje pytanie w komórce tekstowej w Colabie jako tytuł (znak `#` na początku tekstu)  →  to będzie temat Twojego mini-projektu.


## Przygotuj dane

W większości przypadków wystarczy Ci `df_small`.  
Możesz też utworzyć mniejszą wersję zawierającą tylko kolumny, które Cię interesują, np.:

> df_project = df_small[["track_name", "artists", "popularity", "tempo", "energy", "danceability", "track_genre"]]

Jeśli potrzebujesz policzyć średnie lub pogrupować dane — użyj `groupby()` lub `describe()`.  
Nie szukaj nowych danych — skup się na tym, żeby wyciągnąć ciekawy wniosek z tego, co już masz.



## Stwórz 2–3 wykresy

Wybierz różne typy wykresów, które najlepiej pokazują Twoje dane (poprzedni rozdział)

Każdy wykres opisz: co pokazuje, jakie wnioski można z niego wyciągnąć.  

Pamiętaj o dodaniu tytułów i podpisów osi:
> plt.title("Twój tytuł")  
> plt.xlabel("Oś X")  
> plt.ylabel("Oś Y")



## Napisz krótkie podsumowanie

W komórce tekstowej w Colabie odpowiedz na pytanie:

> Co odkryłam / odkryłem w danych?

To może być 3–5 zdań, w których:
- opiszesz, co udało się zauważyć,  
- wskażesz ciekawe zjawisko lub zależność,  
- podsumujesz najważniejszy wniosek.  

Przykład:

> Dane pokazują, że gatunki o [wyższej/niższej] tempie i energii są częściej popularne.  
> [Najbardziej/mniej] energetyczne style, takie jak [dane], mają najwyższe średnie wartości popularności.  
> Nie wszystkie szybkie utwory są jednak taneczne — tempo nie zawsze oznacza rytmiczność.

---

## 🎁 Dodatkowe wyzwanie (dla chętnych)

Jeśli chcesz pójść krok dalej:
- spróbuj połączyć kilka wykresów w jednym `plt.figure()` (np. dwa obok siebie),
- dodaj własną kolorystykę lub styl,
- zapisz raport do pliku `.ipynb` i dodaj go na GitHub lub Dysk Google jako twoje analityczne portfolio.

---

💬 **Na koniec:**
Gratulacje! 🎉  

To Twój pierwszy *data story*.  
I właśnie od takich historii zaczyna się praca z danymi. 💪
