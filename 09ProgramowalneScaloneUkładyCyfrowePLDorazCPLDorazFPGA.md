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

#### Gate Arrays

#### Standard Cell

#### Full Custom

# Co ma zostać wymienione