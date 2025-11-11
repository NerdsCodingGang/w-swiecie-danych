---
title: 11. Słowniki
layout: post
---

Słowniki to kolejny typ danych w Pythonie. Słownik pozwala przechowywać informacje w parach **klucz-wartość**. W przeciwieństwie do list, które używają numerycznych indeksów, słowniki używają kluczy do identyfikacji wartości.

Wyobraź sobie prawdziwy słownik - szukasz słowa (klucza) i znajdujesz jego definicję (wartość). Podobnie działają słowniki w Pythonie!

```python
slownik = {"klucz1": "wartość1", "klucz2": "wartość2", "klucz3": "wartość3"}
```


Słownik tworzymy używając nawiasów klamrowych `{}`, a pary klucz-wartość oddzielamy przecinkami. Klucz i wartość łączymy dwukropkiem `:`.

np.

```python
slownik_czarodziejow = {
    "rośliny": "herbae",
    "kapelusz": "galerus",
    "jagody": "baccae",
    "napar": "potio",
    "kociołek": "cacabus"
}

print(slownik_czarodziejow["jagody"])  
# >>> baccae
```

Stwórzmy np. słownik z informacjami o osobie:

```python

profesor = {
    "imię": "Jaromira",
    "nazwisko": "Infusora",
    "zawód": "Mistrzyni Eliksirów",
    "ulubiony_napar": "herbata z liści werbeny",
    "specjalizacja": "transmutacja smaków i zapachów",
    "zawołanie": "Potio et Lux!"
}
```

Aby wyświetlić wartość ze słownika, odwołujemy się do słownika i podajemy klucz:

```python
print(profesor["ulubiony_napar"])  
# >>> herbata z liści werbeny
```

W swoim pliku Python stwórz teraz słownik o nazwie `moje_magiczne_ja`, który zawiera informacje o Tobie: jak np. imię, wiek, ulubiony kolor i hobby. Następnie wypisz w konsoli swoje imię używając słownika.

### Właściwości słowników

Podobnie jak listy, słowniki mają swoją długość, którą możemy sprawdzić funkcją `len()`:

```python
print(len(profesor))
# >>> 6
```

Teraz wypisz w konsoli liczbę elementów w swoim słowniku "moje_magiczne_ja".

### Dodawanie i modyfikowanie elementów

Do dodawania nowej pary klucz-wartość wystarczy przypisać wartość do nowego klucza:

```python
profesor = {
    "imię": "Jaromira",
    "nazwisko": "Infusora",
    "zawód": "Mistrzyni Eliksirów",
    "ulubiony_napar": "herbata z liści werbeny",
    "specjalizacja": "transmutacja smaków i zapachów",
    "zawołanie": "Potio et Lux!"
}

# dodajemy nowy klucz
profesor["letni_eliksir"] = "koktajl z nutą różanej mgły"

print(profesor)
```

Dodaj do swojego słownika "moje_magiczne_ja" nowy klucz "ulubiona_ksiazka" z nazwą książki, którą lubisz.

Możemy również modyfikować istniejące wartości:

```python
profesor["letni_eliksir"] = "mrozone smoothie z mięty"
print(profesor["letni_eliksir"])
# >>> mrozone smoothie z mięty
```

Zmień wartość jednego z kluczy w swoim słowniku "moje_magiczne_ja" i wypisz go w konsoli.

### Różne typy danych w słowniku

W słowniku możemy przechowywać różne typy danych - stringi, liczby, listy, a nawet inne słowniki:

```python
student = {
    "imię": "Witomir",
    "wiek": 23,
    "oceny": [5, 3, 4, 6, 5],
    "adres": {
        "ulica": "Aleja Feniksa 7",
        "miasto": "Czarogród"
    },
    "aktywny": True
}
```

Aby dostać się do wartości w zagnieżdżonym słowniku:

```python
print(student["adres"]["miasto"])
# >>> Czarogród

print(student["oceny"][0])
# >>> 5
```

### Sprawdzanie czy klucz istnieje

Zanim spróbujemy odwołać się do klucza, warto sprawdzić, czy istnieje. Używamy do tego słowa kluczowego `in`:

```python
if "sowa" in student:
    print(f"Poczta: {student['sowa']}")
else:
    print("Brak adresu sowy")
```

Sprawdź w swoim słowniku `moje_magiczne_ja`, czy istnieje klucz `miasto`. Jeśli nie, dodaj go!

### Usuwanie elementów ze słownika

Do usuwania elementów ze słownika możemy użyć kilku metod:

**Słowo kluczowe `del`**:
```python
del student["wiek"]
print(student)
```

