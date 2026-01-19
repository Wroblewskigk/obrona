# 13 Metody tworzenia harmonogramu projektu

https://www.perplexity.ai/search/opracuj-mi-nastepujace-tresci-OVHbWh0qRLupSm2nDQWNKQ#0

https://mfiles.pl/pl/index.php/Wykresy_sieciowe

https://mfiles.pl/pl/index.php/Wykres_Gantta

Harmonogram projektu stanowi fundamentalny dokument w zarządzaniu projektami, pełniący funkcję mapy drogowej dla całego przedsięwzięcia. Skuteczne harmonogramowanie wpływa bezpośrednio na powodzenie projektu, pozwalając menedżerom na koordynację działań, kontrolę postępów, zarządzanie zasobami i minimalizowanie ryzyka opóźnień.

## Wykresy Gantta

Wykres Gantta jest graficznym sposobem planowania i kontroli. Planowanie i koordynowanie przebiegu różnych czynności w przekroju czasowym odgrywa istotną rolę w tworzeniu i funkcjonowaniu organizacji. Wykresy Gantta służą do planowania działań wielopodmiotowych zarówno zespołowych, jak i grupowych. Przedstawiają następstwo kolejnych zdarzeń, uwzględniając również zadania wykonywane równolegle. Dzięki tej technice można także kontrolować realizację zaplanowanego przedsięwzięcia.

**TLDR;** Wykres Gantta to narzędzie planowania i kontroli, które przedstawia kolejność zadań i umożliwia kontrolowanie realizacji projektu. Powstał w 1917 roku i rozwijał się dzięki komputerom. Wykres Gantta umożliwia planowanie, kontrolę i optymalizację projektów. Może być stosowany w różnych dziedzinach. Istnieją różne rodzaje powiązań między zadaniami w harmonogramie Gantta. Zalety to m.in. automatyczne wyznaczanie ścieżki krytycznej i przejrzyste przedstawienie harmonogramu. Wady to brak szczegółowych informacji i trudności w analizie większych projektów. Najczęstsze błędy to nadmiar informacji i posiadanie zbyt dużej liczby wersji wykresu.

### Zalety i Zastosowania
Wykresy Gantta dostarczają licznych korzyści:

- Wizualna klarowność – Pozwalają na szybkie zrozumienie harmonogramu przez wszystkie zainteresowane strony
- Śledzenie postępów – Umożliwiają porównanie zaplanowanego harmonogramu z rzeczywistym postępem prac
- Zarządzanie zależnościami – Jasno pokazują, które zadania mogą się odbywać równolegle, a które wymagają sekwencji
- Identyfikacja wąskich gardeł – Ułatwiają zauważenie zadań mogących spowodować opóźnienia całego projektu
- Komunikacja – Stanowią uniwersalny dokument komunikacyjny dla zespołu i interesariuszy

### Ograniczenia
Mimo ich popularności, wykresy Gantta posiadają kilka ograniczeń:

- Złożoność dla dużych projektów – W przypadku projektów o wielu tysiącach zadań mogą stać się trudne do czytania i zarządzania
- Brak informacji o ryzyka – Nie zawierają informacji o probabilistycznym charakterze czasów realizacji
- Statyczność – Papierowy wykres Gantta szybko przestaje być aktualny; wymaga stałych aktualizacji
- Niedostęp do obliczeniowych aspektów – Nie wskazują wprost ścieżki krytycznej ani marż czasowych

## Wykresy Czynności

Wykresy czynności, znane również jako diagramy sieciowe, stanowią narzędzie reprezentujące projekt w postaci sieci powiązanych działań i zdarzeń. Różnią się od wykresów Gantta tym, że uwzględniają logikę przyczynowo-skutkową między czynnościami oraz umożliwiają matematyczne obliczenia czasowe.

**TLDR;** Wykresy sieciowe to metody opracowane w latach 50. i 60. dla projektów przemysłu zbrojeniowego. Najpopularniejsze to CPM i PERT. Procedura opracowania wykresu obejmuje podział projektu na zadania, ustalenie kolejności, określenie czasu trwania, wykreślenie sieci i drogi krytycznej. Zalety wykresów sieciowych to skrócenie czasu realizacji projektu, zmniejszenie kosztów, koncentracja na czynnościach krytycznych i ułatwienie planowania. Metoda ścieżki krytycznej (CPM) służy do określenia terminu zakończenia projektu, a technika PERT do operacji niepowtarzalnych. Dwa najbardziej znane wykresy, to:

