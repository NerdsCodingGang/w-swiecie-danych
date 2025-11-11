---
title: 3. Skąd się biorą dane?
layout: post
---

W tym rozdziale:
- poznasz jedno z najpopularniejszych źródeł danych do analiz,
- dowiesz się, czym jest plik CSV,
- po raz pierwszy otworzysz prawdziwe dane w Google Colab.

ale spokojnie, przeprowadzimy Cię przez wszystko krok po kroku.

---

## 📂 Skąd bierzemy dane?

Dane mogą pochodzić z wielu miejsc:
- z plików (na przykład CSV),
- z API serwisów internetowych,
- z otwartych repozytoriów i portali, na przykład Github albo Kaggle,
- z systemów firmowych, aplikacji, ankiet, procesów badawczych jak UX research (*user experience research*).

Na naszych warsztatach zaczniemy od jednego, konkretnego zestawu:
**dane o piosenkach ze Spotify**.

Te dane:
- pochodzą z prawdziwych zestawów typu [Spotify Tracks Dataset Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset?resource=download), 
- są zapisane w pliku `spotify_sample.csv`,
- zawierają między innymi: tempo, energię, taneczność, popularność i długość utworu.

Robi się poważnie, ale spokojnie, za chwilę zobaczysz, że to po prostu tabelka danych 

---

## 📄 Czym jest CSV

Plik CSV (comma-separated values) to bardzo zwykły i popularny format danych:
- wygląda jak plik surowych danych, ale po otwarciu np. w MS Excel to tabela,
- każda linijka to jeden rekord,
- wartości są oddzielone przecinkiem lub średnikiem.

Możesz go otworzyć w:
- Google Sheets,
- Excelu,
- edytorze tekstu,
- albo... w Pythonie

My użyjemy Pythona w Colabie, żeby zrobić pierwszy krok w stronę Data Science.

---

## ☁️ Przygotuj notatnik w Colabie

Upewnij się, że masz już:
- otwarty notatnik w Google Colab,
- nazwany na przykład `DataScience_Workshop` albo inaczej - zmienialiśmy nazwę w poprzedniej lekcji.


Jesteście gotowi?

---

### 🎵 Zbiór danych: spotify_sample.csv

Na warsztatach możesz pobrać plik ze strony [Dataset Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset?resource=download) albo skorzystać z pliku na githubie -> [`spotify_sample.csv`](https://raw.githubusercontent.com/NerdsCodingGang/data/spotify_sample.csv) z przygotowanymi danymi.  


> Zestaw danych zawierający utwory ze Spotify obejmujący 125 różnych gatunków muzycznych. Każdy utwór ma przypisane określone cechy dźwiękowe. Dane są zapisane w formacie CSV, czyli w postaci tabeli, którą można łatwo i szybko wczytać.

![github]({{ site.baseurl }}/assets/dane-github.png){:title="dane spotify" class="img-responsive"}


Pokażemy Ci teraz dwa sposoby pracy z tym plikiem w Google Colab.


Najpierw zrób import biblioteki `pandas`.  
Skopiuj ten kod do pierwszej komórki w Colabie i uruchom go:

```python
import pandas as pd
```

Jeśli nie pojawił się żaden błąd, wszystko działa poprawnie.

### Sposób 1: wgrywanie pliku z komputera

Ten sposób jest dobry, gdy masz plik zapisany na swoim komputerze.

1. Zapisz plik spotify_sample.csv na komputerze.

2. W Colabie dodaj nową komórkę z tym kodem:

    ```python
    from google.colab import files

    uploaded = files.upload()
    ```

3. Uruchom komórkę i wybierz plik spotify_sample.csv z dysku.

4. Po wgraniu pliku dodaj kolejną komórkę i wczytaj dane:
    ```python
    df = pd.read_csv("spotify_sample.csv")
    df.head()
    ```

Powinna pojawić się tabelka z pierwszymi wierszami danych.
Jeśli ją widzisz, to właśnie zrobiłaś/zrobiłeś pierwszy krok w pracy z danymi.