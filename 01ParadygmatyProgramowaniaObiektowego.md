# 01 Paradygmaty programowania obiektowego

## Programowanie obiektowe
Programowanie obiektowe organizuje kod wokół klas i obiektów, gdzie klasa definiuje atrybuty i metody odpowiedzialne kolejno za stan obiektu i jego zachowanie. A obiekt jest instancją klasy.

## Założenia paradygmatu
### Abstrakcja 
Każdy obiekt w systemie służy jako model abstrakcyjnego „wykonawcy”, który może wykonywać pracę, opisywać i zmieniać swój stan oraz komunikować się z innymi obiektami w systemie bez ujawniania, w jaki sposób zaimplementowano dane cechy. Procesy, funkcje lub metody mogą być również abstrahowane, a kiedy tak się dzieje, konieczne są rozmaite techniki rozszerzania abstrakcji. Metaforycznym przykładem abstrakcji z codziennego życia jest ekspres do kawy. Nie interesuje nas to w jaki sposób robi on naszą kawę, a jedynie to, że jeśli wcisnę odpowiedni guzik to mogę się jej spodziewać.

### Enkapsulacja  
Polega na ukrywaniu pewnych danych składowych oraz metod obiektów danej klasy tak, aby były one dostępne tylko metodom wewnętrznym danej klasy lub funkcjom zaprzyjaźnionym. Takie podejście zapewnia, że obiekt nie może zmieniać stanu wewnętrznego innych obiektów w nieoczekiwany sposób. Tylko własne metody obiektu są uprawnione do zmiany jego stanu. Każdy typ obiektu prezentuje innym obiektom swój interfejs, który określa dopuszczalne metody współpracy.

Realizacja enkapsulacji poprzez parametry dostępu:
- private - dostęp tylko w obrębie danej klasy
- protected - dostęp również po klasie po niej dziedziczące
- public - dostęp do danych w każdym miejscu programu, gdzie dostępny jest obiekt

### Dziedziczenie
Współdzielenie funkcjonalności pomiędzy klasami. Klasa "dziecka" może mieć swoje funkcjonalności oraz otrzymać funkcjonalności "rodzica" po którym dziedziczy. Z jednej klasy "rodzica" można uzyskać wiele klas potomnych. Klasy dziecka posiadają oprócz swoich funkcjonalności, również kompletny interfejs  metod i atrybutów udostępniany przez klasę rodzica

### Polimorfizm 
Mechanizmy pozwalające programiście używać wartości, zmiennych i podprogramów
na kilka różnych sposobów. Inaczej mówiąc jest to możliwość wyabstrahowania
wyrażeń od konkretnych typów. Polimorfizm dzieli się na dwa główne typy:
- Polimorfizm statyczny – odpowiedź funkcji określana jest w trakcie kompilacji
programu (przeciążanie metod, przeciążanie operatorów)
- Polimorfizm dynamiczny – odpowiedź funkcji określana jest w czasie wykonywania
programu (nadpisywanie metod z wykorzystaniem funkcji wirtualnych)

## Co ma zostać wymienione:
- Co to jest programowanie obiektowe
- Założenia paradygmatów: dziedziczenie, polimorfizm, enkapsulacja, abstrakcja