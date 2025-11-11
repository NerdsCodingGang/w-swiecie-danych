---
title: 13. Let's make some magic! 🌈 ✨ 
layout: post
---

**Uwaga:** Pamiętaj, że dobrą praktyką jest pisanie kodu w języku angielskim!

Spróbujmy nieco ożywić naszą konsolę i dodać jej trochę koloru! Stworzymy magiczny generator kolorów, który będzie wyświetlał kolorowy tekst bezpośrednio w terminalu.

Stwórzmy naszą pierwszą funkcję w projekcie!

W Twoim pliku Python zdefiniujemy następującą funkcję:

```python
def get_random_color():
    print('Wylosujmy kolor!')

get_random_color()
```

Uruchommy nasz program i zobaczmy co się wydarzyło. Pojawił się wpisany przez nas napis. 

### Zadanie
Spróbuj uzyć modułu random `import random` i wylosować liczbę od 0 do 255.

```python
import random

# tutaj dodaj swój kod
my_number = ...

print(f"moja liczba to ... {my_number}")
```
Udało się? 

Czas poszukać kolorów!

## Kolory w terminalu
W terminalu możemy wyświetlać kolorowy tekst, używając specjalnych kodów zwanych kodami ANSI. Są to ciągi znaków, które zaczynają się od `\033[` i informują terminal, jak ma wyświetlić tekst – np. na czerwono, zielono albo niebiesko.

Spróbuj wpisać w swoim pliku Pythona:

```python
print("\033[31mTo jest czerwony tekst!\033[0m")
print("\033[32mA to zielony!\033[0m")
print("\033[34mA ten niebieski!\033[0m")

```

Dobra... wygląda to trochę dziwnie, ale jest prostrze niz myślisz 

Zauważ:
- 🔴 `\033[31m` = czerwony  
- 🟢 `\033[32m` = zielony  
- 🔵 `\033[34m` = niebieski  
- ⬜ `\033[0m` = reset (czyli powrót do domyślnego koloru)



*Zadziała w większości nowoczesnych terminali*
Jeśli nie widzisz kolorów – spróbuj uruchomić plik przez VSC terminal albo ręcznie (np. `python magic.py`) zamiast wbudowanego edytora.

### Co to jest RGB?
RGB to skrót od Red, Green, Blue – czyli czerwony, zielony i niebieski. Skrót znany kazdemu, kto spróbował trochę zabawy z grafiką komputerową. Każdy kolor na ekranie komputera (i terminalu!) można stworzyć, mieszając te trzy kolory w różnych proporcjach. Na przykład:

- RGB(255, 0, 0) = czysta czerwień 🔴
- RGB(0, 255, 0) = czysta zieleń 🟢
- RGB(0, 0, 255) = czysty niebieski 🔵

- RGB(255, 255, 0) = żółty (czerwony + zielony) 🟡
- RGB(255, 165, 0) = pomarańczowy 🟠
- RGB(128, 0, 128) = fioletowy 🟣
- RGB(139, 69, 19) = brązowy 🟤
- RGB(0, 0, 0) = czarny ⚫ (czarny to "brak koloru")
- RGB(255, 255, 255) = biały ⚪

![]({{ site.baseurl }}/assets/RGB-model.png)


W terminalu możemy korzystać z pełnych kolorów RGB, jeśli użyjemy tzw. true color ANSI kodu, który wygląda tak:

```
\033[38;2;R;G;Bm
```

gdzie `R`, `G`, `B` to znane nam wartości w palecie kolorów! 

Przykład:

```python
print("\033[38;2;255;0;0mTo jest RGB czerwony!\033[0m")
print("\033[38;2;100;200;255mTo jest kolor nie z tej ziemi!\033[0m")
```

✨ **A teraz… magia!** ✨ 

Stworzymy prawdziwą magię! 

Zamiast wybierać kolory ręcznie, stworzymy funkcję, która losuje kolor RGB i konwertuje go na kod ANSI.
Będziemy generować losowe kolory RGB i przekształcać je na kody kolorów terminalowych.

Zacznijmy od tego, by stworzyć funkcję generującą losowe wartości RGB:

```python
import random

def get_random_rgb():
    red = random.randint(0, 255)
    green = random.randint(0, 255)
    blue = random.randint(0, 255)
    return red, green, blue
```

Przetestujmy naszą funkcję:

```python
print(get_random_rgb())
```

Świetnie! Teraz dodaj funkcję, która przekształci nasze wartości RGB na kolor terminalowy:

```python
def rgb_to_terminal_color(red, green, blue):
    # Kod ANSI dla kolorów RGB w terminalu
    return f"\033[38;2;{red};{green};{blue}m"

def reset_color():
    return "\033[0m"
```

Teraz połączmy wszystko razem w naszej głównej funkcji:

