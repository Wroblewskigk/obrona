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

### ```Ze względu na podejście TO NIE MA SENSU?```
- Pesymistyczne - złożoność realnego problemu będzie w najgorszym przypadku zgodna z oszacowaniem
- optymistyczne - złożoność realnego problemu będzie w najlepszym przypadku zgodna z oszacowaniem
- Oczekiwane - uśrednienie podejścia optymistycznego i pesymistycznego

## Przykładowe notacje

- $O(f(n)) \implies ≤ c⋅f(n) \implies$ Algorytm wykonuje się z **maksymalnie** taką złożonością
- $Ω(f(n)) \implies ≥ c⋅f(n) \implies$ Algorytm wykonuje się z **conajmniej** taką złożonością
- $Θ(f(n)) \implies$ Algorytm wykonuje się **dokładnie** z taką złożonością

## Klasy złożoności dla notacji typu O

- $O(1)$ - Złożoność stała
- $O(log n)$ - Złożoność logarytmiczna
- $O(n)$ - Złożoność liniowa
- $O(n log n)$ - Złożoność liniowo-logarytmiczna
- $O(n^k)$ - Złożoność wielomianowa
- $O(c^n), O(n!)$ - Złożoność wykładnicza 

## Klasy problemów np 
| Klasa problemu NP | Sprawdzenie rozwiązania | Znalezienie rozwiązania |
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