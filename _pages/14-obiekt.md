---
title: 14. Wszędzie są obiekty!
layout: post
---

... bo wszystko w Pythonie jest obiektem! To kolejny sposób organizowania danych. W Pythonie mamy coś podobnego do obiektów JavaScript - **słowniki** (które już znasz!) oraz prawdziwe **obiekty** (klasy).

**Uwaga:** To jest rozszerzenie kursu - obiekty nie są nam niezbędne do tworzenia kolejnych elementów kursu, ale warto wiedzieć, że istnieją! 😊


## Słowniki jako "obiekty" - już to znasz!

```python
person = {
    'name': 'Natalia',
    'age': 27,
    'hobby': ['swimming', 'cycling', 'fantasy books']
}
```

Jak widzisz, słownik przypomina listę, ale zamiast indeksów liczbowych mamy **klucze**. Klucze to nazwy, które pomagają nam zrozumieć, co przechowujemy.

By odwołać się do jakiegoś elementu słownika, używamy klucza:

```python
print(person['hobby'])
# lub
print(person.get('hobby'))
```

Do istniejącego słownika możemy dodawać nowe elementy:

```python
person['city'] = 'Poznań'
print(person)
```

Możemy je także usuwać:

```python
del person['hobby']
# lub
person.pop('hobby')
```

## Zagnieżdżone słowniki

Czasami w słowniku może być inny słownik:

```python
person = {   
    'name': 'Natalia',
    'age': 27,
    'hobby': ['swimming', 'cycling', 'fantasy books'],
    'city': 'Poznań',
    'family': {
        'mom': 'Anna',
        'dad': 'Paweł',
        'sister': 'Karolina'
    }
}
```

Jak wyświetlić imię siostry?

```python
print(person['family']['sister'])
```

## Prawdziwe obiekty - klasy

W Pythonie możemy tworzyć prawdziwe obiekty używając **klas**. To jak szablon do tworzenia obiektów:

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        self.hobbies = []
    
    def add_hobby(self, hobby):
        self.hobbies.append(hobby)
    
    def introduce(self):
        return f"Cześć! Jestem {self.name} i mam {self.age} lat."

# Tworzenie obiektu
natalia = Person('Natalia', 27)
natalia.add_hobby('swimming')
natalia.add_hobby('cycling')

print(natalia.introduce())
print(f"Hobby: {natalia.hobbies}")
```

## Dlaczego obiekty są takie fajne?

1. **Organizacja** - grupują powiązane dane
2. **Czytelność** - `person['name']` mówi więcej niż `data[0]`
3. **Elastyczność** - można łatwo dodawać/usuwać właściwości

## Przykład: System książek

```python
library = {
    'books': [
        {
            'title': 'Hobbit',
            'author': 'J.R.R. Tolkien',
            'year': 1937,
            'available': True
        },
        {
            'title': 'Dune',
            'author': 'Frank Herbert', 
            'year': 1965,
            'available': False
        }
    ]
}

def find_available_books(library):
    available = []
    for book in library['books']:
        if book['available']:
            available.append(book['title'])
    return available

print("Dostępne książki:")
for title in find_available_books(library):
    print(f"- {title}")
```

## 🧪  Zadanie

Stwórz słownik reprezentujący Twoją ulubioną grę:

```python
game = {
    'title': 'Nazwa gry',
    'genre': 'Gatunek',
    'rating': 8.5,
    'platforms': ['PC', 'PlayStation', 'Xbox'],
    'details': {
        'developer': 'Studio deweloperskie',
        'release_year': 2023,
        'multiplayer': True
    }
}

# Wyświetl informacje o grze
def display_game_info(game):
    # Twoja implementacja tutaj!
    pass
```


Obiekty (słowniki) to świetny sposób na organizację danych, ale nie są niezbędne! Wszystko, co możesz zrobić z obiektami, możesz też zrobić ze zwykłymi zmiennymi, listami i funkcjami. 

Obiekty po prostu sprawiają, że kod jest bardziej czytelny i łatwiejszy do utrzymania w większych projektach! 🚀


### 🧪 Zadanie

W tym zadaniu pocwiczymy korzystanie z obiektów stworzymy prostą logikę do **zarządzania swoją szafą**.  
Każdy element garderoby będzie prawdziwym obiektem – z własnymi właściwościami i metodami.

![]({{ site.baseurl }}/assets/sabrina.gif)

#### 👗 Krok 1: Zdefiniuj klasę `ClothingItem`

Stwórz klasę `ClothingItem`, która będzie reprezentować jedno ubranie.  
Każdy element powinien mieć:

- `type` – typ ubrania (np. `"T-shirt"`, `"Jeans"`)
- `color` – kolor (np. `"czarny"`)
- `size` – rozmiar (np. `"M"`)
- `season` – sezon, na który się nadaje (np. `"summer"`, `"winter"`, `"all"`)
- `washed` – czy ubranie jest czyste (`True` lub `False`)

Dodaj do klasy metody:

- `describe()` – zwraca opis ubrania, np.:  
  `"Czarny T-shirt w rozmiarze M na lato. Czysty."`
- `wash()` – ustawia `washed` na `True`
- `wear()` – ustawia `washed` na `False`



#### 🧤 Krok 2: Wypełnij swoją szafę

Stwórz kilka obiektów i dodaj je do listy `wardrobe`, np.:

```python
shirt = ClothingItem("T-shirt", "black", "M", "summer", True)
jeans = ClothingItem("Jeans", "blue", "L", "all", False)
wardrobe = [shirt, jeans]
```

Wyświetl opisy ubrań i „ubierz” niektóre z nich (czyli użyj wear()),
a następnie sprawdź, które ubrania trzeba wyprać.

#### 🧼 Krok 3: Dodatkowe funkcje
Dodaj jedną lub więcej funkcji, które pomogą zarządzać szafą:

```python
def show_clean_clothes(wardrobe):
    # wypisz tylko czyste ubrania
    pass

def show_season_clothes(wardrobe, season):
    # wypisz ubrania odpowiednie na dany sezon
    pass
```