- CPM - Critical Path Method - metoda ścieżki krytycznej,
- PERT - Program Evaluation and Review Technique - technika oceny i przeglądu projektów.

### Podstawowe pojęcia

- Czynność, zadanie - działanie określone w czasie, a więc posiadające czas trwania. Na wykresie CPM zaznacza się ją strzałką, natomiast w PERT - prostokątem.
- Zdarzenie - moment zakończenia lub rozpoczęcia czynności. Jest punktem na skali czasu, a więc nie posiada swojego wymiaru czasowego. W PERT nie występuje. Na wykresie CPM zaznaczany jest kółkiem. Kółko to należy podzielić na 4 części znakiem X. W górnej części wpisywany jest numer kolejny, po lewej najwcześniejszy możliwy termin wystąpienia, po prawej najpóźniejszy dopuszczalny termin wystąpienia, a na dole rezerwę czasu.
- Ścieżka krytyczna - droga od pierwszego do ostatniego zdarzenia poprzez wszystkie zdarzenia i czynności posiadające rezerwę zerową.
- Najwcześniejszy możliwy termin wystąpienia (NM) zdarzenia wyznaczamy sumując czas czynności, dla której zdarzenie jest końcowym, oraz najwcześniejszy termin zdarzenia poprzedniego dla tej czynności. Jeżeli takich sum można wyznaczyć więcej niż jedną (np. wykres się wcześniej rozgałęzia), wybieramy maksymalną wartość zgodnie z zasadą mówiącą, że zdarzenie może nastąpić, gdy wcześniej zakończą się wszystkie czynności je poprzedzające. Dla zdarzenia początkowego najwcześniejszy termin wynosi "0".
- Najpóźniejszy dopuszczalny termin wystąpienia (ND) zdarzenia otrzymujemy odejmując od najpóźniejszego terminu wystąpienia zdarzenia kończącego czas trwania czynności. Jeśli wykres za zdarzeniem się rozgałęzia, wyznaczamy najmniejszą wartość.
- Rezerwa czasu dla zdarzenia jest równa różnicy najpóźniejszego i najwcześniejszego terminu. Dla zdarzenia kończącego wykres oba terminy są równe, a rezerwa równa "0". Jeżeli ciąg czynności trwających najdłużej biegnie przez zdarzenia, dla których rezerwa wynosi "0", nazywamy go ciągiem krytycznym.

### Metoda PERT - Program Evaluation and review technique / technika oceny i przeglądu projektów

Metoda ta powstała w 1958 roku w Stanach Zjednoczonych. Została ona stworzona przez matematyków pracujących w Amerykańskim Biurze Systemów Morskich. Tym co odróżnia metodę PERT od metody CPM są elementy mianowane, którymi w tym wypadku są wierzchołki tworzące sieć zdarzeń. Metodę PERT wykorzystuje się w odniesieniu do operacji niepowtarzalnych. Technika kontroli i oceny programu działania jest modelem stochastycznym, ponieważ czas trwania poszczególnych działań nie jest w niej określany dokładnie, jedynie z pewnym prawdopodobieństwem. Dzięki temu łatwiej jest zastosować odpowiedni program komputerowy. Koszty wykonania poszczególnych zadań również można określić w przybliżeniu. Technikę kontroli i oceny programu działania PERT stosujemy więc przy założeniu, że pracujemy w warunkach niepewności. W metodzie PERT każdej czynności przyporządkowujemy cztery szacunki czasu: optymistyczny, najbardziej prawdopodobny, pesymistyczny oraz oczekiwany

PERT bazuje na koncepcji trzypunktowej estymacji, uwzględniającej niepewność i ryzyko związane z oszacowaniem czasu realizacji czynności. Trzy szacunki dla każdej czynności to:

1. Szacunek Optymistyczny (O – Optimistic Estimate) – Najkrótszy możliwy czas realizacji czynności, zakładając, że wszystko przebiega lepiej niż zazwyczaj. Reprezentuje scenariusz best-case.
2. Szacunek Najbardziej Prawdopodobny (M – Most Likely Estimate) – Czas, który eksperty uważają za najbardziej realistyczny na bazie doświadczenia i historycznych danych. To szacunek modalny rozkładu czasu.
3. Szacunek Pesymistyczny (P – Pessimistic Estimate) – Najdłuższy możliwy czas realizacji czynności, zakładając, że napotka się problemy i opóźnienia. Reprezentuje scenariusz worst-case.

### Metoda CPM - Critical path method / ścieżka krytyczna 

