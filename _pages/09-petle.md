---
title: 9. Pętle
layout: post
---

Załóżmy, że chcemy coś zrobić kilka razy, np. wysłać 5 takich samych wiadomości, albo nadać identyfikator 30 kolejnym książkom w naszym księgozbiorze. Robienie kilkukrotnie tej samej rzeczy jest... nuuuudne i mało optymalne. 

Dlatego możemy wykorzystać pętle. 

Żeby powtórzyć coś kilkukrotnie potrzebujemy licznika - by wiedzieć, w którym momencie jesteśmy i czy powinnyśmy już skończyć, czy nadal powtarzać dany skrypt.

Załóżmy, że chcemy w konsoli napisać pięć razy wiadomość "Witajcie na kursie Pythona, adepci magii kodu!". Możemy to zrobić w ten sposób:


```python
print("Witajcie na kursie Pythona, adepci magii kodu!")
print("Witajcie na kursie Pythona, adepci magii kodu!")
print("Witajcie na kursie Pythona, adepci magii kodu!")
print("Witajcie na kursie Pythona, adepci magii kodu!")
print("Witajcie na kursie Pythona, adepci magii kodu!")
```

Trochę dużo pisania, prawda? Możemy ten kod uprościć!

## Pętla for 

Pętla for w Pythonie wygląda w następujący sposób:

```python
for zmienna in sekwencja:
    kod który chcemy powtórzyć
```
Np. sprawdź ten kod:

```python
for litera in "długi tekst":
    print("-", litera)
```

Żeby powtórzyć coś określoną liczbę razy, możemy skorzystać z funkcji `range()`, która tworzy sekwencję liczb:

```python
for i in range(5):
    kod który chcemy powtórzyć 5 razy
```

Przeróbmy nasz kod z wiadomością!

```python
for i in range(5):
    print("Witajcie na kursie Pythona, adepci magii kodu! ✨🧙‍♀️")
```

Funkcja `range()` może przyjmować różne parametry:
- `range(5)` - tworzy liczby od 0 do 4 (5 liczb)
- `range(1, 6)` - tworzy liczby od 1 do 5 
- `range(1, 11, 2)` - tworzy liczby od 1 do 10 co 2 (1, 3, 5, 7, 9)

```python
range(START, KONIEC, KROK)
```

Przetestuj przykłady powyzej:

Porównaj:

```python
for i in range(5):
    print("Liczba", i)

print("---koniec---")

for i in range(1, 6):
    print("Liczba", i)

print("---koniec---")

for i in range(3, 7):
    print("Liczba", i)

print("---koniec---")

for i in range(1, 11, 2):
    print("Liczby z krokiem co 2:", i)
```

Możemy też liczyć w dół:

```python
for i in range(5, 0, -1):
    print("Cześć! Miło nam Cię powitać na kursie Pythona!")
```

W tym przypadku:
- zaczynamy od 5
- kończymy przed 0 (czyli na 1)
- zmniejszamy o 1 (dlatego -1)

Spróbuj w swoim pliku Python zapisać powyższą pętlę.

*Dla chętnych: Spraw, by kod powtórzył się 10 razy.*

---------

### Czas na nasze książki w Magicznej Bibliotece! 

Chcemy dodać identyfikator (id) kolejnym 30 książkom.

Możemy to zrobić tak:

```python
print("id-1")
print("id-2")
print("id-3")
print("id-4")
print("id-5")
print("id-6")
# ...
print("id-30")
```

Ale taki kod zająłby bardzo wiele miejsca 🥺 
Wykorzystajmy więc pętle! Zauważmy, że tym razem powtarzamy tę samą czynność, jednak string, który chcemy wyświetlić, zmienia się. Zwiększa się dokładnie o 1. Podobnie zachowuje się nasz licznik!

Sprawdź co się wydarzy, gdy spróbujesz wyświetlić w konsoli wartość naszego licznika (to jest zmienna więc wystarczy wpisać jej nazwę).

```python
for i in range(30):
    print(i)
```

Konsola wyświetliła nam liczby od 0 do 29. W końcu `range(30)` tworzy liczby od 0 do 29. Gdy osiąga 30, zatrzymujemy pętlę. Musimy więc lekko przerobić naszą pętlę. Nasze id zaczyna się od 1, więc użyjemy `range(1, 31)` - zaczynamy od 1 i kończymy przed 31 (czyli na 30).

```python
for i in range(1, 31):
    print(i)
```