```python
import random

def get_random_rgb():
    red = random.randint(0, 255)
    green = random.randint(0, 255)
    blue = random.randint(0, 255)
    return red, green, blue

def rgb_to_terminal_color(red, green, blue):
    return f"\033[38;2;{red};{green};{blue}m"

def reset_color():
    return "\033[0m"

def get_random_color():
    red, green, blue = get_random_rgb()
    color_code = rgb_to_terminal_color(red, green, blue)
    return color_code, (red, green, blue)

# Testujmy!
color_code, rgb_values = get_random_color()
print(f"{color_code}To jest kolorowy tekst! RGB: {rgb_values}{reset_color()}")
```

## Dodajmy więcej magii!

Stwórzmy funkcję, która wyświetli kolorowy tekst:

```python
def display_colored_text(text, color_info=None):
    if color_info is None:
        color_code, rgb_values = get_random_color()
    else:
        color_code, rgb_values = color_info
    
    colored_text = f"{color_code}{text}{reset_color()}"
    print(colored_text)
    print(f"Kolor RGB: {rgb_values}")
    return color_code, rgb_values

# Testujemy
display_colored_text("✨ Magiczny tekst! ✨")
```

## Stworzymy kolekcję kolorów!

Teraz użyjemy słowników i list, żeby stworzyć kolekcję naszych ulubionych kolorów:

```python
def create_color_palette(size=5):
    palette = {}
    colors_list = []
    
    for i in range(size):
        color_name = f"magic_color_{i+1}"
        color_code, rgb_values = get_random_color()
        
        palette[color_name] = {
            'rgb': rgb_values,
            'code': color_code
        }
        colors_list.append(rgb_values)
    
    return palette, colors_list

# Stwórzmy naszą paletę
my_palette, colors_list = create_color_palette(7)

print("🎨 Moja magiczna paleta kolorów:")
for color_name, color_info in my_palette.items():
    rgb = color_info['rgb']
    code = color_info['code']
    print(f"{code}{color_name}: RGB{rgb}{reset_color()}")
```

## Interaktywna magia!

Stwórzmy interaktywną funkcję, która pozwoli użytkownikowi wybierać kolory:

```python
def interactive_color_magic():
    print("✨ Witaj w magicznym świecie kolorów! ✨")
    
    while True:
        print("\nCo chcesz zrobić?")
        print("1. Wylosuj losowy kolor")
        print("2. Stwórz paletę kolorów")
        print("3. Pokoloruj swój tekst")
        print("4. Wyjdź")
        
        choice = input("Wybierz opcję (1-4): ")
        
        if choice == '1':
            color_code, rgb_values = get_random_color()
            print(f"{color_code}🌈 Twój losowy kolor! RGB: {rgb_values}{reset_color()}")
            
        elif choice == '2':
            size = int(input("Ile kolorów ma mieć paleta? "))
            palette, _ = create_color_palette(size)
            print(f"\n🎨 Twoja paleta ma {size} kolorów:")
            for name, info in palette.items():
                code = info['code']
                rgb = info['rgb']
                print(f"{code}● {name}: RGB{rgb}{reset_color()}")
                
        elif choice == '3':
            user_text = input("Wpisz tekst do pokolorowania: ")
            display_colored_text(user_text)
            
        elif choice == '4':
            print("👋 Dzięki za magiczne chwile!")
            break
            
        else:
            print("❌ Nieprawidłowa opcja!")

# Uruchommy magię!
interactive_color_magic()
```

##  🧙‍♀️ Zadanie dla prawdziwych czarodziejów!

Stwórz funkcję `magic_text_animation(text, duration=10)`, która:

1. Przyjmuje tekst jako parametr
2. Wyświetla ten tekst zmieniając jego kolor co 0.5 sekundy
3. Animacja trwa przez `duration` sekund
4. Użyj pętli, `time.sleep()` i wszystkich poznanych elementów!

```python
import time

def magic_text_animation(text, duration=10):
    # Twoja implementacja tutaj!
    pass

# Przykład wywołania:
magic_text_animation("✨ NERDS CODING GANG! ✨", 15)
```

**Wskazówka:** Użyj `time.sleep(0.5)` do zatrzymania programu na pół sekundy i `print("\033[2J\033[H", end="")` do wyczyszczenia ekranu przed każdym nowym kolorem!

## 🌈 Bonus: Gradientowe szaleństwo! 🌈

Dla najodważniejszych: stwórz funkcję `rainbow_text(text)`, która wyświetli każdą literę tekstu w innym kolorze!

```python
def rainbow_text(text):
    # Każda litera w innym kolorze!
    result = ""
    for char in text:
        if char != ' ':  # Nie kolorujemy spacji
            color_code, _ = get_random_color()
            result += f"{color_code}{char}{reset_color()}"
        else:
            result += char
    print(result)

# Testuj:
rainbow_text("PYTHON MAGIC!")
```

---

✨ **Czy to nie jest magiczne?** ✨

Teraz masz pełną kontrolę nad kolorami w terminalu! Możesz tworzyć tęczowe teksty, kolorowe menu, a nawet proste animacje. Pamiętaj - magia tkwi w kodzie, ale prawdziwa moc w kreatywności programisty! Baw się dalej! 