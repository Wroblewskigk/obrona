# 05 Ocena złożoności algorytmów

## Podstawowe definicje

### Problem obliczeniowy
Zadanie do wykonania wraz z danymi wejściowymi oraz warunkami jakie ma spełnić wynik.

### Instancja problemu
Problem obliczeniowy z konkretnymi danymi. **Należy pamiętać, że instancja problemu to nie problem**

Na przykład, sortowanie tablicy to problem, gdzie konkretne liczby np. 7, 3, 5, 0 to instancja problemu, a posortowana sekwencja to rozwiązanie

### Algorytm
Algorytm to skończony zbiór jasno zdefiniowanych, logicznych kroków i instrukcji, które krok po kroku prowadzą do rozwiązania konkretnego problemu lub wykonania określonego zadania, przekształcając dane wejściowe w pożądane dane wyjściowe w **skończonym** czasie

### Złożoność obliczeniowa 
Złożoność obliczeniowa to miara zasobów czasu i pamięci potrzebnych algorytmowi do rozwiązania **instancji?** problemu, zależna od rozmiaru danych wejściowych $n$ i wyrażana w notacji Wielkiego $O$ np. $O(n)$, określająca, jak efektywnie algorytm skaluje się wraz ze wzrostem ilości danych wejściowych.

## Typy złożoności obliczeniowej

### Ze względu na zasoby
- Złożoność czasowa: w jakim tępie rośnie ilość czasu potrzebna do wykonania algorytmu, w zależności od rozmiaru instancji problemu.
- Złożoność pamięciowa w jakim tępie rośnie ilość pamięci potrzebnej do przechowania wszystkich struktur danych wymaganaych przez algorytm, w zależności od rozmiaru instancji problemu.

### Ze względu na podejście
- Pesymistyczna -  jest to najgorszy możliwy przypadek danych wejściowych, gdzie algorytm wykonuje się najdłużej, posiada najwięcej operacji dominujących, zabiera najwięcej pamięci, wykorzystuje najwięcej wątków i tym podobne
- Optymistyczna - przypadek, gdzie dane są tak dobrane, że występuje najmniejsza ilość operacji dominujących i podobnych
- Przeciętna / Oczekiwana / Średnia - wartość oczekiwana zasobów wykorzystywanych przez program w zwykłym przypadku.

## Przykładowe notacje
- $o(f(n)) \implies < c⋅f(n)$
- $O(f(n)) \implies ≤ c⋅f(n) \implies$ Algorytm wykonuje się z **maksymalnie** taką złożonością
- $ω(f(n)) \implies > c⋅f(n)$
- $Ω(f(n)) \implies ≥ c⋅f(n) \implies$ Algorytm wykonuje się z **conajmniej** taką złożonością
- $Θ(f(n)) \implies$ Algorytm wykonuje się **dokładnie** z taką złożonością

## Klasy złożoności dla notacji typu O

- $O(1)$ - Złożoność stała
- $O(log n)$ - Złożoność logarytmiczna
- $O(n)$ - Złożoność liniowa
- $O(n log n)$ - Złożoność liniowo-logarytmiczna
- $O(n^k)$ - Złożoność wielomianowa
- $O(c^n)$ - Złożoność wykładnicza 
- $O(n!)$ - Złożoność rzędu n-silnia 

## Klasy problemów np 
| Klasa problemu | Sprawdzenie rozwiązania | Znalezienie rozwiązania |
| - | - | - |
| Problem P | Złożoność wielomianowa: $O(n^x)$ | Złożoność wielomianowa: $O(n^x)$ | 
Problem NP | Złożoność wielomianowa: $O(n^x)$ | Nie obalono i nie odkryto złożonośći wielomianowej $O(n^x)$. Istnieją rozwiązania wykładnicze $O(X^n)$ |
| Problem NP‑zupełny | Złożoność wielomianowa $O(n^x)$ | Złożoność wykładnicza: $O(X^n)$ |
| Problem NP‑trudny  | Złożoność wielomianowa $O(n^x)$ lub wykładnicza $O(X^n)$ | Złożoność wykładnicza: $O(X^n)​$ |

# Co ma zostać wymienione
- Czym jest złożoność obliczeniowa
- Typy złożoności obliczeniowej 
- Przykładowe notacje
- Klasy złożoności 