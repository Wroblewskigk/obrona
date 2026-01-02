
## Arytmetyka stałoprzecinkowa

Arytmetyka stałoprzecinkowa (ang. fixed-point arithmetic) reprezentuje liczby rzeczywiste poprzez zarezerwowanie stałej liczby bitów dla części całkowitej i ułamkowej. Pozycja przecinka ustalana jest z góry i pozostaje niezmienną — na przykład w 16-bitowym formacie można przydzielić 8 bitów na część całkowitą i 8 na część ułamkową. Wartość liczby obliczana jest analogicznie do pozycyjnego systemu liczbowego: bity części całkowitej posiadają wagi 2^k, 2^(k-1),..., 2^0, natomiast bity części ułamkowej wagi 2^(-1), 2^(-2),..., 2^(-n).

Kluczową cechą jest funkcjonalny trade-off: zwiększenie precyzji wymaga zmniejszenia zakresu liczb całkowitych i vice versa. Arytmetyka stałoprzecinkowa była normą w kalkulatorach mechanicznych i pozostaje stosowana w systemy wbudowanych o ograniczonych możliwościach arytmetycznych (mikrokontrolery, FPGA) oraz w aplikacjach wymagających wysokiej szybkości lub niskiego poboru mocy, takich jak przetwarzanie obrazu i sygnałów cyfrowych.

## Arytmetyka zmiennoprzecinkowa

Arytmetyka zmiennoprzecinkowa (ang. floating-point arithmetic) bazuje na notacji naukowej, reprezentując liczby w formacie: x = S · M · 2^E, gdzie S jest znakiem, M znormalizowaną mantysą (z przedziału [1, 2)), a E jest cechą (wykładnikiem). Mantysa i cecha są kodowane jako liczby stałoprzecinkowe, ale pozycja przecinka w liczbie całkowitej zmienia się wraz ze zmianą cech — stąd nazwa reprezentacji.
​
Standard IEEE 754 unormował arytmetykę zmiennoprzecinkową, gwarantując identyczne obliczenia na wszystkich komputerach. Format ten pozwala reprezentować znacznie szerszy zakres wartości: dla tego samego rozmiaru słowa zmiennoprzecinkowe mogą reprezentować liczby od 1.234567 do 1234567000000, podczas gdy stałoprzecinkowe są ograniczone do zakresu typu 123.45, 1234.56, 12345.67 itd.

## Spowiedź studenta

### Dlaczego nie używamy tylko systemu ZM? (GPT)

Problemy Praktyczne Systemu Znak-Moduł
Problem reprezentacji zera: System posiada dwie reprezentacje zera — +0 (00000000) i -0 (10000000). Ta redundancja zmniejsza efektywnie użyteczny zakres liczb i komplikuje logikę porównań w sprzęcie. Warunek if (x == 0) wymaga sprawdzenia dwóch bitowych konfiguracji.

Arytmetyka Addition/Subtraction: Dodawanie liczb wymaga specjalnej logiki warunkowej — jeśli znaki są identyczne, dodajemy moduły; jeśli różne, odejmujemy moduły i porównujemy ich wielkości, aby ustalić znak wyniku. Ten algorytm jest znacznie bardziej złożony niż przy kodzie uzupełnień do dwóch (U2).

Skomplikowana logika sprzętowa: Realizacja jednostki arytmetyczno-logicznej (ALU) wymaga oddzielnych ścieżek dla dodawania i odejmowania, zwiększając liczbę tranzystorów, pobór mocy i opóźnienia propagacji sygnałów.

Przewaga Kodu Uzupełnień do Dwóch
Kod U2, który dominuje w nowoczesnych komputerach, wyeliminował te problemy: posiada jednoznaczną reprezentację zera, operacje arytmetyczne (dodawanie, odejmowanie, mnożenie) działają identycznie dla liczb dodatnich i ujemnych bez logiki warunkowej, oraz wymaga znacznie prostszego sprzętu. W U2 dodawanie dwóch liczb wymaga zaledwie kaskady sumatorów binarnych — operacja może być wykonana w jednym cyklu zegara niezależnie od wartości operandów.