Super! Teraz dodajmy brakujący element id, czyli string "id-". Możemy do tego wykorzystać łączenie stringów. W Pythonie możemy łączyć stringi na kilka sposobów:

```python
for i in range(1, 31):
    print("id-" + str(i))
```

Zwróć uwagę, że musimy przekształcić liczbę `i` na string za pomocą `str(i)`, żeby móc ją połączyć ze stringiem "id-".

#### F-string
Możemy to również zrobić za pomocą f-stringów (formatowania stringów), co jest bardzo popularne w Pythonie:

```
f"Tekst tekst {dowolna_zmienna} tekst"
```

`dowolna_zmienna` moze być liczbą (`int` / `float`), a nawet boolean'em (`True/False`)!

> ##### Uwaga!
>
> Pamiętaj, ze nawiasy klamrowe są tutaj niezbędne `{` `zmienna` `}`

{: .block-warning }


```python
for i in range(1, 31):
    print(f"id-{i}")
```

### Interowanie po sekwencji

W Pythonie możemy również używać pętli `for` do iterowania po sekwencji np. tekście (stringu), listach i innych:

```python
for litera in "Python":
    print(litera)
```
Zobacz tez

```python
owoce = ["jabłko", "banan", "wiśnia"]
for owoc in owoce:
    print(owoc)
```


### 🧪 Zadanie 1

W Wielkiej Bibliotece Magii trwa porządkowanie zbiorów. Twoim zadaniem jako asystenta Czarodzieja jest **przypisanie identyfikatorów magicznym księgom**.

Księgi muszą mieć nadany identyfikator w formacie:

```
mag-1
mag-2
mag-3
...
mag-50
```

![]({{ site.baseurl }}/assets/books.gif)

### 🧪 Zadanie 2

Masz listę imion czarodziejów i czarownic, którym trzeba wysłać wiadomość o przyjęciu do Szkoły Magii i Czarodziejstwa w Hogwarcie.
Wiadomość zaczyna się od: Witaj + `<imię>`!, a potem dodajesz fragment listu, który zapisany jest w zmiennej.

Napisz program, który:
- Ma zdefiniowaną zmienną `list_tresc` (czyli treść listu),
- Ma listę imion, np. `["Hermiona", "Harry", "Ron", "Luna"]`,

Dla każdego imienia wypisuje spersonalizowaną wiadomość.

✨ Przykład działania:
Jeśli `list_tresc = "Z radością informujemy, że zostałeś przyjęty do Szkoły Magii i Czarodziejstwa w Hogwarcie!"`, to program powinien wypisać:

```
Witaj Hermiona! Z radością informujemy, że zostałeś przyjęty do Szkoły Magii i Czarodziejstwa w Hogwarcie!
Witaj Harry! Z radością informujemy, że zostałeś przyjęty do Szkoły Magii i Czarodziejstwa w Hogwarcie!
Witaj Ron! Z radością informujemy, że zostałeś przyjęty do Szkoły Magii i Czarodziejstwa w Hogwarcie!
Witaj Luna! Z radością informujemy, że zostałeś przyjęty do Szkoły Magii i Czarodziejstwa w Hogwarcie!
```



## Pętla while

Oprócz pętli `for` w języku Python występuje pętla `while`, której struktura wygląda tak:

```python
while wyrażenie_sprawdzające:
    kod który chcemy powtórzyć dopóki jest spełniany warunek
```

Pętla `for` jest wykonywana określoną ilość razy (gdy używamy `range()`). Pętla `while` działa, dopóki wyrażenie po słowie `while` jest prawdziwe (`True`).

Zauważ jednak, że w tej pętli nie ma automatycznego licznika. Dlatego często dodaje się go ręcznie. Wracając do naszej wiadomości do 5 osób:

```python
counter = 0
while counter < 5:
    print("Cześć! Miło nam Cię powitać na kursie Pythona!")
    counter += 1
```

Zmienną, która jest naszym licznikiem definiujemy przed pętlą. Przy każdej pętli zwiększamy licznik o 1 za pomocą `counter += 1`.

**Ważne:** Pamiętaj, żeby zawsze zwiększać licznik w pętli `while`, inaczej pętla będzie działać w nieskończoność!

Możemy też stworzyć pętlę while, która liczy w dół:

```python
counter = 5
while counter > 0:
    print("Cześć! Miło nam Cię powitać na kursie Pythona!")
    counter -= 1
```

### 🧪 Zadanie

Rozgrzewka: w swoim pliku napisz taką pętlę `while`, która 10 razy napisze w konsoli "Python to nie magia!".

