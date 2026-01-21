# 20 HTTP we wzorcu architektonicznym REST

## REST

**REST (Representational State Transfer)** stanowi dominujący wzorzec architektoniczny dla projektowania nowoczesnych interfejsów API. Jego integralnym elementem jest protokół HTTP, który nie jest jedynie mechanizmem transportu, lecz kluczową częścią struktury architektonicznej.

## API - Interfejs programistyczny aplikacji

**API (ang. Application Programming Interface)** to zestaw reguł i protokołów, który definiuje, w jaki sposób dwa programy lub systemy mogą komunikować się ze sobą. API stanowi kontrakt między dostawcą usługi (serwerem) a konsumentem usługi (klientem), określając, jakie żądania są dostępne, jak je formatować i jakie odpowiedzi można spodziewać się otrzymać.

Kluczowe elementy API:

- Endpointy (punkty dostępu) – adresy URL, pod którymi dostępne są zasoby lub funkcjonalności
- Metody/operacje – czynności, które można wykonać na zasobach (pobieranie, tworzenie, aktualizacja, usuwanie)
- Parametry – dane wejściowe niezbędne do wykonania operacji
- Formaty danych – sposób, w jaki dane są reprezentowane i przesyłane (JSON, XML)
- Kody odpowiedzi – informacja zwrotna o wyniku operacji
- Dokumentacja – szczegółowy opis sposobu użycia API

## URI - Ujednolicony identyfikator zasobów

**URI Uniform Resource Identifier)** to ujednolicony identyfikator zasobów, czyli ciąg znaków służący do jednoznacznego identyfikowania zasobów w sieci, takich jak strony WWW, pliki, usługi, czy dane, działający jako nazwa **(URN)** lub adres **(URL)**, przy czym każdy URL jest URI, ale nie każdy URI jest URL, a w praktyce często oba pojęcia (URI i URL) są używane zamiennie dla adresów internetowych

Konwencje projektowania URI:

- Zasoby powinny być reprezentowane jako rzeczowniki w liczbie mnogiej: ```/users, /products, /orders```
- Hierarchia zasobów powinna odzwierciedlać relacje: ```/users/123/orders``` (zamówienia użytkownika 123)
- Unikać czasowników w URI: zamiast ```/getUser/123``` użyć ```GET /users/123```
- Identyfikatory zasobów powinny być jednoznaczne i trwałe

## Metody GET, POST, PUT, DELETE

REST API operuje na czterech podstawowych metodach HTTP, które mapują się na operacje CRUD (Create, Read, Update, Delete):

- **Metoda GET** służy do pobrania reprezentacji zasobu bez modyfikacji. Jest metodą bezpieczną (safe) i idempotentną, co oznacza, że wielokrotne wykonanie tego samego żądania GET nie zmienia stanu serwera.

- **Metoda POST** służy do tworzenia nowych zasobów lub przesyłania danych do serwera. POST nie jest idempotentny, czyli wielokrotne wysłanie tego samego żądania POST tworzy wiele zasobów.

- **Metoda PUT** służy do zaktualizowania istniejącego zasobu lub zastąpienia go całkowicie. PUT jest idempotentny, czyli wielokrotne wysłanie tego samego żądania PUT ma taki sam efekt co jednokrotne wykonanie.

- **Metoda DELETE** służy do usunięcia zasobu. DELETE jest idempotentny, czyli wielokrotne wysłanie żądania DELETE do nieistniejącego zasobu zwróci ten sam kod statusu.

## Kody statusu HTTP

https://pl.wikipedia.org/wiki/Kod_odpowiedzi_HTTP

## Bezstanowość

**Bezstanowość** jest jedną z fundamentalnych zasad architektury REST. Oznacza ona, że każde żądanie od klienta do serwera musi zawierać wszystkie informacje niezbędne do jego przetworzenia, a serwer nie przechowuje żadnych informacji o stanie klienta pomiędzy żądaniami.

### Implikacje bezstanowości

**Dla serwera:**

- Brak sesji per client – serwer nie utrzymuje żadnych danych o sesji dla poszczególnych klientów
- Każde żądanie jest traktowane niezależnie i w pełni
- Brak konieczności synchronizacji stanu pomiędzy serwerami w klastrach

**Dla klienta:** implikuje to, że każde żądanie musi zawierać wszystkie niezbędne dane:

- Identyfikator zasobu (w URI)
- Dane uwierzytelniające (tokeny, klucze API)
- Dane wejściowe (w ciele żądania lub parametrach)
- Dodatkowe metadane (nagłówki)

### Korzyści bezstanowości

1. **Skalowalność** – dowolny serwer może obsłużyć dowolne żądanie w dowolnym momencie, bez potrzeby dostępu do lokalnego stanu sesji

2. **Niezawodność** – brak zależności od poprzednich żądań zmniejsza złożoność obsługi błędów

3. **Wydajność** – serwery mogą działać jako bezstanowe jednostki, ułatwiając balansowanie obciążenia

4. **Prostota** – każde żądanie jest samostanowiące, co upraszcza architekturę

## Formaty JSON - JavaScript object notation i XML

**JSON** to lekki, czytelny dla człowieka format wymiany danych, który stał się de facto standardem dla nowoczesnych REST API. JSON jest oparty na strukturach danych wspólnych dla większości języków programowania. Charakterystyka JSON:

- **Format:** pary klucz-wartość
- **Zwięzłość:** minimalne znaczniki, kompaktowe reprezentacje
- **Parsowanie:** szybkie i proste
- **Czytelność:** wysoka, intuicyjna struktura
- **Typy danych:** string, number, boolean, null, object, array
- **Wydajność:** mniejszy rozmiar pliku, szybsza transmisja

```
{
  "users": [
    {
      "id": 1,
      "name": "Jan Kowalski",
      "email": "jan@example.com",
      "active": true
    },
    {
      "id": 2,
      "name": "Maria Nowak",
      "email": "maria@example.com",
      "active": false
    }
  ]
}
```

**XML** to starszy, bardziej złożony format opisu danych, który znajduje zastosowanie w systemach legacy i sytuacjach wymagających zaawansowanej strukturalizacji danych. Charakterystyka XML:

- **Format:** znaczniki opisowe (tags)
- **Zwięzłość:** więcej znaczników, bardziej rozbudowana reprezentacja
- **Parsowanie:** wolniejsze, wymaga specjalistycznych parserów
- **Czytelność:** średnia, bardziej złożona struktura
- **Typy danych:** bogatsze wsparcie dla typów, możliwość atrybutów
- **Wydajność:** większy rozmiar pliku, wolniejsza transmisja

```
<?xml version="1.0" encoding="UTF-8"?>
<users>
  <user>
    <id>1</id>
    <name>Jan Kowalski</name>
    <email>jan@example.com</email>
    <active>true</active>
  </user>
  <user>
    <id>2</id>
    <name>Maria Nowak</name>
    <email>maria@example.com</email>
    <active>false</active>
  </user>
</users>
```