**Jak unika tych problemów IEEE754?**

### Jakie są inne standardy IEEE?

| Aspekt         | IEEE 754 (1985/2008)   | IEEE 854 (1987)                                 | IEEE 754-2019 |
| -------------- | ---------------------- | ----------------------------------------------- | ------------------------- |
| Radix (baza)   | Tylko 2 (binarna)      | Dopuszcza inne niż 2 np. 10                   | 2 i 10 standards.ieee​    |
| Formaty danych | Określone (32/64 bit)  | Parametryzowane, bez sztywnych sininenankka.dy​ | Binary + decimal32/64/128 |
| Precyzje       | Single/double/extended | Basic/extended (single/double)                  | Jak wyżej + extendable    |
| Zastosowanie   | Powszechne w CPU       | Rzadkie, teoretyczne myszka.kmim.pwr​           | Standard w ML/AI, finanse |

### Czym się różni U1 od U2?

Kod Uzupełnień do Jedności (U1): Liczby ujemne koduje się poprzez bitową negację (inwersję) wszystkich bitów liczby dodatniej. Dla liczby dodatniej n bitów: -x = NOT(x).

Kod Uzupełnień do Dwóch (U2): Liczby ujemne koduje się poprzez bitową negację wszystkich bitów, a następnie dodanie 1 do wyniku. Dla liczby dodatniej n bitów: -x = NOT(x) + 1

**Problemy U1 (GPT)**

Dwie Reprezentacje Zera. U1 posiada dwie różne reprezentacje zera: +0 jako 00000000 i -0 jako 11111111. Ta redundancja powoduje:
- Zmniejszenie efektywnego zakresu liczb (dla 8 bitów: [-127, +127] zamiast [-128, +127])
- Komplikację logiki porównań (if (x == 0) wymaga sprawdzenia obu reprezentacji)
- Nieefektywne wykorzystanie przestrzeni bitowej

### Jakie znasz błędy i problemy w systemach arytmetyki komputerowej zmiennoprzecinkowej i stałoprzecinkowej (GPT)

Błędy w Arytmetyce Zmiennoprzecinkowej
1. Błędy Reprezentacji i Zaokrąglenia
Fundamentalnym problemem jest fakt, że większość ułamków dziesiętnych nie może być dokładnie reprezentowana w systemie binarnym. Przykład klasyczny: 0.1 + 0.2 w wielu jezykach programowania daje wynik 0.30000000000000004, a nie oczekiwane 0.3. Dzieje się to, ponieważ zarówno 0.1 jak i 0.2 są ułamkami okresowymi w systemie binarnym i ulegają zaokrągleniu przy przechowywaniu w mantysie.

Błędy zaokrąglenia akumulują się przy długich ciągach operacji — pojedynczy błąd zaokrąglenia wynoszący około 10^(-16) dla liczb jednostkowych może prowadzić do błędu całkowitego rzędu 10^(-12) lub gorszego po wykonaniu milionów operacji.
​
2. Utrata Dokładności przy Odejmowaniu Bliskich Wartości
Odejmowanie dwóch liczb prawie równych prowadzi do katastrofalnej utraty dokładności (catastrophic cancellation). Przykład: jeśli a = 4.005 i b = 4.004 z czterocyfrową precyzją:
​
- Bezpośrednie obliczenie: (a - b) = 0.001, ale błąd względny wynosi ~25%

- Po zastosowaniu tożsamości algebraicznej (x² - y²) = (x-y)(x+y), błąd spada poniżej 0.01%

Problem wynika z faktu, że podczas wyrównywania cech przed odejmowaniem znaczące bity mogą być "przesunięte poza" mantysę, tracąc informację.

3. Overflow i Underflow
Overflow (nadmiar) występuje, gdy wynik obliczeń przekracza maksymalną reprezentowalną wartość (dla single-precision około ±3.4 × 10³⁸), co skutkuje reprezentacją infinity (±∞).