**Metoda `pop()`** - usuwa element i zwraca jego wartość:

```python
czarodziejka = {
    "imię": "Mirabel",
    "zawód": "runopisarka",
    "ulubiony_kolor": "szmaragdowy",
    "wiek": 126
}

usuniety_wiek = czarodziejka.pop("wiek")
print(usuniety_wiek)  # >>> 126
print(czarodziejka)
# >>> {'imię': 'Mirabel', 'zawód': 'runopisarka', 'ulubiony_kolor': 'szmaragdowy'}
```

**Metoda `popitem()`** - usuwa ostatnio dodaną parę klucz-wartość:
```python
czarodziejka = {
    "imię": "Wencla",
    "zawód": "zielarka",
    "ulubiona_roślina": "krwawnik"
}

usunieta_para = czarodziejka.popitem()
print(usunieta_para)
# >>> ('ulubiona_roślina', 'krwawnik')
print(czarodziejka)
# >>> {'imię': 'Wencla', 'zawód': 'zielarka'}

```

### Przydatne metody słowników

**Metoda `keys()`** - zwraca wszystkie klucze:
```python
czarodziejka = {
    "imię": "Dobromira",
    "zawód": "twórczyni magicznych map",
    "wiek": 87
}

print(czarodziejka.keys())
# >>> dict_keys(['imię', 'zawód', 'wiek'])
```

**Metoda `values()`** - zwraca wszystkie wartości:
```python
print(czarodziejka.values())
# >>> dict_values(['Dobromira', 'twórczyni magicznych map', 87])
```

**Metoda `items()`** - zwraca pary klucz-wartość:
```python
print(czarodziejka.items())
# >>> dict_items([('imię', 'Dobromira'), ('zawód', 'twórczyni magicznych map'), ('wiek', 87)])
```

**Metoda `get()`** - bezpieczny sposób pobierania wartości:
```python
# Jeśli klucz nie istnieje, zwróci None lub wartość domyślną
print(czarodziejka.get("różdżka"))            # >>> None
print(czarodziejka.get("różdżka", "cisowa"))  # >>> cisowa - wartość domyślna jeśli nie znajdzie
print(czarodziejka.get("imię", "Nieznana"))   # >>> Dobromira - tu znalazło więc pomija wartość domyślną
```

### Pętla po słowniku

🔮 Możemy iterować po słowniku na kilka sposobów:

**Iterowanie po kluczach** (domyślne):
```python
ksiega = {
    "tytuł": "Starożytne Zaklęcia i Rytuały",
    "autor": "Arkadios z Doliny Run",
    "wiek": 342
}

for klucz in ksiega:
    print(klucz)
# >>> tytuł
# >>> autor
# >>> wiek
```

**Iterowanie po wartościach**:
```python
for wartosc in ksiega.values():
    print(wartosc)
# >>> Starożytne Zaklęcia i Rytuały
# >>> Arkadios z Doliny Run
# >>> 342
```

**Iterowanie po parach klucz-wartość**:
```python
for klucz, wartosc in ksiega.items():
    print(f"{klucz}: {wartosc}")
# >>> tytuł: Starożytne Zaklęcia i Rytuały
# >>> autor: Arkadios z Doliny Run
# >>> wiek: 342
```

### 🧪 Zadanie

Stwórz słownik o nazwie ksiega zawierający informacje o Twojej ulubionej księdze magicznej: tytuł, autor, rok_wydania, liczba_stron, dziedzina (np. eliksiry, klątwy, transmutacja) Następnie:

1. Wypisz wszystkie informacje używając pętli
2. Dodaj klucz "przeczytana" z wartością `True` lub `False`
3. Usuń klucz `liczba_stron`
4. Wypisz tylko klucze słownika

### Łączenie słowników

Możemy połączyć dwa słowniki na kilka sposobów:

**Metoda `update()`**:
```python
czarodziej_info1 = {"imię": "Jaromir", "wiek": 137}
czarodziej_info2 = {"specjalizacja": "eliksiry", "dom": "Mirabilis"}

czarodziej_info1.update(czarodziej_info2)
print(czarodziej_info1)
# >>> {"imię": "Jaromir", "wiek": 137, "specjalizacja": "eliksiry", "dom": "Mirabilis"}
```

**Operator `|` (Python 3.9+)**:
```python
czarodziej1 = {"imię": "Jaromir", "wiek": 137}
czarodziej2 = {"specjalizacja": "eliksiry", "dom": "Mirabilis"}

nowy = czarodziej1 | czarodziej2
print(nowy)
# >>> {"imię": "Jaromir", "wiek": 137, "specjalizacja": "eliksiry", "dom": "Mirabilis"}
```

