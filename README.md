# Framework_Scraper

|Składowa|Selektor|Nazwa zmiennej|Typ zmiennej|
|--------|--------|--------------|------------|
|opinia|div.js_product-review|opinion|bs4.element.Tag|
|identyfikator opinii|div.js_product-review\["data-entry-id"\]|opinion_id|str|
|autor opinii|span.user-post__author-name|author|str|
|rekomendacja|span.user-post__author-recomendation > em|recommendation||
|liczba gwiazdek|span.user-post__score-count|stars||
|treść opinii|div.user-post__text|content||
|lista zalet|div.review-feature__title--positives ~ div.review-feature__item <br> div\[class$=positives\] ~ div.review-feature__item<br> div.review-feature__col:has(> div\[class$=positives\]) > div.review-feature__item|pros||
|lista wad|div.review-feature__title--negatives ~ div.review-feature__item <br> div\[class$=negatives\] ~ div.review-feature__item<br> div.review-feature__col:has(> div\[class$=negatives\]) > div.review-feature__item|cons||
|dla ilu osób przydatna|span\[id^=votes-yes\]<br>button.vote-yes > span<br>button.vote-yes["data-total-vote"]|useful||
|dla ilu osób nieprzydatna|span\[id^=votes-no\]<br>button.vote-no > span<br>button.vote-no["data-total-vote"]|useless||
|data wystawienia mopinii|span.user-post__published > time:nth-child(1)\["datetime"\]|publish_date||
|data zakupu|span.user-post__published > time:nth-child(2)\["datetime"\]|purchase_date||

## Etapy pracy nad projektem
## Wersja strukturalna
1. Pobranie do pojedynczych zmiennych składowych pojedynczej opinii
2. Zapisanie wszystkich składowych pojedynczej opinii do słownika
3. Pobranie wszystkich opinii z pojedynczej strony do słowników i zapisanie ich na liście
4. Zapisanie wszystkich opinii z listy do pliku .json
5. Pobranie wszystkich opinii o produkcie i zapisanie ich na liście w postaci słowników
6. Dodanie możliwości podania kodu produktu przez użytkownika 
7. Optymalizacja kodu
    a. utworzenie funkcji do ekstrakcji elementów strony
    b. utworzenie słownika selektorów
    c. użycie dictionary comprehension do pobrania składowych pojedynczej opinii na podstawie słownika selektorów
8. Analiza pobranych opinii dla konkretnego produktu
    a. wyliczenie podstawowych statystyk:
        - liczba wszystkich opinii
        - liczba opinii dla których podano zalety
        - liczba opinii dla których podano wady
        - średnia opcena produktu 
    b. przygotowanie wykresów:
        - udział poszczególnych rekomendacji w ogólnej liczbie opinii
        - histogram występowania poszczególnych ocen

## Wersja rozszerzona
1. Utworzenie interfejsu sieciowego
2. Dodanie podstron
3. Załadowanie opinii o wybranym produkcie na stronę 
   1. Odtworzenie struktury opinii ze starej wersji
   2. Reorganizacja w ramach szablonów
4. Delegacja zadań do klas i szablonów
5. Napisanie konstruktorów i funkcji czysto zadaniowych
6. Uzupełnienie metod rzutowania i konstruktorów kopiujących w obiektach
7. Przetwarzanie statystyk
8. Wizualizacja danych
   1. Wyłuskanie informacji
   2. Renderowanie wykresu

## Biblioteki użyte w kodzie źródłowym wersji rozszerzonej
1. Requests: dodaje komunikację ze stronami html i przetwarzanie ich kodu
2. os: zawiera podstawowe interfejsy do komunikacji z systemem operacyjnym
3. Flask: obsługa zadań sieciowych
4. Pandas: analiza danych
5. Beautiful Soup: wyodrębnianie informacji z kodu źródłowego stron internetowych
6. json: praca z plikami w formacie typu json
7. markdown: funkcjonalność konwencji markdown i konwersja zwrotna do html