## Kontrolowanie pętli 

Czasami chcemy przedwcześnie zakończyć pętlę lub pominąć pewne iteracje. Do tego służą słowa kluczowe `break` i `continue`.

### Słowo kluczowe break

`break` pozwala nam całkowicie wyjść z pętli, nawet jeśli warunek pętli nadal jest spełniony.

Załóżmy, że chcemy przeszukać długi tekst i znaleźć pierwszą literę "x". Gdy ją znajdziemy, nie musimy dalej szukać:

```python
tekst = "Python jest fantastyczny język programowania"
for litera in tekst:
    if litera == "x":
        print("Znaleziono literę x!")
        break
    print(f"Sprawdzam literę: {litera}")
```

Jeśli w naszym tekście nie ma litery "x", pętla przejdzie przez wszystkie znaki. 

**Ale** gdyby była, pętla zatrzymałaby się natychmiast po jej znalezieniu.

Spróbujmy z tekstem, który zawiera "x":

```python
tekst = "Python to świetny język do nauki programowania xD"
for litera in tekst:
    if litera == "x":
        print("Znaleziono literę x!")
        break
    print(f"Sprawdzam literę: {litera}")
```

Możemy też używać `break` w pętli `while`. Załóżmy, że chcemy prosić użytkownika o hasło, dopóki nie poda prawidłowego:

```python
poprawne_haslo = "python123"
while True:  # to będzie pętla nieskończona, ale...
    haslo = input("Podaj hasło: ")
    if haslo == poprawne_haslo:
        print("Hasło poprawne!")
        break  # ...użyjemy break, żeby z niej wyjść
    else:
        print("Hasło niepoprawne, spróbuj ponownie.")
```

### Słowo kluczowe continue

`continue` pozwala nam pominąć resztę kodu w danej iteracji pętli i przejść do następnej.

Załóżmy, że chcemy wypisać wszystkie litery z tekstu, ale pomijamy spacje:

```python
tekst = "Python jest super"
for litera in tekst:
    if litera == " ":
        continue  # pomijamy spacje
    print(f"Litera: {litera}")
```

Albo chcemy wypisać tylko litery, pomijając wszystkie znaki interpunkcyjne:

```python
tekst = "Witaj, świecie! Jak się masz?"
for znak in tekst:
    if znak in ".,!?":
        continue  # pomijamy znaki interpunkcyjne
    print(f"Znak: {znak}")
```

Możemy też łączyć `continue` z pętlami numerycznymi. Załóżmy, że chcemy wypisać liczby od 1 do 10, ale pomijamy liczby parzyste:

```python
for i in range(1, 11):
    if i % 2 == 0:  # jeśli liczba jest parzysta
        continue    # pomijamy ją
    print(f"Liczba nieparzysta: {i}")
```

### Łączenie break i continue

Możemy używać obu słów kluczowych w tej samej pętli. Załóżmy, że chcemy policzyć samogłoski w tekście, ale zatrzymać się, gdy znajdziemy cyfrę:

```python
tekst = "Python ma 6 literek"
samogloski = "aeiouAEIOU"
licznik_samoglosek = 0

for znak in tekst:
    if znak.isdigit():  # jeśli znajdziemy cyfrę
        print(f"Znaleziono cyfrę: {znak}")
        print(f"Zatrzymujemy liczenie. Znaleziono {licznik_samoglosek} samogłosek.")
        break
    
    if znak not in samogloski:  # jeśli to nie samogłoska
        continue  # pomijamy i idziemy dalej
    
    # jeśli doszliśmy tutaj, to znaczy że znak to samogłoska
    licznik_samoglosek += 1
    print(f"Znaleziono samogłoskę: {znak}")
```

Warto już teraz wiedzieć, że pętle w Pythonie są baaaaardzo wszechstronne i bardzo przydatne!

### 🧪 Zadanie 1

Napisz pętlę, która przejdzie przez string `"Programowanie w Pythonie to nie magia"` i:
- Wypisze każdą literę
- Zatrzyma się, gdy znajdzie literę "w".  Użyj `break` do zatrzymania pętli

### 🧪 Zadanie 2

Przed Tobą fragment tajemniczego stringu: `"Lumos Maxima! 9¾!"` i:
- Wypisze tylko LITERY (pomijając spacje, cyfry i znaki interpunkcyjne). Użyj `continue` do pomijania niechcianych znaków

💡 Podpowiedź: **istnieje w pythonie metoda, która sprawdzi czy znak jest literą czy nie**. 