Underflow (niedozmiar) zachodzi, gdy wynik jest mniejszy niż najmniejsza reprezentowalna liczba normalna (dla single-precision około ±1.2 × 10⁻³⁸), co zazwyczaj powoduje zaokrąglenie do zera lub liczby denormalizowanej. Praktyczna konsekwencja: bardzo małe liczby mogą być mylnie obliczane jako zero.

Przykład z algebry liniowej: przy obliczaniu normy euklidesowej ||x||₂ = √(x₁² + x₂²), nawet jeśli ostateczny wynik nie powoduje overflow'u, pośrednie kwadraty mogą go spowodować, jeśli któryś z elementów jest duży.

4. Błędy NaN (Not-a-Number)
Operacje matematycznie niezdefiniowane (jak 0/0, √(-1), ∞-∞) prowadzą do specjalnej wartości NaN. Problematyczne: NaN ≠ NaN (nawet porównanie z samym sobą zwraca false), co może prowadzić do nieprzewidywalnego zachowania programów.

5. Brak Asocjatywności Operacji
Operacje zmiennoprzecinkowe nie są asocjacyjne: (a + b) + c ≠ a + (b + c) ze względu na różne błędy zaokrąglenia w każdej kolejności. Analogicznie mnożenie nie jest dystrybutywne względem dodawania.

Błędy w Arytmetyce Stałoprzecinkowej
1. Błędy Zaokrąglenia i Obcięcia
Arytmetyka stałoprzecinkowa charakteryzuje się równomiernym rozkładem błędu — maksymalny błąd zaokrąglenia wynosi zawsze ±0.5 × 2⁻ⁿ, gdzie n to liczba bitów części ułamkowej. Błąd ten jest przewidywalny i stały dla całego zakresu reprezentowalnych liczb.

Problem: jeśli precyzja wynosi 0.01 (2 miejsca dziesiętne), każda operacja może wnosić błąd aż 0.005. Po 1000 operacji błąd może skumulować się do wielkości 5.0 — w praktyce nieakceptowalny dla wielu zastosowań.
​
2. Trade-off między Zakresem a Precyzją
Arytmetyka stałoprzecinkowa wymusza sztywny kompromis: przydzielenie więcej bitów na część całkowitą zmniejsza dostępną precyzję dla części ułamkowej. Przykład:

- 32-bitowa liczba stałoprzecinkowa z podziałem 24/8: zakres [-2²³, 2²³-1], precyzja 1/256

- 32-bitowa liczba stałoprzecinkowa z podziałem 16/16: zakres [-2¹⁵, 2¹⁵-1], precyzja 1/65536

Brak elastyczności: jeśli podczas programu okaże się, że potrzebujesz większego zakresu, musisz przepisać cały kod.

3. Overflow i Underflow
Overflow w arytmetyce stałoprzecinkowej jest katastrofalny — wynik nie zmienia się płynnie na infinity, ale "owija się" modularnie (wraparound), tworząc całkowicie błędne liczby ujemne lub dodatnie. Przykład: jeśli maksimum to 2¹⁵ - 1 = 32767 (format 16-bitowy), to 32767 + 1 staje się -32768 (w U2).
​
Underflow w arytmetyce stałoprzecinkowej nie istnieje w tradycyjnym sensie — liczby poniżej precyzji są zaokrąglane do najbliższej możliwej wartości lub zera, ale nie ma specjalnej reprezentacji (w odróżnieniu od denormalizowanych liczb w zmiennoprzecinkowych).

4. Brak Naturalnego Wsparcia dla Liczb Bardzo Dużych lub Bardzo Małych
Arytmetyka stałoprzecinkowa nie radzi sobie z obliczeniami naukowych, gdzie operujesz liczbami z zakresu od 10⁻²⁰ do 10²⁰. Każdy współczynnik skalujący wymagałby ręcznej kalibracji.

