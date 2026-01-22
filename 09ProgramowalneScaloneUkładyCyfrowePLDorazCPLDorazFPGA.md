# 09 Programowalne scalone układy cyfrowe PLD, CPLD oraz FPGA

## Programowalne układy cyfrowe
Ogromną rolę w technice cyfrowej spełniają układy programowalne, często określane nazwą programowalnych modułów logicznych lub krótko hasłem PLD (programmable logic devices). Odnosi się do każdego cyfrowego układu scalonego, którego właściwości funkcjonalne mogą być zdefiniowane (ustalane) przez końcowego użytkownika, który może zaimplementować w jego strukturze opracowany przez siebie projekt jakiegoś wyspecjalizowanego układu cyfrowego. Najważniejsze cechy tych układów jest więc ich konfigurowalność przez użytkownika.

### ASIC application-specific integrated circuit / specjalizowany układ scalony

#### PLD programmable logic device

Układ PLD może zostać zaprogramowany tak, aby działał jak dowolny układ cyfrowy. Ograniczeniem jest tylko wielkość jego zasobów, czyli liczba wewnętrznych elementów, które można zaprogramować. Układy programowalne nie są procesorami, ponieważ procesor to układ o stałej strukturze wewnętrznej, natomiast struktura bramek logicznych w układach PLD zależy od tego, jak zaprogramowany jest dany układ. Najważniejsze typy układów PLD to:

- SPLD
- - **PAL programmable array logic:**
Struktura dwupoziomowa układ AND OR. Programowalna matryca AND. Najbardziej rozpowszechniona rodzina układów PLD. Produkowana początkowo głównie w dwóch technologiach:
- - - PROM: przepalane bezpieczniki, szybkie układy bipolarne
- - - EPROM – układy MOS (tranzystory?)
Obecnie stosuje się technologię EEPROM (rodzina układów PALCE używa układów
CMOS)

Nazwenoctwo układów PAL np. PAL16L8:
|PAL|16|L|8
|---|--|-|-
|PAL|Liczba wejść matrycy programowalnej|Oznaczenie rodziny układów|Liczba wyjść układu

- - **PLE programmable logic element:**
- - **PLA programmable logic array / programowalna macierz logiczna:**
W układzie PAL jest tylko jedna matryca AND, a bramki OR są wbudowane. W układach PLA natomiast funkcję bramek OR pełni właśnie druga programowalna macierz OR, co czyni te układy dużo bardziej elastycznymi.
- - **GAL generic array logic:**
Następca układów PAL posiadający możliwość wielokrotnego reprogramowania struktury logicznej. Tak jak jego protoplasta posiada układ programowalnej matrycy bramek AND, ale dodatkowo wyposażono go w programowalne makrokomórki wyjściowe OLMC (ang. Output Logic Macro Cell) pozwalające na wybór trybu pracy, dla każdego z wyjść osobno (proste, złożone, rejestrowe). Specjalna odmiana ispGAL pozwala na reprogramowanie struktury logicznej „w układzie” (ang. In-System Programming), czyli bez potrzeby wymontowywania układu scalonego z urządzenia.
- CPLD
- **FPGA field-programmable gate array / bezpośrednio programowalna macierz bramek:**

## Podsumowanie

| Cecha / Właściwość          | **SPLD**                                | **CPLD**                                         | **FPGA**                                           |
|-----------------------------|-----------------------------------------|--------------------------------------------------|----------------------------------------------------|
| **Gęstość / Pojemność**     | Kilkadziesiąt - kilkaset bramek.       | Setki - kilka tysięcy bramek.                    | Dziesiątki tysięcy - miliony bramek.              |
| **Złożoność funkcji**       | Najprostsze funkcje logiczne.          | Złożone funkcje kombiracyjne i sekwencyjne, automaty stanów. | Bardzo złożone systemy, przetwarzanie sygnałów, prototypowanie ASIC. |
| **Architektura połączeń**   | Prosta matryca wejścia/wyjścia.        | **Matryca połączeń (PIA)** o **stałym, przewidywalnym opóźnieniu**. | **Siatka segmentowych połączeń** o **zmiennym opóźnieniu** (zależnym od trasy). |
| **Podstawowy blok logiczny**| Bramki AND/OR (PAL: programowalne AND, stałe OR; PLA: programowalne obie). | **Makrokomórki** (zbiór bramek + przerzutnik).   | **CLB (Configurable Logic Block)** oparty na **LUT (Look-Up Table)** + przerzutniki. |
| **Technologia programowania** | Nieulotna (PROM, EPROM, EEPROM).       | Nieulotna (EEPROM, Flash).                       | Przeważnie **ulotna (SRAM)** – konfiguracja ładuje się z zewnętrznej pamięci. Istnieją nieulotne wersje (Flash). |
| **Prędkość działania**      | Szybkie dla prostych funkcji.          | Szybkie, deterministyczne opóźnienia.            | Bardzo szybkie, ale opóźnienia zależne od implementacji. |
| **Zużycie energii**         | Bardzo niskie.                         | Niskie/umiarkowane.                              | Umiarkowane/wysokie (zależne od rozmiaru projektu i technologii). |
| **Typowe zastosowania**     | Proste dekodery, zastępowanie kilku układów TTL. | **Logika "glue"**, kontrolery interfejsów, złożona logika zastępcza, automaty stanów. | **Systemy na układzie**, przetwarzanie sygnałów (DSP), akceleracja obliczeń, prototypowanie ASIC, sieci neuronowe. |
| **Cykl projektowy**         | Bardzo szybki i prosty.                | Szybki, przewidywalny.                           | Złożony, wymaga zaawansowanych narzędzi do syntezy, mapowania i routingu. |
| **Koszt (jednostkowy)**     | Bardzo niski.                          | Niski/umiarkowany.                               | Umiarkowany/wysoki (zależnie od rozmiaru).         |
| **Elastyczność**            | Bardzo ograniczona.                    | Średnia, dobra dla logiki kombinacyjnej.         | **Bardzo wysoka** – możliwość implementacji dowolnej logiki mieszanej. |
| **Podsumowanie (Rola)**     | **Podstawowa "logika zastępcza"**.     | **Zaawansowana "logika zastępcza" i prostsze automaty**. | **Platforma systemowa / "System na chipie"**.      |