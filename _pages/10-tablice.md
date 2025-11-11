---
title: 10. Listy
layout: post
---

Zmienne, które dotychczas uzywamy, zawierały tylko jeden element - string, liczbę, czy wartość logiczną. Czasami jednak musimy skorzystać z całej listy danych. Do ich przechowywania służą nam listy zwane tez tablicami.

```python
pusta_lista = []
lista = ["kapelusz", 34, True, "eliksir", 45, [67, 56, "czerwony"]]
```
Wyświetl te dwie zmienne.

Jak widać, listę tworzymy zapisując dane pomiędzy kwadratowymi nawiasami i oddzielając te elementy od siebie przecinkami. W liście możemy przechowywać różne typy danych: stringi, liczby, zmienne typu logicznego, a nawet inne listy.

Stwórzmy np. listę znajomych:

```python
friends = ["Michał", "Marta", "Mikołaj", "John", "Natalia", "Ania"]
```

Aby wyświetlić element listy, odwołujemy się do listy i pozycji danego elementu.

UWAGA!

Kolejność elementów liczymy od 0. Tak więc:

```python
print(friends[0])
# >>> Michał

print(friends[3])
# >>> John
```

W swoim pliku Python stwórz teraz listę o nazwie "group", która zawiera imiona wszystkich osób z Twojej grupy, z którą pracujesz na warsztatach. Następnie wypisz w konsoli imię pierwszej i ostatniej zapisanej osoby.

Podobnie jak stringi, długość listy możemy ustalić dzięki funkcji **len()** jak i skorzystać z ujemnego indeksu.

```python
print(len(friends))
# >>> 6
```

**Dodajmy kolejne imię**

Do dodawania nowego elementu służy metoda **append()**:

```python
friends.append('Kasia')

print(friends)
# >>> ["Michał", "Marta", "Mikołaj", "John", "Natalia", "Ania", "Kasia"]
```

Za jej pomocą dodajemy nowy element na końcu listy.

Dodaj do swojej listy "group" jeszcze jedno dowolne imię używając do tego metody `append()`, a następnie wypisz je w konsoli.

Możemy również nadpisać istniejący element listy o określonej pozycji:

```python
friends[2] = "Tomek"

print(friends)
# >>> ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
```

Nadpisz ostatnio dodane do swojej listy imię innym. Raz jeszcze wypisz ostatnie imię w konsoli.

Różne listy możemy dodać do siebie. 

Do listy z imionami osób z grupy i chcemy dodać drugą listę z imionami przyjaciół z grupy obok.

Aby stworzyć listę, w której znajdą się imiona wszystkich Twoich przyjaciół, możemy użyć operatora `+`:

```python
work_friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
next_table = ["Asia", "Kamil", "Bartek", "Ola", "Weronika", "Czarek"]

all_friends = work_friends + next_table

print(all_friends)
# >>> ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia", "Asia", "Kamil", "Bartek", "Ola", "Weronika", "Czarek"]
```

Możemy też użyć metody `extend()`, która dodaje wszystkie elementy z jednej listy do drugiej.

```python
work_friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
next_table = ["Asia", "Kamil", "Bartek", "Ola", "Weronika", "Czarek"]

work_friends.extend(next_table)
print(work_friends)
# >>> ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia", "Asia", "Kamil", "Bartek", "Ola", "Weronika", "Czarek"]
```

❓ Sprawdź w konsoli, jak wygląda nowa lista powstała za pomocą `+` lub `extend()`. Czy widzisz róznice w sposobie ich uzywania? 

By "pobrać" kawałek listy używamy mechanizmu nazywanego "slicing" (krojenie). Określamy od którego elementu chcemy ciąć i na którym chcemy skończyć:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]

part = friends[1:4]
print(part)
# >>> ["Marta", "Tomek", "John"]
```

Zwróć uwagę, że `friends[1:4]` oznacza elementy od pozycji 1 (**włącznie**) do pozycji 4 (**wyłącznie**). Czyli na ostatnim elemencie się zatrzymaj i go nie wliczaj.

Stwórz teraz jeszcze jedną listę, której elementami będą pierwsze i drugie imię z listy "group". Użyj do tego slicing.

Do usuwania elementów z listy służy kilka metod:

**Metoda pop()** - usuwa i zwraca ostatni element (lub element o określonej pozycji):

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]

usuniety_element = friends.pop()
print(usuniety_element)  # >>> Kasia
print(friends)           # >>> ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania"]

# Możemy też usunąć element o konkretnej pozycji:
friends.pop(2)
print(friends)           # >>> ["Michał", "Marta", "John", "Natalia", "Ania"]
```

