# 08 Mechanizmy systemu operacyjnego wspomagające synchronizację procesów

Synchronizacja procesów to klasyczny problem z dziedziny informatyki ustalenia kolejnoƑci dziaųania procesów ze sobČ wspóųpracujČcych. Problem synchronizacji procesów pojawia siħ wszħdzie tam, gdzie mamy do czynienia ze wspóųpracujČcymi ze sobČ wspóųbieǏnymi procesami. Celem synchronizacji jest ograniczenie swobody przeplotu tak, Ǐeby dopuszczalne staųy siħ tylko przeploty zgodne z intencjČ programisty.

## Czym jest system operacyjny?

System operacyjny stanowi oprogramowanie zarządzające sprzętem komputerowym, tworzącym środowisko uruchomieniowe i kontrolującym zadania użytkownika. Zatem jedną z podstawowych jego funkcji jest zarządzanie procesami.

## Czym jest proces?

Proces oznacza wykonujący się program. Jest podstawową jednostką pracy systemu operacyjnego. Aby mógł działać potrzebuje określonych zasobów (czas procesora, pamięci RAM itd)

## Czym jest program?

Program to zbiór instrukcji przechowywany na dysku w postaci pliku

## Problemy synchronizacji procesów

### Zagłodzenie / Starvation

Dany proces nie jest w stanie zakończyć zadania gdyż nie ma dostępu do współdzielonego zasobu. Przykład problem jedzących filozofów

### Zakleszczenie / Deadlock

Conajmniej dwa procesy czekają na siebie nawzajem i żaden z nich nie jest w stanie się z tego powodu zakończyć. Przykład problem jedzących filozofów

## Mechanizmy programowe służące do synchronizacji procesów

### Semafory

### Muteksy

### Zmienne warunkowe

### Monitory

### Sekcje krytyczne