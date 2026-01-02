# 03 Normalizacja schematu bazy danych

## Czym jest baza danych
Baza danych to zbiór danych zapisanych z określonymi regułami. W węższym znaczeniu obejmuje dane cyfrowe gromadzone zgodnie z zasadami przyjętymi dla danego programu komputerowego specjalizowanego w gromadzeniu i przetwarzaniu tych danych. Taki program lub pakiet programów nazywany jest systemem zarządzania bazą danych.

## Czym jest normalizacja bazy danych
Normalizacja bazy danych to proces strukturyzowania relacyjnej bazy danych zgodnie założeniami postaci normalnych w celu zmniejszenia nadmiarowości danych i poprawy ich integralności. 

## Na co wpływa normalizacja

| Aspekt                     | Zmienia się | Przykład                          |
| -------------------------- | ----------- | --------------------------------- |
| Struktura tabel            | ✓           | 1 tabela → 3 tabele               |
| Zawartość danych           | ✗           | "John" to nadal "John"            |
| Semantyka                  | ✗           | Imię to nadal imię                |
| Typy danych                | ✗           | VARCHAR(50) to nadal VARCHAR(50)  |
| NULL wartości              | ✗           | Brakujące dane zostają brakujące  |
| Duplikacja                 | ✓           | Mniej powtórzeń                   |
| JOINy                      | ✓           | Brak JOINów → wiele JOINów        |
| Wydajność SELECT           | ✓           | Wolniej (JOINy)                   |
| Wydajność UPDATE           | ✓           | Szybciej (mniej duplikatów)       |
| Zajęta przestrzeń          | ✓           | Mniej miejsca                     |
| Możliwe zapytania (wyniki) | ✗           | Można uzyskać te same wyniki      |
| Ograniczenia biznesowe     | ✗           | Reguły pozostają do implementacji |

## 1NF Pierwsza postać normalna
Tabela spełnia wymogi pierwszej postaci normalnej, jeżeli na przecięciu wierszy i kolumn znajdują się wartości elementarne (atomowe). Wartości atomowe to pojedyncze wartości określonego typu, a nie zbiory wartości i mają jedną wartość dla każdej instancji encji. 

Przed normalizacją

| Order_ID | Product_ID | Product_Names   | Quantities |
| -------- | ---------- | --------------- | ---------- |
| 101      | P1, P2     | Laptop, Monitor | 2, 1       |
| 102      | P1         | Laptop          | 3          |

Po normalizacji

| Order_ID | Product_ID | Product_Name | Quantity |
| -------- | ---------- | ------------ | -------- |
| 101      | P1         | Laptop       | 2        |
| 101      | P2         | Monitor      | 1        |
| 102      | P1         | Laptop       | 3        |

## 2NF Druga postać normalna
Spełnia warunki pierwszej postaci normalnej i dodatkowo każda kolumna zależy
funkcyjnie od całego klucza głównego

Tabela ZAMÓWIENIE naruszająca 2NF z uwagi na zależność częściową

| Order_ID | Product_ID | Product_Name | Quantity |
|----------|-----------|--------------|----------|
| 101      | P1        | Laptop       | 2        |
| 101      | P2        | Monitor      | 1        |
| 102      | P1        | Laptop       | 3        |

Tabela ZAMÓWIENIE po normalizacji do 2NF

| Order_ID | Product_ID | Quantity |
|----------|-----------|----------|
| 101      | P1        | 2        |
| 101      | P2        | 1        |
| 102      | P1        | 3        |

Tabela PRODUKT po normalizacji do 2NF

| Product_ID | Product_Name |
|-----------|--------------|
| P1        | Laptop       |
| P2        | Monitor      |


Teraz Product_Name zależy tylko od Product_ID, dlatego umieszczono go w osobnej tabeli PRODUKT. Tabela ZAMÓWIENIE zawiera tylko atrybuty, które są w pełni zależne od całego klucza złożonego.


## 3NF Trzecia postać normalna
Spełnia warunki drugiej postaci normalnej i dodatkowo każdy atrybut jest funkcjonalnie zależny jedynie od klucza głównego. Nie mogą więc istnieć jakiekolwiek zależności przechodnie

Tabela STUDENT naruszająca 3NF z uwagi na zależność przechodnią