**Metoda remove()** - usuwa pierwsze wystąpienie określonego elementu:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]

friends.remove("Tomek")
print(friends)
# >>> ["Michał", "Marta", "John", "Natalia", "Ania", "Kasia"]
```

**Słowo kluczowe del** - usuwa element o określonej pozycji:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]

del friends[2]
print(friends)
# >>> ["Michał", "Marta", "John", "Natalia", "Ania", "Kasia"]
```

Usuń teraz za pomocą jednej z powyższych metod pierwsze imię z listy "group".

### Wstawienie elementu w określone miejsce

Do wstawienia elementu w konkretne miejsce służy metoda **insert()**:

```python
friends = ["Michał", "Marta", "John", "Natalia", "Ania", "Kasia"]

friends.insert(2, "Patrycja")
print(friends)
# >>> ["Michał", "Marta", "Patrycja", "John", "Natalia", "Ania", "Kasia"]
```

Pierwszy parametr to pozycja, w którą chcemy wstawić element, drugi to wartość elementu.

### Wyszukiwanie elementu

Do wyszukiwania pozycji elementu służy metoda **index()**. Zwraca ona indeks danego elementu lub wywołuje błąd, jeśli go nie znajdzie:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
pozycja = friends.index("Marta")
print(pozycja)
```

ale

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
pozycja = friends.index("Adam") # błąd!
print(pozycja)
```

Stąd:

```python
if "Marta" in friends:
    pozycja = friends.index("Marta")
    print(f"Marta znajduje się na pozycji {pozycja}")
else:
    print("Marty nie ma w tej liście")
```

Możemy też sprawdzić, czy element istnieje w liście używając operatora **in**:

```python
if "Marta" in friends:
    print("Marta znajduje się w tej liście!")
else:
    print("Marty nie ma w tej liście")
```

Korzystając z `index()` sprawdź jaką pozycję ma Twoje imię w liście "group".

### Pętla po liście

Pętla to doskonały sposób przechodzenia (iterowania) po elementach listy. Wykorzystajmy ją do wypisania naszych znajomych. Aby wypisać jakiś element listy, określamy jego indeks:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]

print(friends[0])
print(friends[1])
print(friends[2])
print(friends[3])
# ...
```

Ale pojawiają się dwa problemy. Po pierwsze, będzie to mało optymalne. Po drugie, co jeśli nie wiem ile jest elementów na liście i jak długo mam powtarzać ten sam kod?

Spróbujmy więc pętli `for` z `range()`:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
for i in range(len(friends)):
    print(friends[i])
```

Używamy `range(len(friends))`, co da nam liczby od 0 do długości listy minus 1 - dokładnie to, czego potrzebujemy do indeksowania.

Ale Python oferuje jeszcze prostszy sposób - możemy iterować bezpośrednio po elementach listy:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
for friend in friends:
    print(friend)
```

To jest najbardziej pythonowy (prawdziwie pythoński) sposób! 🐍

Przećwiczmy to jeszcze wracając do naszej wiadomości. Powiedzmy, że chcemy ją spersonalizować i wyświetlić, np.

> "Cześć Michał! Miło nam Cię powitać na kursie Pythona!"

Wystarczy do naszej wcześniejszej pętli dodać brakujący tekst powitania:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
for friend in friends:
    print(f"Cześć {friend}! Miło nam Cię powitać na kursie Pythona!")
```

Możemy też użyć łączenia stringów:

```python
for friend in friends:
    print("Cześć " + friend + "! Miło nam Cię powitać na kursie Pythona!")
```

### 🧪 Zadanie

Używając pętli `for` spraw, aby w konsoli pojawił się napis witający na kursie Pythona wszystkie osoby zapisane w Twojej liście "group". Tekst ma być następujący: "Cześć \[tu imię osoby\]! Miło nam Cię powitać na kursie Pythona!".

### Ciekawostka: Enumerate 

- gdy potrzebujemy i indeksu i wartości. Czasami potrzebujemy zarówno indeksu elementu, jak i jego wartości. Do tego służy funkcja `enumerate()`:

```python
friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania", "Kasia"]
for i, friend in enumerate(friends):
    print(f"{i}: {friend}")
```