Metoda ta została opracowana w latach 1956-1957 w Stanach Zjednoczonych przez firmę Du Pont de Nemours & Co. Była ona wykorzystywana do zarządzania konserwacją urządzeń wykorzystywanych w procesach ciągłych koncernu. Metoda ścieżki krytycznej miała doprowadzić do uporządkowania organizacyjnego, co miało spowodować wzrost efektywności firmy. Nie ma wyraźnie określonego sposobu prezentacji grafu dla metody ścieżki krytycznej. Aby móc zastosować metodę CPM konieczne jest posiadanie danych na temat czasu trwania poszczególnych działań. Na ogół nie zawsze jest to możliwe i wtedy nie można skorzystać z metody ścieżki krytycznej, ponieważ jest ona modelem deterministycznym, czyli częściami mianowanymi są krawędzie grafu tworzone przez działania o znanym czasie trwania. Metoda CPM ma za zadanie określić całościowy czas realizacji bądź termin zakończenia przedsięwzięcia. Ma ona zastosowanie, gdy mamy do czynienia z operacjami powtarzalnymi

### Procedura opracowania wykresu

1. Podział projektu na zadania i czynności
2. Ustalenie logicznego następstwa poszczególnych czynności
3. Określenie czasu trwania czynności
4. Wykreślenie sieci
5. Ustalenie najwcześniejszych możliwych i najpóźniejszych dopuszczalnych terminów wystąpienia zdarzeń
6. Wyliczenie rezerw czasu
7. Wykreślenie drogi krytycznej
8. Interpretacja rezerw czasu
9. Ewentualne udoskonalenie sieci (skrócenie ścieżki krytycznej) - powrót do 4

### Zasady konstruowania wykresów sieciowych
- Zdarzenia początkowe nie mają czynności poprzedzających,
- Zdarzenia końcowe nie mają czynności następujących po nich,
- Wykres sieciowy może mieć kilka początkowych i kilka końcowych zdarzeń i wówczas łączy się je czynnościami pozornymi w jedno zdarzenie początkowe i jedno zdarzenie końcowe,
- Dane zdarzenie nie może nastąpić, dopóki nie zakończą się wszystkie czynności prowadzące do niego i warunkujące zajście tego zdarzenia,
- Żadna kolejna czynność nie może się rozpocząć, dopóki nie zaistnieje zdarzenie kończące czynności poprzedzające,
- Pomiędzy dwoma zdarzeniami może być zawieszona tylko jedna czynność,
wektory czynności powinny być skierowane z lewej strony do prawej,
- Należy unikać skrzyżowań wektorów,
- Wykres sieciowy rozgałęzia się w kierunku wykonywania czynności od strony lewej do prawej,
- Wykres sieciowy nie powinien mieć obiegów zamkniętych, tj. pętli łączących dwukrotnie te same zdarzenia,
- Każdy sporządzony wykres należy uzgodnić z odpowiedzialnymi wykonawcami, - sprawdzić kolejność czynności, prawidłowość powiązań (następstwo, równoległość czynności), a następnie przeprowadzić obliczenie czasu trwania całego przedsięwzięcia, luzów czasu oraz zaznaczyć drogę krytyczną.

## WBS – Work breakdown structure / struktura podziału pracy

Struktura podziału pracy (WBS) to hierarchiczny opis działań i zadań potrzebnych do wykonania projektu. Może mieć różną liczbę poziomów w zależności od skomplikowania projektu. WBS ma zastosowanie jako narzędzie myślowe, projektowania architektury, planowania i raportowania o stanie projektu. Tworzenie WBS wymaga spełnienia sześciu kryteriów. Istnieją trzy podejścia do tworzenia WBS: przedmiotowe, czynnościowe i organizacyjne. Metody tworzenia WBS to: zstępująca i burza mózgów. Istnieją różne formaty prezentacji WBS, np. schemat organizacyjny, lista wielopoziomowa, wykres bąbelkowy.

Istnieje trzy podejścia do tworzenia struktury podziału prac:

- Podejście przedmiotowe - definiujemy rezultaty pracy w ramach projektu poprzez ich części składowe umożliwiające osiąganie tych rezultatów (rekomendowane przez Instytut Zarządzania Projektami - PMI),
- Podejście czynnościowe - definiujemy rezultaty projektu poprzez działania, które trzeba wykonać, aby rezultaty zostały osiągnięte (np.:projektuj-buduj-testuj-wdrażaj oraz podejście od strony celów cząstkowych projektu),
- Podejście organizacyjne - definiujemy rezultaty projektu poprzez jednostki organizacyjne biorące udział w pracach (działy, procesy, lokalizacja geograficzna).

