# 15 Wymień składowe modelu matematycznego opisującego obraz cyfrowy wraz z krótkim ich opisem

https://www.perplexity.ai/search/opracuj-mi-nastepujace-tresci-SnQNCvnORymH4yMpNxs31Q#0

Obraz cyfrowy modeluje się za pomocą dwuwymiarowej funkcji jasności f(x,y), gdzie koordynaty przestrzenne (x,y) oraz wartość intensywności są dyskretne i skończone. Model ten integruje pięć fundamentalnych składników:


## 1. Funkcja jasności $f(x,y)$

**Definicja**: Dla każdego piksela o koordynatach $(x,y)$ przypisana jest wartość jasności:

$$f(x,y) = z, \quad \text{gdzie } z = \text{intensywność piksela}$$

Koordynaty są liczbami całkowitymi: x ∈ [0, M-1], y ∈ [0, N-1], gdzie M×N to wymiary obrazu w pikselach. Obrazy reprezentuje się macierzowo:

**Reprezentacja macierzowa**:

$$
f(x,y) = \begin{bmatrix} 
f(0,0) & f(0,1) & \cdots & f(0,N-1) \\ 
\vdots & \vdots & \ddots & \vdots \\ 
f(M-1,0) & \cdots & \cdots & f(M-1,N-1) 
\end{bmatrix}
$$

Każdy element macierzy reprezentuje jasność pojedynczego piksela w ustalonym systemie współrzędnych (górny lewy róg = (0,0)).

## 2. Próbkowanie przestrzenne - sampling

Próbkowanie to dyskretyzacja ciągłego obrazu analogowego f(x,y) w regularną siatkę punktów:

$$f_s(m\Delta x, n\Delta y), \quad m=0,1,\ldots,M-1; \quad n=0,1,\ldots,N-1$$

Parametry próbkowania:
- $\Delta x, \Delta y$ – interwały próbkowania
- $M \times N$ – liczba pikseli

Rozdzielczość przestrzenna / fundamental determinant of image quality - określana jest jako liczba pikseli na jednostkę długości (ppi, dpi). Przykład: fotografia 10×15 cm skanowana w 300 dpi daje rozmiar 2400×3000 pikseli. Wyższa rozdzielczość przestrzenna wiąże się z lepszym zachowaniem detali, lecz zwiększa rozmiar pliku.

## 3. Kwantyzacja - quantization

Kwantyzacja odwzorowuje ciągły zakres jasności na dyskretny, skończony zbiór poziomów:

$$L = 2^B$$

gdzie:

- $B$ = głębia bitowa
- $L$ = liczba poziomów kwantyzacji

Standardowe konfiguracje:

- 8-bitowa: L = 256 (poziomy 0–255) – najpowszechnie stosowana w obrazach szarości
- 4-bitowa: L = 16 tonów szarości
- 1-bitowa: L = 2 (obraz binarny)
- 24-bitowa (RGB): 8 bitów na każdy kanał (R, G, B) → 256³ ≈ 16.8 mln kolorów
​

**Rozdzielczość tonalna** (tonal resolution) – liczba różnych odcieni jasności dostępnych w obrazie – bezpośrednio zależy od głębi bitowej. Niska kwantyzacja (B < 4) prowadzi do artefaktów konturowych (false contours) – widocznych granic między obszarami o podobnej jasności.

## 4. Składowe koloru - RGB

Dla obrazów kolorowych używa się modelu RGB (Red-Green-Blue):

$$f(x,y,z) = \text{intensywność w kanale } z, \quad z \in \{R, G, B\}$$

Każdy piksel ma trzy niezależne wartości intensywności:

$$f(x,y) = [f_R(x,y), f_G(x,y), f_B(x,y)]$$

każda w zakresie 0–255 (8-bitowa).

Konwersja do skali szarości – uśrednienie ważone kanałów:

$$I_{x,y} = 0.30 \cdot R_{x,y} + 0.59 \cdot G_{x,y} + 0.11 \cdot B_{x,y}$$

Współczynniki (0.30, 0.59, 0.11) odzwierciedlają niejednorodną czułość ludzkiego oka na poszczególne kolory.

## 5. Histogram - rozkład jasności

