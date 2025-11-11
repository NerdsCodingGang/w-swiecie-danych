---
title: 12. Funkcje
layout: post
---

**Uwaga:** Dobrą praktyką jest pisanie kodu w języku angielskim - nazwy zmiennych, funkcji i komentarzy. Dzięki temu kod jest uniwersalny i zrozumiały dla programistów z całego świata.

Czasami chcemy wykonywać podobne rzeczy dla różnych wartości. Np. chcemy pomalować całe mieszkanie i musimy policzyć powierzchnię ścian dla każdego pokoju. Mamy pokoje o różnych wymiarach, ale samo liczenie będzie wyglądać dokładnie tak samo:

- Malujemy pokój o wymiarach 6m x 5m i wysokości 2,5 m.

- Sumujemy szerokości ścian: 2*6 + 2*5 = 22

- Wyliczamy powierzchnię ścian: 22 × 2,5 = 55

- Wyliczamy powierzchnię sufitu: 6 × 5 = 30

- Dodajemy powierzchnię ścian i sufitu: 55 + 30 = 85


![]({{ site.baseurl }}/assets/room.gif)

I tak dla 7 różnych pomieszczeń w naszym domu. Ale możemy to skrócić. W końcu chodzi o to, by zrobić coś takiego:

```python
x = jedna_sciana
y = druga_sciana
z = wysokosc
szer_scian = 2*x + 2*y
pow_scian = szer_scian * wysokosc
pow_sufitu = x * y
pow_malowania = pow_scian + pow_sufitu
```

Nasze zmienne elementy to x, y i z.

Do wykonywania takich czynności przyda nam się funkcja. Definicja funkcji wygląda następująco:

```python
def nazwa_funkcji():
    # co ma się wydarzyć

# np.:
def greeting():
    print('Hello World!')
```

Teraz funkcję należy wywołać:

```python
nazwa_funkcji()
greeting()
```

Przy każdym wywołaniu funkcji zadziała ona tak samo.

Ale co z naszymi zmiennymi parametrami? Otóż w nawiasach przy nazwie funkcji określmy właśnie te parametry. Np.

```python
def greeting(name):
    print('Hello ' + name)
```

Przy wywołaniu w miejscu parametru należy wstawić istniejące dane, np.

```python
greeting('Marta')
# >>> Hello Marta
greeting('Ania')
# >>> Hello Ania
```

Wróćmy do liczenia powierzchni: nasze zmienne parametry to szerokość jednej ściany, drugiej ściany i wysokość, czyli:

```python
def painting_area(wall_1, wall_2, height):
    # ....
```

Teraz wnętrze naszej funkcji:

```python
def painting_area(wall_1, wall_2, height):
    x = wall_1
    y = wall_2
    z = height
    walls_width = 2*x + 2*y
    walls_area = walls_width * height
    ceiling_area = x * y
    total_painting_area = walls_area + ceiling_area
    
    print(total_painting_area)
```

I jej wywołanie:

```python
painting_area(6, 5, 2.5)
painting_area(3, 4, 2.5)
```

### 🧪 Zadanie 1

W swoim pliku Python napisz funkcję o nazwie `hello_nerds_coding_gang`, która po wywołaniu wyświetli następujący napis: "Cześć, [tu poda imię osoby podanej w wywołaniu]! Witaj na warsztatach!".

```python
# Przykład wywołania:
hello_nerds_coding_gang('Anna')
# >>> Cześć, Anna! Witaj na warsztatach!
```

### 🧪 Zadanie 2

Przeanalizuj poniższy kod

```python
def menu(option):
    if option == 1:
        print("Jeden")
    elif option == 2:
        print("Dwa")
    elif option == 3:
        print("Trzy")
    elif option == 4:
        print("Cztery")
    else:
        print("Ohooo")


menu(1)
choice = 2
menu(choice)
menu(4)
```

Na podstawie powyższego kodu utwórz menu użytkownika, w którym:

Program wyświetla użytkownikowi listę kategorii posiłków:
```
1 – Śniadanie
2 – Obiad
3 – Kolacja
4 – Deser
```
- Użytkownik wpisuje numer kategorii (1–4).
- Program odpowiada konkretną propozycją posiłku w zależności od wybranej kategorii.
- Jeśli użytkownik wpisze inną liczbę niż 1–4, program wyświetla komunikat, ze nie zna takiego dania 

**Przykład działania**
```
Wybierz kategorię posiłku:
1 - Śniadanie
2 - Obiad
3 - Kolacja
4 - Deser
Podaj numer kategorii: 2
Propozycja na obiad: Pieczone tofu z ziemniakami i fasolką szparagową.
```



### 🧪 Zadanie 3

🎁 Co na prezent? Stwórz program, który: Zawiera listę pomysłów na prezent dla Twoich bliskich (np. książka, bilety do kina, zestaw herbat).

Program:
- losowo wybiera jeden prezent z listy ( przyda się moduł `random`),
- (opcjonalnie) podpowiada miejsce, gdzie można go kupić (np. Empik, Allegro, lokalny sklep).



### 🧪 Zadanie 4
```
    +
   +++
  +++++
 +++++++
+++++++++
```

- użytkownik podaje rodzaj znaku
- użytkownik podaje wysokość choinki
- znak użytkownika nie może być literą ani cyfrą

### 🧪 Zadanie 5
Zakoduj tajną wiadomość 🕵️
```
PYTHON JEST SUPER
```

- stwórz plik `secret1.py` zaawierający algorytm, który zmieni powyższą wiadomość w ciąg ”RZUIPO-KFTU-TWRFS”
- wymyśl własny algorytm kodujący (możesz skorzystać z istniejących np. klasyczne/harcerskie) jako `secret2.py`
- napisz program `secret3.py`, które odkoduje twoją wiadomość

### 🧪 Zadanie 6
Śledź robota 🤖 Robot porusza się w płaszczyźnie zaczynając od pierwotnego punktu (0,0). Robot może poruszać się w GÓRĘ, W DÓŁ, ​​W LEWO i W PRAWO, wykonując określone kroki. Ślad ruchu robota pokazano następująco:
```
UP 5
DOWN 3
LEFT 3
RIGHT 2
```
Liczby po kierunku są krokami. Napisz program do odczytu wskazówek podanych jak wyżej i oblicz odległość od aktualnej do startowej pozycji. Jeśli odległość jest liczbą dziesiętną, wyświetl po prostu najbliższą liczbę całkowitą.

Przykład:
```
UP 5
DOWN 3
LEFT 3
RIGHT 2
```

Wynik: `3`

![Wynik]({{ site.baseurl }}/assets/result.png)


### 🧪 Zadanie 7
Stwórz grę inspirowaną miłosną wróżbą z czasów szkolnych. Zasady gry przedstawia to [wideo](https://www.youtube.com/watch?v=oFsLVG7EAZ4).
1. Pobierz imiona zakochanych
2. Policz wystąpienia każdej z liter w obu imionach oraz słowie LOVE.
3. Redukuj liczbę elementów tablicy dodając pierwszą i ostatnią liczbę do siebie, tak długo, aż zostaną dwie cyfry.
4. Dwie ostatnie cyfry tworzą wartość procentową dopasowania pary wg. wróżby.

Mało? 
Przejdź do kolejnej lekcji!