| Problem                     | Arytmetyka Zmiennoprzecinkowa                     | Arytmetyka Stałoprzecinkowa                                |
| --------------------------- | ------------------------------------------------- | ---------------------------------------------------------- |
| Błąd zaokrąglenia           | Zależy od wielkości liczby (~10⁻¹⁶ dla jednostek) | Stały (~0.5 × 2⁻ⁿ), ale bezwzględnie duży dla małych liczb |
| Underflow                   | Kontrolowany (zero lub liczby denormalizowane)    | Bezgłośne (zaokrąglenie do zera)                           |
| Overflow                    | Kontrolowany (infinity)                           | Katastrofalny (wraparound modularny)                       |
| Odejmowanie bliskich liczb  | Katastrofalna utrata dokładności                  | Równomierna utrata precyzji                                |
| Aritmetyczne asocjatywności | Brak                                              | Brak (z uwagi na zaokrąglenia)                             |
| Precyzja dla małych liczb   | Doskonała (~10⁻³⁰)                                | Gorsza (zależy od podziału bitów)                          |
| Precyzja dla dużych liczb   | Gorsza (~10⁶)                                     | Identyczna jak dla małych                                  |

- Unikać odejmowania bliskich liczb poprzez algebraiczne przefaktoryzowanie wyrażeń

- Używać algorytmów numerycznie stabilnych (backward stable algorithms)

- Porządkować operacje by dodawać liczby od najmniejszej do największej

- Stosować arytmetykę wyższej precyzji (double zamiast float) dla pośrednich obliczeń

W arytmetyce stałoprzecinkowej:

- Dokładnie oszacować zakres danych przed implementacją

- Przeprowadzać operacje w szerszym formacie (np. 64-bitowe obliczenia pośrednie na 32-bitowym sprzęcie)

- Monitorować overflow jawnie poprzez testy i assertions

### Dlaczego wykładnik może być ujemny w IEEE754? (GPT)

Wykładnik, liczba pozycji określa zakres dynamiczny
Mnożnik, liczba pozycji określa dokładność

W standardzie IEEE 754 wykładnik (cecha) koduje potęgę liczby 2, przez którą mnożona jest znormalizowana mantysa. Liczba zmiennoprzecinkowa obliczana jest jako: x = (-1)^S × 1.M × 2^E, gdzie S to bit znaku, M to frakcja mantysy, a E to wartość wykładnika.

Aby reprezentować zarówno bardzo duże (2^100, 2^1000) jak i bardzo małe liczby (2^(-100), 2^(-1000)), wykładnik musi być w stanie przyjmować wartości zarówno dodatnie jak i ujemne.

Liczba 0.125 = 1/8 = 1.0 × 2^(-3):

- Bit znaku: 0 (liczba dodatnia)

- Mantysa: 1.0 (znormalizowana do [1, 2))

- Wykładnik: -3 (ujemny, bo liczba jest mniejsza niż 1)

Liczba 256 = 1.0 × 2^8:

- Bit znaku: 0

- Mantysa: 1.0

- Wykładnik: 8 (dodatni, bo liczba jest większa niż 1)

### Czym się różni quiet NaN od signaled NaN? (Wikipedia)

Quiet NaN

In general, quiet NaNs, or qNaNs, do not raise any additional exceptions, as they propagate through most operations. But the invalid-operation exception is signaled by some operations that do not return a floating-point value, such as format conversions or certain comparison operations.

Signaling NaN

Signaling NaNs, or sNaNs, are special forms of a NaN that, when consumed by most operations, should raise the invalid operation exception and then, if appropriate, be "quieted" into a qNaN that may then propagate. They were introduced in IEEE 754. There have been several ideas for how these might be used:

Filling uninitialized memory with signaling NaNs would produce the invalid operation exception if the data is used before it is initialized
Using an sNaN as a placeholder for a more complicated object, such as:
A representation of a number that has underflowed
A representation of a number that has overflowed
Number in a higher precision format
A complex number

When encountered, a trap handler could decode the sNaN and return an index to the computed result. In practice, this approach is faced with many complications. The treatment of the sign bit of NaNs for some simple operations (such as absolute value) is different from that for arithmetic operations. Traps are not required by the standard.

When an operation results in a quiet NaN, there is no indication that anything is unusual until the program checks the result and sees a NaN. That is, computation continues without any signal from the floating point unit (FPU) or library if floating-point is implemented in software. A signalling NaN will produce a signal, usually in the form of exception from the FPU. Whether the exception is thrown depends on the state of the FPU.