To wypisze:
```
0: Michał
1: Marta
2: Tomek
3: John
4: Natalia
5: Ania
6: Kasia
```

### 🧪 Zadanie

W starym notatniku profesora zaklęć odnaleziono dziwną wiadomość:

> "Verba tantum huius scripti quae septem litteris longiora sunt verissima huius incantationis pars sunt — sed ea intellegit tantum is, cui mens sapientia illuminata est."

Legenda głosi, że **tylko słowa dłuższe niż 7 liter** są prawdziwymi składnikami zaklęcia, które można aktywować.

Twoje zadanie:

1. Zapisz ten tekst do zmiennej `tekst`  
2. Podziel go na słowa (użyj pewnej metody typu string)  
3. Utwórz pustą listę `zaklecie`  
4. Przejdź przez każde słowo w pętli i:
   - jeśli ma więcej niż 7 znaków, dodaj je do listy `zaklecie`
5. Na końcu wypisz zawartość listy `zaklecie` – to Twoje aktywne słowa mocy ✨

> ##### 💡 Podpowiedź
>
> Możesz usunąć znaki interpunkcyjne przed sprawdzaniem długości słowa (`.strip(".,")`)
> Bonus: swoje zaklęcie wynikowe połączyć w jeden tekst metodą `join()`
{: .block-tip }



### Dodatkowe metody list

Python oferuje wiele przydatnych metod do pracy z listami:

**count()** - zlicza wystąpienia elementu:
```python
lista = [1, 2, 3, 2, 2, 4]
print(lista.count(2))  # >>> 3
```

**reverse()** - odwraca listę:
```python
lista = [1, 2, 3, 4, 5]
lista.reverse()
print(lista)  # >>> [5, 4, 3, 2, 1]
```

**sort()** - sortuje listę:
```python
lista = [3, 1, 4, 1, 5, 9, 2, 6]
lista.sort()
print(lista)  # >>> [1, 1, 2, 3, 4, 5, 6, 9]
```

**clear()** - usuwa wszystkie elementy z listy:
```python
lista = [1, 2, 3, 4, 5]
lista.clear()
print(lista)  # >>> []
```

### 🧪 Zadanie: Najpotężniejsza liczba

Masz listę liczb przedstawiających moc magicznych iskier:
```
moce = [3, 7, 2, 9, 5, 9, 4]
```

Twoim zadaniem jest:

1. Wypisać wszystkie moce po kolei
2. Znaleźć największą moc (czyli najpotężniejszą iskrę!)
3. Wypisać wszystkie moce równe tej największej (jeśli jest ich więcej niż jedna)

Spróbuj to zrobić za pomocą pętli bez metody `max()`

> ##### 🧙‍♀️  WSKAZÓWKA
>
> Użyj zmiennej `max_moc`, która na początku ma wartość `0`.  
> W pętli `for` porównuj każdą moc i aktualizuj `max_moc`, jeśli znajdziesz większą.
{: .block-tip }

![]({{ site.baseurl }}/assets/elixir.gif)

### 🧪 Zadanie: Inwentarz eliksirów

Profesor Infusora, mistrzni naparów, zostawiła na tablicy nieuporządkowaną listę eliksirów przygotowanych na czarodziejskie egzaminy. Twoim zadaniem jest uporządkować ją i nawarzyć 💥

1. Stwórz listę `eliksiry` zawierającą tę listę (dodana ponizej)
2. Dodaj nowy eliksir `"Eliksir Księżycowego Blasku"` na koniec listy
3. Wstaw `"Eliksir Jedwabistego Snu"` na początek listy – to klasyk, który powinien być zawsze pierwszy!
4. Usuń `"Mugolskie Krople"` – Profesor uznała, że to profanacja sztuki warzenia
5. Wypisz w pętli wszystkie eliksiry z komentarzem `"✅ Gotowy"` przy każdym
6. Posortuj listę alfabetycznie i wypisz jeszcze raz – teraz wszystko wygląda jak gotowe do prezentacji!

``` 
Lista eliksirów:

"Eliksir Miłości",
"Wywar Stokrotkowy",
"Fortuna Potio",
"Napar Prawdy",
"Eliksir Niewidzialności",
"Super Mocny na Skupienie",
"Zapominalstwo wBbutelce",
"Mugolskie Krople",
"Anty-Sen o Smaku Kawy",
"Eliksir Sportowy"
```

🔮 Bonus: Dodaj f-string, np. `print(f"{eliksir} ✅ Gotowy")` aby wyglądało ładniej

