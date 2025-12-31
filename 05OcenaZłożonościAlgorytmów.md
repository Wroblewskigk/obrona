# 05 Ocena złożoności algorytmów

## Podstawowe definicje

### Problem obliczeniowy
Zadanie do wykonania wraz z danymi wejściowymi oraz warunkami jakie ma spełnić wynik.

### Instancja problemu
Problem obliczeniowy z konkretnymi danymi. **Należy pamiętać, że instancja problemu to nie problem**

Na przykład, sortowanie tablicy to problem, gdzie konkretne liczby np. 7, 3, 5, 0 to instancja problemu, a posortowana sekwencja to rozwiązanie


### Algorytm
Algorytm to skończony zbiór jasno zdefiniowanych, logicznych kroków i instrukcji, które krok po kroku prowadzą do rozwiązania konkretnego problemu lub wykonania określonego zadania, przekształcając dane wejściowe w pożądane dane wyjściowe w **skończonym** czasie

# PONIŻEJ NIESPRAWDZONE

### Złożoność obliczeniowa 
Ilość zasobów potrzebnych do rozwiązania problemu.

## Typy złożoności obliczeniowej

### Ze względu na zasoby
- Złożoność czasowa - w jakim tępie rośnie ilość czasu potrzebna do wykonania algorytmu, w zależności od rozmiaru problemu.
- Złożoność pamięciowa w jakim tępie rośnie ilość pamięci potrzebna przechowania wszystkich struktur danych wymaganaych przez algorytm, w zależności od rozmiaru problemu.

### Ze względu na podejście
- Pesymistyczne - złożoność realnego problemu będzie w najgorszym przypadku zgodna z oszacowaniem
- optymistyczne - złożoność realnego problemu będzie w najlepszym przypadku zgodna z oszacowaniem
- Oczekiwane - uśrednienie podejścia optymistycznego i pesymistycznego

## Przykładowe notacje

- Notacja O - notacja pesymistyczna Dla funkcji pomnożonej przez pewną stałą musi być od pewnego rozmiaru problemu zawsze niemniejsza od złożoności algorytmu
- Notacja $\mathsf{\Omega}$ - notacja optymistyczna. Dla funkcji pomnożonej przez pewną stałą musi być od pewnego rozmiaru problemu zawsze niewiększa od złożoności algorytmu
- Notacja $\mathsf{\Theta}$ - notacja uśredniona.  

## Klasy złożoności dla notacji typu O

- $O(1)$ - złożoność stała
- $O(log n)$ - złożoność logarytmiczna
- $O(n)$ - złożoność liniowa
- $O(n log n)$ - złożoność liniowo - logarytmiczna
- $O(n^k)$ - złożoność wielomianowa
- $O(c^n), O(n!)$ - złożoność wykładnicza 

Ważne zapamiętania: złożoność czasowa nie zawsze wskazuje że problem wykonuje się szybciej. Jeżeli jakiś algorytm wykonuje się zawsze w 10 min to może być wolny od algorytmu o złożoności liniowej jeżeli wykonuje się w ciągu sekundy.

## Klasy problemów np 
| Klasa problemu NP | Sprawdzenie rozwiązania | Znalezienie rozwiązania |
| - | - | - |
| Problem P | Złożoność wielomianowa: $P = O(n^x)$ | Złożoność wielomianowa: $NP = O(n^x)$ | Problem NP | Złożoność wielomianowa: $P = O(n^x)$ |Złożoność wielomianowa $NP = O(n^x)$ lub wykładnicza EXPTIME = O(X^n) |
| Problem NP‑zupełny | Złożoność wielomianowa $P = O(n^x)$ | Złożoność wykładnicza: $NEXPTIME = O(X^n)$ |
| Problem NP‑trudny  | Złożoność wielomianowa $P = O(n^x)$ lub wykładnicza $EXPTIME = O(X^n)$ | Złożoność wykładnicza: $NEXPTIME = O(X^n)​$ |


# Streszczenie
- Czym jest złożoność obliczeniowa
- Typy złożoności obliczeniowej 
- Przykładowe notacje
- Jakiekolwiek klasy złożoności 