Histogram opisuje rozkład statystyczny intensywności pikseli w obrazie:

$$h(r_k) = n_k$$

gdzie n_k = liczba pikseli o intensywności r_k

**Histogram znormalizowany** (estymator gęstości prawdopodobieństwa):

$$p(r_k) = \frac{n_k}{M \cdot N}$$

Ciekawa właściwość: 

$$\sum_{k=0}^{L-1} p(r_k) = 1$$

Histogram charakteryzuje kontrast i dynamikę obrazu – pokazuje, czy obraz jest niedoświetlony (histogram skupiony w lewej części), prześwietlony (prawa część), czy równomiernie rozłożony. Jest narzędziem diagnostycznym do oceny jakości przechwycenia i optymalizacji parametrów próbkowania/kwantyzacji.

## Tabela z podsumowaniem

| Składnik         | Matematyczna reprezentacja | Rola w modelu                                   | Jednostka/Zakres                                  |
| ---------------- | -------------------------- | ----------------------------------------------- | ------------------------------------------------- |
| Funkcja jasności | f(x,y) = z                 | Wartość intensywności każdego piksela           | z ∈ [0, L-1], zwykle                              |
| Próbkowanie      | Δx, Δy; siatka M×N         | Określa rozdzielczość przestrzenną (ile detali) | ppi, dpi; liczba pikseli                          |
| Kwantyzacja      | B bitów; L = 2^B           | Określa rozdzielczość tonalną (ile tonów)       | B ∈ {1, 4, 8, 16, 24, ...}; L ∈ {2, 16, 256, ...} |
| Składowe RGB     | f(x,y,R/G/B) ∈ ³           | Informacja kolorystyczna                        | 3 kanały × 256 poziomów każdy                     |
| Histogram        | h(r_k); p(r_k) = n_k/(MN)  | Rozkład tonalny – diagnostyka kontrastu         | liczba pikseli; prawdopodobieństwo                |

## Proces digitalizacji

Łącznie, te pięć składników w pełni opisują obraz cyfrowy: funkcja jasności zawiera informację wartościową (jaka jasność), próbkowanie narzuca sieć przestrzenną (gdzie ta jasność), kwantyzacja definiuje możliwe wartości (ile poziomów), składowe RGB dodają wymiar kolorystyczny, a histogram stanowi metadane diagnostyczne charakteryzujące rozkład tych wartości w całym obrazie.


**Proces digitalizacji** składa się z dwóch etapów:

1. **Próbkowanie przestrzenne**: Ciągły obraz $f(x,y)$ → dyskretna siatka $f_s(m\Delta x, n\Delta y)$
2. **Kwantyzacja tonalna**: Ciągłe wartości → dyskretne poziomy $f_d[m,n] \in \{0, 1, \ldots, L-1\}$

---

## Pieć składowych modelu w pełni opisujących obraz cyfrowy

| **Składnik** | **Rola** | **Informacja** |
|--------------|----------|----------------|
| **1. Funkcja jasności** | **Wartościowa** | **Jaka jasność** ma każdy piksel |
| **2. Próbkowanie** | **Strukturalna** | **Gdzie** (siatka przestrzenna) |
| **3. Kwantyzacja** | **Dyskretyzująca** | **Ile poziomów** dostępnych wartości |
| **4. Składowe RGB** | **Kolorystyczna** | **Wymiar barwny** (R,G,B) |
| **5. Histogram** | **Diagnostyczna** | **Rozkład** wartości w obrazie |

**Łącznie** te elementy definiują **kompletną strukturę obrazu cyfrowego**:
- **Przestrzenną** (gdzie piksele)
- **Tonalną** (jakie wartości) 
- **Kolorystyczną** (jakie kolory)
- **Statystyczną** (jak rozłożone)

## Czym jest pixel

Pixel (z angielskiego picture element, w skrócie px, pel) to najmniejszy adresowalny element rasterowego obrazu cyfrowego lub najmniejsza jednostka manipulowana przez oprogramowanie w urządzeniach wyświetlających. W kontekście cyfrowego przetwarzania sygnałów i obrazów stanowi on fundamentalny budulec reprezentacji cyfrowej dwuwymiarowych danych przestrzennych.