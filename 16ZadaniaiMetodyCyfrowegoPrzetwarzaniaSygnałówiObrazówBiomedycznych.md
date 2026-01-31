# 16 Zadania i metody cyfrowego przetwarzania sygnałów i obrazów biomedycznych

Cyfrowe przetwarzanie sygnałów i obrazów biomedycznych stanowi fundamentalną dziedzinę informatyki biomedycznej, której głównym celem jest wydobywanie diagnostycznie cennych informacji z danych pochodzących z urządzeń medycznych. Opracowanie to szczegółowo omawia trzy kluczowe zadania: filtrację, segmentację oraz ekstrakcję cech, wraz z praktycznym uzasadnieniem ich zastosowań w medycynie.

## Filtracja

Filtracja cyfrowa jest operacją matematyczną na pikselach obrazu źródłowego, której celem jest **wydobycie z oryginalnego obrazu szeregu informacji ułatwiającej dalszą obróbkę**. Procedurę tę można opisać jako przekształcenie kontekstowe, ponieważ do wyznaczenia nowej wartości piksela obrazu docelowego potrzebna jest informacja z wielu sąsiednich pikseli obrazu źródłowego.

Zastosowania praktyczne:

- Usuwanie szumów (filtr medianowy, uśredniające)
- Redukcja szumu termicznego z czujników (ramka bazowa)
- Rozmycie obrazu i ulepszanie kontrastu
- Wykrywanie krawędzi obiektów
- Nieostre maskowanie (unsharp masking) – eliminacja składowych niskopasmowych

## Segmentacja

Głównym celem segmentacji jest przejście z poziomu pikseli na poziom obiektów – **wydzielenie interesujących nas obszarów** (Region of Interest, ROI) od tła. Dla obrazów medycznych oznacza to typowo izolację patologicznych struktur (guza, lezji) od tkanki zdrowej, lub wydzielenie poszczególnych organów/struktur anatomicznych.
​
Bez precyzyjnej segmentacji niemożliwa jest:

- Dokładna ocena rozmiaru i kształtu guza
- Planowanie chirurgii (określenie granic obszaru do resekcji)
- Automatyczne pomiary (objętość, średnica)
- Ekstrakcja cech radiomicznych dla predykcji wyników leczenia

## Ekstrakcja cech

Po segmentacji fragmentu zainteresowania (np. guza), niezbędne jest **wyodrębnienie z tego regionu parametrów numerycznych, które będą służyć do diagnozowania lub predykcji wyników.** Jako przykład: z wydzielonego guza mózgu można wyekstrahować około 30-400 cech radiomicznych, obejmujących cechy morfologiczne (kształt, wymiary) i cechy teksturalne (rozkład intensywności, wzorce).
​
## Przetwarzanie sygnałów: EKG, ELG, MRI, CT

| Sygnał | Zakres częstotliwości | Amplituda | Preprocessing                                    | Ekstrakcja cech                    |
| ------ | --------------------- | --------- | ------------------------------------------------ | ---------------------------------- |
| EKG    | 0.15-150 Hz           | 5-10 mV   | Filtracja 50 Hz, normalizacja                    | Fale P, QRS, T; RR intervals       |
| EEG    | 0.2-100 Hz            | 600 μV    | Filtracja pasmowa (pasma delta-gamma), artefakty | Moc spektralna, falkowa, entropija |
| EMG    | 10-8000 Hz            | 0.1-1 mV  | Rektyfikacja, filtracja                          | RMS, cechy falkowe                 |

## Czym jest pixel

Pixel (z angielskiego picture element, w skrócie px, pel) to najmniejszy adresowalny element rasterowego obrazu cyfrowego lub najmniejsza jednostka manipulowana przez oprogramowanie w urządzeniach wyświetlających. W kontekście cyfrowego przetwarzania sygnałów i obrazów stanowi on fundamentalny budulec reprezentacji cyfrowej dwuwymiarowych danych przestrzennych.