Przykład WBS dla projektu oprogramowania:
```
Projekt: System e-commerce
├── Faza 1: Planowanie
│   ├── Analiza wymagań
│   ├── Projektowanie architektury
│   └── Planowanie zasobów
├── Faza 2: Implementacja
│   ├── Moduł Frontend
│   │   ├── Strona główna
│   │   ├── Koszyk zakupów
│   │   └── Profil użytkownika
│   ├── Moduł Backend
│   │   ├── Zarządzanie użytkownikami
│   │   ├── Zarządzanie produktami
│   │   └── Przetwarzanie płatności
│   └── Integracja z bazą danych
├── Faza 3: Testowanie
│   ├── Testy jednostkowe
│   ├── Testy integracyjne
│   └── Testy końcowe
└── Faza 4: Wdrożenie i konserwacja
    ├── Wdrożenie produkcyjne
    ├── Szkolenie użytkowników
    └── Wsparcie powidrażeniowe
```

### Zastosowania struktury podziału pracy
WBS ma cztery zastosowania, czyli jest:

1. Narzędziem procesu myślowego (planowania i projektowania) - pomaga menedżerowi projektu i zespołowi projektowemu wizualizować sposób, w jaki praca będzie przeprowadzona i efektywnie zarządzana,
2. Narzędziem projektowania architektury (graficzna ilustracja pracy w projekcie) - pokazuje, w jaki sposób poszczególne części są ze sobą powiązane,
3. Narzędziem planowania - służy zespołowi projektowemu jako szczegółowa prezentacja zbioru zadań, które muszą być wykonane w celu ukończenia projektu,
4. Narzędziem raportowania o stanie projektu (wyższe poziomy działań wynikają z działań na poziomach niższych) - definiowanie punktów kontrolnych, w odniesieniu do których zostanie raportowany postęp prac nad projektem.
   
Struktura podziału prac jest podstawą planowania, ponieważ dzięki jej zespól dysponuje informacjami umożliwiającymi:

- Dokonanie podziału obowiązków,
- Przypisanie zadania do określonych zasobów,
- Oszacowanie czasu potrzebnego do zakończenia poszczególnych zadań oraz ogólnego horyzontu czasowego projektu,
- Opracowanie budżetu przedsięwzięcia,
- Zorganizowanie systemu monitorowania i tworzenia raportu na temat dokonywanych postępów oraz zużytych środków finansowych,
- Prognozowanie wydatków koniecznych do zakończenia projektu lub kamienia milowego,
- Identyfikowanie i analizowanie problemów związanych z planem przedsięwzięcia.

## Zarządzanie czasem

Gdy projekt grozi opóźnieniem, dostępne są dwie główne techniki kompresji harmonogramu:

### Crashing - Skrócenie harmonogramu

Crashing to technika skrócenia czasu trwania projektu przez dodatkowe alokacje zasobów (więcej personelu, dodatkowych godzin pracy, sprzętu). Kluczowe cechy:

- Mechanizm: Dodawanie zasobów bezpośrednio do czynności krytycznych
- Koszt: Znaczący wzrost kosztów (pensje, overtimie, potencjalne bonusy)
- Efektywność: Nie zawsze proporcjonalna – dodawanie zasobów może prowadzić do zmniejszenia efektywności (zjawisko law of diminishing returns)
- Ryzyko: Wzrost kosztów, potencjalna degradacja jakości
- Warunki: Efektywne, gdy projekt ma sztywne terminy, a budżet jest elastyczny

**Przykład Crashing:**
Projekt inicjalnie zaplanowany na 200 dni musi być ukończony w 180 dni. Zostaje zidentyfikowana ścieżka krytyczna zawierająca czynności zajmujące 40 dni. Zespół decyduje się na zwiększenie obsady z 3 do 5 osób na tej ścieżce. Koszt dodatkowy wyniesie 50 tys. zł, ale projekt zostanie ukończony w terminie.

### Fast-Tracking - przyspieszenie harmonogramu

Fast-tracking to technika skrócenia harmonogramu poprzez wykonywanie czynności równolegle (overlap), które pierwotnie były zaplanowane sekwencyjnie. Kluczowe cechy:

