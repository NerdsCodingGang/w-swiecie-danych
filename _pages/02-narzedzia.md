---
title: 2. Narzędzia
layout: post
---

By zacząć pisać kod, nie potrzeba wiele.  
Na początek wystarczy przeglądarka internetowa i miejsce, w którym będziemy pisać i uruchamiać nasze pierwsze linijki Pythona 🐍  

Nie musisz niczego instalować na swoim komputerze – użyjemy **Google Colab**, czyli darmowego środowiska do nauki kodu w chmurze.  

---

## ☁️ Google Colab

**Google Colab** to darmowe narzędzie od Google, które pozwala pisać i uruchamiać kod Pythona bez żadnej instalacji.  
Wszystko działa w przeglądarce, a Twoje notatki możesz zapisać na Dysku Google. O taki notatkik w chmurze!

🔗 Otwórz: [https://colab.research.google.com](https://colab.research.google.com)

1️⃣ Zaloguj się na swoje konto Google.  
2️⃣ Wybierz **“New Notebook” / „Nowy notatnik”**.  
3️⃣ Zmień nazwę notatnika na coś w stylu **“DataScience_Workshop”**.  
4️⃣ Gotowe! Teraz możesz pisać kod i uruchamiać komórki (Shift + Enter).  

💬 Każda komórka to jak mały eksperyment, mini kod pythona możesz do niej wstawić kod, tekst lub wykres.  
To właśnie w Colabie będziemy pracować z danymi w dalszych rozdziałach.

![Colab]({{ site.baseurl }}/assets/02-google-colab.png){:title="google colab" class="img-responsive"}

---

## Chwila... ale co to ten Colab?

Dobrze, że pytasz!

Google Colab to coś pomiędzy:
- **zeszytem z notatkami**,  
- a **środowiskiem wykonawczym dla jezyka programowania python**
- dla niektórych, którzy coś już gdzieś dłubali może przypominać też Jupyer Notebook i będzie to całkiem słuszne skojarzenie.

Możesz pisać tu kod, dodawać komentarze i od razu zobaczyć efekty.  
Nie musisz się martwić o instalacje bibliotek większość narzędzi, jak **pandas**, **matplotlib** czy **scikit-learn**, jest już dla nas dostępne.

Notatniki Colab uruchamiają kod na serwerach Google w chmurze, co oznacza, że możesz korzystać z mocy obliczeniowej sprzętu Google, a więc niezależnie od mocy Twojego komputera. Potrzebujesz tylko przeglądarki, nawet jeśli Twój laptop jest zupełnie słaby czy "stary" lub pracujesz na tablecie (a dla już prawidziwych masochistów na telefonie 😳 ).

---

## 💻 Alternatywnie: lokalnie z VS Code

Jeśli chcesz rozwijać się dalej po warsztatach i pisać projekty samodzielnie, warto mieć lokalne środowisko.

👉 Zainstaluj **[Visual Studio Code (VS Code)](https://code.visualstudio.com/)**  

To darmowy edytor kodu z:
- kolorowaniem składni,  
- podpowiedziami,  
- integracją z GitHubem i terminalem.  

Zainstalujesz go raz i możesz używać do Pythona, HTML-a, Javy czy czegokolwiek innego ✨  

Na warsztatach skupiamy się na Colabie, ale VS Code przyda Ci się później, jeśli chcesz pisać własne projekty lub portfolio. Jeśli chcesz, możesz korzystać, my będziemy jednak używać Colaba ;) 

PS: jeśli mimo wszystko decydujesz się na VSC dodaj wtyczkę  do Pythona 

![VSC]({{ site.baseurl }}/assets/vsc-python.png){:title="VSC wtyczka Python" class="img-responsive"}

---

## 📦 Dodatkowe narzędzia, które się przydają

| Narzędzie | Do czego służy | Link |
|------------|----------------|------|
| 🧮 Google Sheets | szybkie podglądy danych | [https://sheets.google.com](https://sheets.google.com) |
| 📊 Kaggle | do pobierania zestawów danych (CSV) i nauki | [https://www.kaggle.com](https://www.kaggle.com) |
| 💾 GitHub | do przechowywania kodu i dzielenia się projektami | [https://github.com](https://github.com) |

---

## ✨ Pierwszy krok w Colabie

1. Zmień tytuł notatnika na np. Zrozum dane z NCG

2. Utwórz komórkę tekstową i dodaj tam opis tego notatnika np. "moje notatki z warsztatów z nerds coding gang".

3. Utwórz kolejną komórkę tym razem "kodową".

4. Spróbuj wpisać poniższy kod w nowej komórce i uruchom go skrótem **Shift + Enter** lub znakiem startu obok komórki:

```python
print("Hello, Data Science! 🎉")
```

Jeśli zobaczysz komunikat Hello, Data Science! 🎉 — to znaczy, że Twój notatnik działa i jesteś gotowa/gotowy do dalszej nauki 💪

To zróbmy jeszcze jedną rzecz, spróbuj zrobić pętlę, która wyświetli napis "Hello, Data Science! 🎉" 10 razy: oto twój kod startowy, pokombinuj, nie bój się eksperymentować:

```python
for number in range(10):
    print(numer)
```


Zastanów się co się stało z tym kodem poniżej:

```python
names_list = ["Ada", "Julia", "Gleam"]
for name in names_list:
    print(name)
```

Jeśli ten kod wydaje się zatrudny poproś o pomoc mentorów ;) 

###  🎉 Świetnie!
W kolejnych rozdziałach poznamy podstawy Pythona, nasze pierwsze zbiory danych i nauczymy się, jak je otworzyć w Colabie i podejrzeć ich zawartość.