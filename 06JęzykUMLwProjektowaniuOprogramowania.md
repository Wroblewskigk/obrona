# 06 Jeżyk UML w projektowaniu oprogramowania

## Czym jest UML?

UML (Unified Modeling Language) został opracowany w celu stworzenia wspólnego, bogatego semantycznie i składniowo wizualnego języka modelowania dla architektury, projektowania i implementacji złożonych systemów oprogramowania, zarówno pod względem strukturalnym, jak i behawioralnym. UML jest stosowany nie tylko przy tworzeniu oprogramowania, ale także w procesach produkcyjnych.

Jest on analogiczny do schematów używanych w innych dziedzinach i składa się z różnych rodzajów diagramów. Ogólnie rzecz biorąc, diagramy UML opisują granice, strukturę i zachowanie systemu oraz obiektów w nim zawartych.

UML nie jest językiem programowania, ale istnieją narzędzia, które mogą być używane do generowania kodu w różnych językach przy użyciu diagramów UML. UML ma bezpośredni związek z analizą i projektowaniem zorientowanym obiektowo.

UML złożony jest z dwóch podstawowych elementów: **notacji** (reprezentacja graficzna, elementy graficzne, które widad w modelach – składnia języka modelowania) oraz **metamodelu** (definicje pojęd i powiązania, jest to nadanie modelom większej ścisłości bez poświęcania ich przydatności). W
modelowaniu ważniejsza jest notacja, natomiast podczas generowania kodu ważniejszy jest metamodel. Języka UML można używad podczas tworzenia wyprzedzającego jak i odtwarzania wstecznego. Oznacza to, że diagram UML można stworzyd przed napisaniem kodu programu jak również można go skonstruowad dla istniejącego kodu w celu lepszego zrozumienia go.

## Hierarchia rodzaji diagramów UML

```
UML (14)
├── STRUKTURALNE (7)
│   ├── Diagram klas
│   ├── Diagram obiektów
│   ├── Diagram pakietów
│   ├── Diagram komponentów
│   ├── Diagram wdrożenia
│   ├── Diagram struktur złożonych
│   └── Diagram profilu
│
└── BEHAWIORALNE (7)
    ├── Diagram przypadków użycia
    ├── Diagram aktywności / czynności
    ├── Diagram stanów
    └── INTERAKCJI (4)
        ├── Diagram sekwencji / przebiegu
        ├── Diagram komunikacji
        ├── Diagram przeglądu interakcji
        └── Diagram uwarunkowań czasowych
```

## Rodzaje diagramów UML

### Diagramy strukturalne

Diagramy strukturalne modelują statyczne aspekty systemu, reprezentując komponenty, klasy, obiekty oraz relacje między nimi. Stanowią fundament dla zrozumienia architektury i organizacji systemu.

#### Diagram klas

Diagram klas przedstawia klasy występujące w systemie i relacje pomiędzy nimi. Jest podstawowym diagramem struktury logicznej systemu. Diagram klas jest jednym z najczęściej używanych diagramów UML. Na diagramie prezentowane są klasy, ich atrybuty i operacje, oraz powiČzania miħdzy klasami

Możliwe relacje w diagramie klas:

- Zależność
- Asocjacja
- Agregacja częściowa
- Kompozycja / Agregacja całkowita
- Dziedziczenie / Uogólnienie

#### Diagram obiektów

```
Diagramy obiektów są budowane w celu sprawdzenia, czy diagram funkcjonuje we właściwy sposób. Na przykład, można utworzyć przypadek testowy przy użyciu diagramu obiektów, aby sprawdzić, czy diagram klas jest wykonalny i kompletny.
```

#### Diagram pakietów

Diagramy pakietów pokazują relacje pomiędzy różnymi pakietami w systemie. Symbol folderu plików jest używany do reprezentowania pakietu, a pakiet może zawierać różne komponenty, grupy, a nawet inne pakiety. Diagramy pakietów pokazują zatem złożone systemy, które składają się z dużych komponentów.

#### Diagram komponentów