### Słownik z listą

Często używamy słowników do grupowania danych. Na przykład, każda komnata uczniowska ma przypisanych mieszkańców:

```python
komnaty = {
    "komnata_runiczna": ["Dobiesława", "Boguchwał", "Świętopełk"],
    "komnata_ziół": ["Jaromira", "Mieczysław", "Dobrochna"],
    "komnata_mgieł": ["Wielimir", "Radomiła", "Gniewosz"]
}

print(komnaty["komnata_runiczna"])
# >>> ["Dobiesława", "Boguchwał", "Świętopełk"]

# Dołączenie nowej adeptki do komnaty runicznej
komnaty["komnata_runiczna"].append("Lutomira")
print(komnaty["komnata_runiczna"])
# >>> ["Dobiesława", "Boguchwał", "Świętopełk", "Lutomira"]
```

### 🧪 Zadanie

Stwórz słownik `oceny_magii`, gdzie kluczami będą przedmioty: "alchemia", "programowanie", "zaklęcia ochronne", a wartościami listy ocen w skali 1 do 6.

1. Dodaj nową ocenę do alchemii
2. Oblicz średnią ocen z każdego przedmiotu
3. Wypisz przedmiot z najwyższą średnią jako twój magiczny talent ✨

### Lista słowników

Możemy też tworzyć listy zawierające słowniki:

```python
uuczniowie = [
    {"imie": "Dobiesława", "wiek": 16, "komnata": "komnata runiczna"},
    {"imie": "Jaromira", "wiek": 17, "komnata": "komnata ziół"},
    {"imie": "Wielimir", "wiek": 15, "komnata": "komnata mgieł"}
]

# Wypisanie wszystkich uczniów
for uczen in uczniowie:
    print(f"{uczen['imie']} ma {uczen['wiek']} lat ~ nalezy do {uczen['komnata']}.")
```

### 🧪 Zadanie

Stwórz listę `przedmioty` zawierającą słowniki z informacjami o przedmiotach magicznych (nazwa, moc, kategoria, aktywność). 

```python
przedmioty = [
    {"nazwa": "Eliksir Snu", "moc": 7, "kategoria": "alchemia", "aktywność": True},
    {"nazwa": "Lustro Prawdziwe Ja", "moc": 9, "kategoria": "artefakt", "aktywność": False},
    {"nazwa": "Kamień Filozofów", "moc": 5, "kategoria": "rytuał", "aktywność": True},
    {"nazwa": "Napój Mocy", "moc": 8, "kategoria": "alchemia", "aktywność": True},
    {"nazwa": "Flet Oczyszczenia", "moc": 4, "kategoria": "dźwięk", "aktywność": False}
]
```

Następnie:
1. Wypisz wszystkie przedmioty z kategorii **"alchemia"**
2. Znajdź przedmioty o **największej mocy** (przypomnij sobie zadanie z iskrami z tematu o tablicach)
3. Policz ile jest **aktywnych** przedmioty (`aktywność = True`)

### Zagnieżdżone słowniki

Słowniki mogą zawierać inne słowniki, co pozwala na tworzenie złożonych struktur danych:

```python
instytut = {
    "nazwa": "Akademia Magii i Eliksirów",
    "lokalizacja": {
        "ulica": "Zaułek Feniksa 7¾",
        "miasto": "Czarogród",
        "kod": "77-777"
    },
    "kadra": {
        "ignacy_kociołek": {
            "funkcja": "mistrz kodzenia",
            "pensja": 15000,
            "lata_praktyki": 120
        },
        "celestyna_aurora": {
            "funkcja": "zaklinaczka światła",
            "pensja": 13200,
            "lata_praktyki": 97
        }
    }
}

print(instytut["kadra"]["ignacy_kociołek"]["funkcja"])
# >>> mistrz kodzenia
```

### 🧪 Zadanie 

Stwórz słownik "biblioteka" reprezentujący system biblioteczny:
- Klucze to tytuły książek
- Wartości to słowniki z informacjami: autor, rok, dostępna (True/False), wypożyczający (imię osoby lub None)

Następnie napisz kod, który:
1. Wyświetla wszystkie dostępne książki
2. "Wypożycza" książkę (zmienia dostępna na False i dodaje imię wypożyczającego)
3. "Zwraca" książkę (zmienia dostępna na True i usuwa imię wypożyczającego)
4. Wyświetla statystyki: ile książek jest dostępnych, ile wypożyczonych