💡 Dodatkowo możesz
- użyć `.upper()` lub `.lower()`, by wypisać zaklęcie w jednolitej formie
- sprawdzić jaki parametr w metodzie `print()` pozwoli zmienić znak końcowy tak by wyświetlić całe zaklęcie ciągiem a nie litera pod literą 😊🪄



### 🧪 Zadanie 3

Napisz program, który:
1. Przejdzie przez string "Uczę się programowania i czarowania w tym roku"
2. Będzie szukał liter "p", "r", "o", "g", "r", "a", "m" w tej kolejności
3. Pominie wszystkie inne znaki używając `continue`
4. Zatrzyma się gdy znajdzie wszystkie litery słowa "program" używając `break`
5. Wypisuje każdą znalezioną literę



## Pętla while z break i continue

Niby oczywiste, ale lepiej to zazaczyć. Tak! 
Możemy też używać `break` i `continue` w pętlach `while`. 

Oto przykład prostego menu przetestuj go:

```python
while True:
    print("\n--- MENU ---")
    print("1. Powitaj się")
    print("2. Powiedz coś miłego")
    print("3. Wyjdź")
    
    wybor = input("Wybierz opcję (1-3): ")
    
    if wybor == "1":
        print("Cześć! Miło Cię poznać!")
        continue  # wracamy do początku pętli (pokazujemy menu ponownie)
    
    if wybor == "2":
        print("Jesteś wspaniałą osobą!")
        continue
    
    if wybor == "3":
        print("Do widzenia!")
        break  # wychodzimy z pętli
    
    # jeśli użytkownik wpisał coś innego
    print("Nieprawidłowy wybór, spróbuj ponownie.")
```

### 🪄 Zadanie

Twoja różdżka jeszcze nie została dostrojona. Aby ją aktywować, musisz wybrać swój **kolor mocy**.

1. Napisz program z pętlą `while`, który pyta użytkownika o jego ulubiony kolor.
2. Jeśli poda `"czerwony"`, `"zielony"` lub `"niebieski"` – wyświetl komunikat: `"Doskonale! Twoja różdżka rezonuje z tym kolorem."` i zakończ program (`break`)
3. Jeśli poda `"czarny"` – wyświetl `"To nie jest kolor mocy! Spróbuj jeszcze raz."` i wróć do pytania (`continue`)
4. Dla wszystkich innych kolorów – wyświetl `"Interesujący wybór! Ale spróbuj jeszcze raz..."` i wróć do pytania
5. Użyj `break` i `continue`, aby kontrolować działanie pętli

💡 *Program powinien działać, dopóki nie zostanie wybrany odpowiedni kolor magiczny.*


![]({{ site.baseurl }}/assets/wand.webp)

### 🪄 Zadanie liczby 

Twoim celem jest rzucić skuteczne zaklęcie – ale najpierw musisz odgadnąć tajną liczbę. 
Każda wersja zadania jest trochę trudniejsza niż poprzednia.

🔹 A. Podstawowa
- Zapisz do zmiennej jakąś tajną liczbę (np. 7).
- Poproś użytkownika, żeby wpisał liczbę i próbował ją zgadnąć.

W pętli sprawdzaj:
- jeśli wpisał za małą liczbę – wypisz „Zaklęcie za słabe!”
- jeśli za dużą – wypisz „Zaklęcie za potężne!”
- jeśli zgadł – wypisz „Brawo! Trafiłeś dokładnie!” i zakończ

🔹 B. Ciut trudniej
Wylosuj tajną liczbę z zakresu 1–20.
Poproś użytkownika o zgadywanie, aż trafi.
W zależności od tego, jak bardzo się pomylił:
- jeśli różnica między jego liczbą a tajną jest mała (do 2) → wypisz „Ciepło – czujesz magię!”
- jeśli różnica jest większa → wypisz „Zimno – brrr!”
- jeśli trafił → wypisz „Brawo!” i zakończ

🔹 C. Wartosć bezwzględna ;)
Wylosuj tajną liczbę z zakresu 1–20.
Użytkownik zgaduje aż trafi.
Po każdej próbie:
- sprawdź, czy nowa próba jest bliżej czy dalej od poprzedniej (uzyj funkcji `abs()`)

wypisz:

- „Cieplej – jesteś bliżej źródła magii!” jeśli jest lepiej
- „Zimniej – oddalasz się od magii!” jeśli gorzej
- „Brawo! Trafiłeś dokładnie!” jeśli trafił