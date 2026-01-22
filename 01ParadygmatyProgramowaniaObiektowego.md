# 01 Paradygmaty programowania obiektowego

## Programowanie obiektowe
Programowanie obiektowe organizuje kod wokół klas i obiektów, gdzie klasa definiuje atrybuty i metody odpowiedzialne kolejno za stan obiektu i jego zachowanie. Obiekt jest instancją danej klasy.

## Założenia paradygmatu
### Abstrakcja 
Abstrakcja to proces wydzielający istotne cechy obiektów i pomijający te nieistotne. Prowadzi do tworzenia pojęć ogólnych, oderwanych od konkretnej rzeczywistości. W programowaniu obiektowym polega na upraszczaniu złożonych systemów przez izolowanie najważniejszych cech obiektu lub metody i ukrywanie szczegółów implementacji tzw. "czarna skrzynka". Metaforycznym przykładem abstrakcji z codziennego życia jest ekspres do kawy. Nie interesuje nas to w jaki sposób robi on naszą kawę, a jedynie to, że jeśli wcisnę odpowiedni guzik to mogę się jej spodziewać. Można też wejść na wyższy poziom abstrakcji przechodząc od ekspresu do ogólniejszego pojęcia maszyny.

### Hermetyzacja (Enkapsulacja) (Separacja)
Zapewnia, że obiekt nie może zmieniać stanu wewnętrznego innych obiektów w nieoczekiwany sposób. Tylko wewnętrzne metody obiektu są uprawnione do zmiany jego stanu. Każdy typ obiektu prezentuje innym obiektom swój interfejs, który określa dopuszczalne metody współpracy.

Realizacja enkapsulacji może przebiegać poprzez parametry dostępu:
- ```private``` - Dostęp tylko w obrębie danej klasy
- ```protected``` - Dostęp również po klasie po niej dziedziczącej
- ```public``` - Dostęp do danych w każdym miejscu programu

### Dziedziczenie (Kompozycja)
Polega na stworzeniu nowej klasy, zwanej podklasą, na podstawie istniejącej już
klasy bazowej, zwanej nadklasą. Wspólne atrybuty i metody są definiowane w nadklasie i potem dziedziczone przez podklasę. Dziedziczenie umożliwia definiowanie wyspecjalizowanych obiektów na podstawie bardziej ogólnych. Nie trzeba wtedy redefiniować wszystkich funkcjonalności, więc wymagana jest implementacja tylko tych, których nie ma obiekt ogólniejszy. Wyróżniamy dziedziczenie pojedyncze i wielokrotne. Jeżli nowa klasa jest podklasą tylko jednej klasy bazowej, to wtedy mówimy o dziedziczeniu pojedynczym. Analogicznie dziedziczone jest po więcej niż jednej nadklasie mamy do czynienia z dziedziczeniem wielokrotnym.

### Polimorfizm (Wielopostaciowość)
Mechanizmy pozwalające programiście używać wartości, zmiennych i podprogramów
na kilka różnych sposobów. Inaczej mówiąc jest to możliwość wyabstrahowania
wyrażeń od konkretnych typów. Polimorfizm dzieli się na dwa główne typy:
- Polimorfizm statyczny – odpowiedź funkcji określana jest w trakcie kompilacji
programu (przeciążanie metod, przeciążanie operatorów)
- Polimorfizm dynamiczny – odpowiedź funkcji określana jest w czasie wykonywania
programu (nadpisywanie metod z wykorzystaniem funkcji wirtualnych)

# Rodzaje Polimorfizmu

| Rodzaj polimorfizmu       | Kiedy decyzja o konkretnej metodzie? | Mechanizm w większości języków          | Przykład w praktyce                          | Najczęściej spotykany w       |
|---------------------------|---------------------------------------|------------------------------------------|-----------------------------------------------|-------------------------------|
| **Statyczny** (czas kompilacji) | W czasie kompilacji                  | Przeciążanie funkcji/metod/operatorów    | Różne sygnatury tej samej nazwy metody        | C++, Java, C#                 |
| **Dynamiczny** (czas wykonania) | W czasie wykonywania programu        | Nadpisywanie metod + późne wiązanie      | Wywołanie metody przez referencję do klasy bazowej | Prawie wszystkie języki OOP   |
| **Parametryczny** (generyczny)  | Częściowo kompilacja / częściowo runtime | Szablony / generyki                      | Lista<T>, ArrayList<T>                        | Java, C#, C++, TypeScript     |
| **Ad-hoc**                | Czas kompilacji                      | Przeciążanie operatorów, konwersje       | operator+, operator<< w C++                   | C++, Python (duck typing)     |

## Zasady SOLID

| Inicjał | Skrót | Koncepcja                                                                                                                                                                                                                                                            |
| ------- | ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| S       | SRP   | Single responsibility principle (Zasada jednej odpowiedzialności) Klasa powinna mieć tylko jedną odpowiedzialność (nigdy nie powinien istnieć więcej niż jeden powód do modyfikacji klasy)​                                                               |
| O       | OCP   | Open/closed principle (Zasada otwarte-zamknięte) Klasy (encje) powinny być otwarte na rozszerzenia i zamknięte na modyfikacje​                                                                                                                            |
| L       | LSP   | Liskov substitution principle (Zasada podstawienia Liskov) Funkcje, które używają wskaźników lub referencji do klas bazowych, muszą być w stanie używać również obiektów klas dziedziczących po klasach bazowych, bez dokładnej znajomości tych obiektów​ |
| I       | ISP   | Interface segregation principle (Zasada segregacji interfejsów) Wiele dedykowanych interfejsów jest lepsze niż jeden ogólny​                                                                                                                              |
| D       | DIP   | Dependency inversion principle (Zasada odwrócenia zależności) Wysokopoziomowe moduły nie powinny zależeć od modułów niskopoziomowych – zależności między nimi powinny wynikać z abstrakcji​                                                               |

## Co ma zostać wymienione:
- Co to jest programowanie obiektowe
- Założenia paradygmatów: dziedziczenie, polimorfizm, enkapsulacja, abstrakcja
- SOLID