| Student_ID | Imię   | Department_ID | Department_Name |
|-----------|--------|---------------|-----------------|
| 1         | Jan    | D1            | Informatyka     |
| 2         | Maria  | D2            | Elektronika     |
| 3         | Piotr  | D1            | Informatyka     |

**Problem:** Zależność przechodnia – Department_Name zależy od Department_ID, a Department_ID zależy od Student_ID. Zatem Department_Name zależy przechodnie od Student_ID (klucza głównego) poprzez Department_ID. Department_Name nie powinno być w tabeli studenta, bo nazwa wydziału zawsze będzie taka sama dla danego ID wydziału.

Tabela STUDENT po normalizacji do 3NF

| Student_ID | Imię   | Department_ID |
|-----------|--------|---------------|
| 1         | Jan    | D1            |
| 2         | Maria  | D2            |
| 3         | Piotr  | D1            |

Tabela DEPARTMENT po normalizacji do 3NF

| Department_ID | Department_Name |
|--------------|-----------------|
| D1           | Informatyka     |
| D2           | Elektronika     |


## Podsumowanie porównawcze

| Postać Normalna | Co się usuwa                                 | Główne Wymogi                                    | Praktyczne Znaczenie                                       |
| --------------- | -------------------------------------------- | ------------------------------------------------ | ---------------------------------------------------------- |
| 1NF             | Powtarzające się grupy, wartości nie-atomowe | Wszystkie wartości są atomowe                    | Zapobiega przechowywaniu zbiorów wartości w jednej komórce |
| 2NF             | Zależności częściowe                         | Brak zależności od części klucza złożonego       | Eliminuje anomalie w tabelach z kluczami złożonymi         |
| 3NF             | Zależności przechodnie                       | Brak zależności między atrybutami nie-kluczowymi | Zapobiega anomaliom aktualizacji i redundancji danych      |

## Anomalie usuwane przez normalizację bazy danych

Anomalie w bazach danych to niespójności, powtórzenia i błędy wynikające z nieodpowiedniego, zwykle nieznormalizowanego projektu bazy. Prowadzą one do problemów takich jak utrata danych, niespójność informacji czy utrudnione dodawanie, aktualizowanie lub usuwanie rekordów (anomalie wstawiania, aktualizacji i usuwania); głównym rozwiązaniem jest normalizacja bazy danych, która strukturyzuje dane w logiczne tabele, eliminując te problemy. 

Wyróżnamy następujące rodzaje anomalii:

- Anomalia wstawiania: Nie można dodać jednej informacji bez dodania innej (np. nie można dodać nowego nauczyciela bez przypisania go do sali). 

- Anomalia aktualizacji: Zmiana danych w jednym miejscu wymaga zmiany w wielu (np. zmiana adresu pracownika w wielu rekordach), co prowadzi do niespójności, jeśli pominiemy któryś rekord. 

- Anomalia usuwania: Usunięcie jednego rekordu powoduje utratę innych, powiązanych danych, które powinny pozostać (np. usunięcie studenta powoduje utratę informacji o przedmiocie, który tylko on studiował).

## Wady i zalety procesu normalizacji bazy danych

| Wymiar             | Wpływ                                                 
| ------------------ | ------------------------                               
| Anomalie danych    | ↓ Dramatycznie zmniejsza bo służy do ich usuwania      
| Spójność           | ↑ Dramatycznie zwiększa bo służy do jej zwiększenia    
| Wydajność odczytu  | ↓ Zmniejsza wymaga używania bardziej złożonych zapytań
| Wydajność zapisu   | ↑ Zwiększa bo operacje dotyczą jednego miejsca, a nie wielu duplikatów
| Przestrzeń dyskowa | ↓ Zmniejsza bo  Normalizacja eliminuje duplikację danych
| Złożoność          | ↑ Zwiększa bo normalizacja rozprasza dane na wiele tabel
| Konserwacja        | ↑ Zwiększa bo normalizacja izoluje dane, przez co zmiany są lokalne i nie rozprzestrzeniają się


# Co ma zostać wymienione
- Czym jest baza danych
- Czym jest normalizacja
- Jak normalizacja wpływa na dane
- Postacie normalne
- Postacie anomalii bazy danych
- Wady i zalety normalizacji