Diagramy komponentów są używane w celu rozbicia złożonych systemów na ich kompon enty, aby uzyskać uproszczoną wizualną reprezentację systemu.

#### Diagram wdrożenia

#### Diagram struktur złożonych

Przedstawia wewnętrzną strukturę obiektu oraz punkty interakcji z innymi obiektami w systemie. Obiekt składa się z części, które reprezentują poszczególne składowe obiektu realizujČce poszczególne funkcje obiektu. Komunikacja pomiędzy obiektem, a jego środowiskiem przebiega poprzez port (oznaczany jako mały prostokąt umieszczony na krawędzi obiektu). Porty są połączone z częściami obiektu, które są odpowiedzialne za realizacje tych funkcji

Złożone diagramy struktury są rzadko używane, ponieważ ich funkcja jest bardzo specyficzna. Pokazują one wewnętrzną strukturę klas oraz interakcję pomiędzy komponentami klas.

#### Diagram profilu

### Diagramy behawioralne / Diagramy zachowań

#### Diagram sekwencji / przebiegu

#### Diagram komunikacji

Diagramy komunikacji, znane również jako diagramy współpracy, są używane do pokazania przepływu wiadomości pomiędzy obiektami oraz sposobu, w jaki obiekty komunikują się ze sobą. Przypominają one diagramy sekwencji. Jednak w diagramach komunikacyjnych używane są połączenia asocjacyjne i podczas gdy diagramy sekwencji budowane są pionowo, diagramy komunikacyjne budowane są za pomocą schematów numerycznych.

#### Diagram przeglądu interakcji

#### Diagram uwarunkowań czasowych

#### Diagram przypadków użycia

Diagramy przypadków użycia są używane do modelowania aktorów w systemie, sposobu działania tych aktorów i interakcji pomiędzy działaniami. Aktorzy są pokazani jako figurki i mogą reprezentować ludzi lub organizacje. Funkcje są pokazane jako czasowniki, które reprezentują działania, a związek pomiędzy aktorami i funkcjami jest pokazany za pomocą prostych strzałek.

Czym może być aktor:

Czym jest przypadek użycia:

#### Diagram aktywności / czynności

#### Diagram stanów

Znany jest również jako diagram maszyny stan ów i diagramy wykresów stan ów do wyświetlania przejść. Są one używane do przedstawiania systemów, które zawierają obiekt zachowujący się reaktywnie na bodźce zewnętrzne i stan, w którym się znajduje. Diagram stanów daje informacje o możliwych stanach obiektu i jego przejściu z jednego do drugiego.

#### Diagram czynności

## Ocena jakości modelu UML

Ocena jakości modelu UML opiera się na dwóch kluczowych rodzajach poprawności: syntaktycznej i semantycznej, które zapewniają, że model jest zarówno formalnie poprawny, jak i użyteczny w praktyce.

### Poprawność syntaktyczna 

Sprawdza zgodność elementów modelu z regułami składni UML – np. czy połączenia między klasami mają właściwą linię przerywaną lub ciągłą, czy mnożniki kardynalności są poprawnie zapisane. Naruszenia syntaktyki uniemożliwiają automatyczne przetwarzanie modelu przez narzędzia, takie jak generatory kodu.

### Poprawność semantyczna 

Weryfikuje, czy model wiernie odzwierciedla rzeczywistość biznesową lub wymagania systemu – np. czy diagram przypadków użycia obejmuje wszystkie istotne akcje aktorów. Dodatkowe kryteria jakości to kompletność (wszystkie aspekty systemu), spójność (brak sprzeczności między diagramami) oraz prostota (minimalna złożoność bez utraty informacji).

### Metody oceny

- Narzędzia automatyczne: Sprawdzają syntaktykę (np. Enterprise Architect, Visual Paradigm).
- Recenzje eksperckie: Oceniają semantykę i spójność podczas walkthroughs
- Symulacje: Testują zachowanie modelu, np. poprzez animację diagramów aktywności.
​

# Co ma zostać wymienione
- Co to jest UML
- Rodzaje diagramów UML
- Ocena jakości modelu