- Mechanizm: Reorganizacja sekwencji czynności; rozpoczynanie następnej czynności zanim poprzednia jest w pełni ukończona
- Koszt: Minimalny wzrost kosztów (głównie komunikacja i koordynacja)
- Efektywność: Może skrócić harmonogram znacznie, o ile jest dużo możliwości do paralelizacji
- Ryzyko: Wysokie – równoległe wykonywanie czynności może prowadzić do rework'u, jeśli zmienią się wymagania wcześniejszych faz
- Warunki: Lepsze, gdy ryzyko projektowe jest akceptowane, ale budżet jest ograniczony

**Przykład Fast-Tracking:**
W projekcie budowlanym, zamiast czekać na całkowite ukończenie fundamentów (30 dni) przed rozpoczęciem ścian (40 dni), można rozpocząć wznoszenie ścian na już ukończonych fundamencie (po 20 dniach). Oszczędza to 10 dni, ale wiąże się z ryzykiem konieczności demolowania części ścian, jeśli odkryje się problem w fundamentach.

| Aspekt          | Crashing                           | Fast-Tracking                           |
| --------------- | ---------------------------------- | --------------------------------------- |
| Mechanizm       | Dodatkowe zasoby                   | Paralelizacja czynności                 |
| Wpływ na koszt  | Znaczny wzrost                     | Minimalny wzrost                        |
| Wpływ na ryzyko | Umiarkowany wzrost                 | Znaczny wzrost                          |
| Kiedy stosować  | Sztywne terminy, elastyczny budżet | Ograniczony budżet, akceptowalne ryzyko |
| Efektywność     | Zależy od ograniczeń zasobowych    | Zależy od niezależności czynności       |

## Zarządzanie zasobami

Jednym z największych wyzwań w zarządzaniu harmonogramem jest optymalny rozkład zasobów, szczególnie gdy ich dostępność jest ograniczona.

### Resource Leveling - Równoważenie zasobów

Resource leveling to technika optymalizacji zasobów, w której dostosowuje się harmonogram projektu do dostępnych zasobów, potencjalnie przedłużając termin realizacji projektu.

Charakterystyka:

- Cel: Uniknięcie przeciążenia zasobów i zapewnienie równomiernego rozłożenia obciążenia
- Mechanizm: Modyfikacja czasów rozpoczęcia i ukończenia czynności, aby rozłożyć zapotrzebowanie na zasoby
- Wynik: Może skutkować wydłużeniem projektu, jeśli liczba zasobów jest niewystarczająca
- Zastosowanie: Gdy ograniczenia zasobowe są bardziej krytyczne niż terminy
- Narzędzia: Microsoft Project, Smartsheet i inne narzędzia zarządzania projektami mają wbudowane algorytmy leveling

Procedura Resource Leveling:

1. Zidentyfikowanie czynności z nadmiarem zapotrzebowania na zasoby
2. Przeanalizowanie możliwości przesuniętych czasów dostępnych zasobów (slack)
3. Przesunięcie niekrytycznych czynności, aby wyrównać obciążenie
4. Jeśli to nie wystarczy, przesunięcie lub podzielenie czynności krytycznych (z możliwym wydłużeniem projektu)
5. Weryfikacja, że przeprojektowany harmonogram spełnia ograniczenia

### Resource Smoothing - Wygładzanie zasobów

Resource smoothing to technika, w której dostosowuje się alokację zasobów bez przedłużenia czasu trwania projektu. Różni się od levelingu tym, że nie wpływa na ścieżkę krytyczną.

Charakterystyka:

- Cel: Wyrównanie obciążenia zasobów, zachowując oryginalny termin projektu
- Mechanizm: Wykorzystanie dostępnego slack time w czynnościach niekrytycznych, aby przesunąć zadania i wyrównać obciążenie
- Wynik: Projekt kończy się w pierwotnie zaplanowanym terminie
- Zastosowanie: Gdy termin projektu jest sztywny, a zasoby muszą być równomiernie rozłożone (np. dla optymalnego wykorzystania team velocity)
- Ograniczenie: Może być niemożliwe, jeśli wszystkie zasoby są już w pełni wykorzystane bez slack time

| Aspekt                     | Resource Leveling                               | Resource Smoothing                |
| -------------------------- | ----------------------------------------------- | --------------------------------- |
| Wpływ na termin            | Może wydłużyć projekt                           | Nie zmienia terminu               |
| Wpływ na ścieżkę krytyczną | Może zmienić ścieżkę krytyczną                  | Nie zmienia ścieżki krytycznej    |
| Kiedy stosować             | Zasoby są głównym ograniczeniem                 | Termin jest głównym ograniczeniem |
| Efekt                      | Wyrównanie rzeczywistych zasobów do dostępności | Wyrównanie rozkładu obciążenia    |