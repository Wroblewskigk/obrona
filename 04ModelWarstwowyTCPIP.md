# 04 Model warstwowy TCP/IP

## Warstwy modelu TCP/IP

### Warstwa aplikacji

Warstwa aplikacji udostępnia użytkownikom możliwość korzystania z usług sieciowych, takich jak WWW, poczta elektroniczna, wymiana plików, połączenia terminalowe czy komunikatory. Swoim uczniom mówię zawsze, że jest to warstwa najbliższa użytkownikowi, ponieważ to właśnie ona pozwala nam w pełni korzystać z dobrodziejstw współczesnych usług sieciowych. Kiedy siadamy przed komputerem i uruchamiamy np. przeglądarkę internetową to korzystamy z sieci właśnie na poziomie warstwy aplikacji.

Przykładowe protokoły:

- HTTP (strony WWW)
- DNS (tłumaczenie nazw domenowych)
- SMTP (wymiana poczty)
- SSH (zdalna praca konsolowa)

### Warstwa transportowa

Niżej mamy warstwę transportu, której głównym zadaniem jest sprawna obsługa komunikacji pomiędzy urządzeniami. W warstwie tej dane dzielone są na mniejsze części, następnie opatrywane są dodatkowymi informacjami pozwalającymi zarówno przydzielić je do właściwej aplikacji na urządzeniu docelowym, jak i pozwalającymi złożyć je na urządzeniu docelowym w odpowiedniej kolejności.

Przykładowe protokoły:

- TCP (połączeniowy, gwarantujący niezawodność transmisji)
  - https://pasja-informatyki.pl/sieci-komputerowe/naglowek-tcp/
- UDP (bezpołączeniowy, szybszy, ale nie gwarantujący poprawności transmisji)
  - https://pasja-informatyki.pl/sieci-komputerowe/protokol-udp/

### Warstwa internetu

Dalej jest warstwa internetowa, której głównym zadaniem jest odnalezienie najkrótszej i najszybszej drogi do urządzenia docelowego przez sieć rozległą, podobnie jak robią to samochodowe GPS’y, ale także adresowanie danych z wykorzystaniem adresów logicznych (adresów IP).

Przykładowe protokoły:

- IP wybiera najlepszą drogę transportu pakietów
- ICMP używany przez polecenia w konsoli sprawdzające jakość połączenia

### Warstwa dostępu do sieci

No i na koniec mamy warstwę dostępu do sieci, która koduje dane do postaci czystych bitów (zer i jedynek) i przekazuje je do medium transmisyjnego i także je adresuje, tym razem poprzez adresy fizyczne (adresy MAC).

Przykładowe protokoły:

- Ethernet / WIFI
- MAC - adres fizyczny urządzenia

### Podsumowanie

Każda z warstw jest niezależna od pozostałych. Przykładowo, na poziomie warstwy aplikacji po drugiej stronie łącza widoczna jest bezpośrednio aplikacja, z którą zostało nawiązane połączenie, niezależnie od trasy pokonywanej przez pakiety w warstwie internetowej. Z kolei z perspektywy warstwy internetowej po przeciwnej stronie łącza znajduje się następne urządzenie na trasie posiadające adres IP, niezależnie od fizycznej struktury sieci i przykładowo liczby przełączników, jakie musi pokonać ramka przenosząca pakiet IP. Dzięki temu można łatwo wykorzystać w sieci różne technologie i z punktu widzenia wyższych warstw nie ma na przykład znaczenia, czy fizycznie transmisja odbywa się kablem w standardzie Ethernet, czy bezprzewodowo w jednym ze standardów Wi-Fi – dowolny rodzaj danych da się przesłać dowolnym łączem.

## Warstwy modelu ISO/OSI

### Warstwa aplikacji

Na samej górze tego modelu wyróżnić możemy warstwę aplikacji i tutaj tak naprawdę jej funkcję są bardzo podobne do tych z modelu TCP/IP, no bo pozwalają użytkownikom końcowym sieci korzystać z aplikacji sieciowych.

### Warstwa prezentacji

Dalej mamy warstwę prezentacji, która to przekazuje do warstwy aplikacji informacje o zastosowanym formacie danych, np. informuje jakie typy plików będą przesyłane, odpowiada ona również za odpowiednie zakodowanie danych na urządzeniu źródłowym i ich dekodowanie na urządzeniu docelowym.

### Warstwa sesji

Niżej jest warstwa sesji, zarządzająca sesjami użytkowników korzystających np. ze stron WWW czy komunikacji video.

### Warstwa transportowa

Idąc dalej mamy warstwę transportu, czyli ponownie dokładnie to samo co w modelu TCP/IP, zarówno w jednym jak i w drugim przypadku funkcje tej warstwy są dokładnie takie same.

### Warstwa Sieci

Następnie mamy warstwę sieci, która jest odpowiednikiem warstwy internetowej modelu TCP/IP czyli znowu bardzo podobne funkcje, takie jak adresowanie i wyznaczanie najlepszej ścieżki przesyłu danych.

### Warstwa łącza danych

Dalej idąc w dół mamy warstwę łącza danych, której głównym zadaniem jest kontrola dostępu do medium transmisyjnego, a także adresowanie danych, tym razem jednak w celu przesyłania ich pomiędzy hostami w sieci LAN.

### Warstwa fizyczna

No i na koniec warstwa fizyczna, która koduje dane do postaci czystych bitów (zer i jedynek) i przesyła je poprzez medium transmisyjne do odpowiednich urządzeń.

## Zadania poszczególnych warstw TCP/IP i ISO/OSI

### Warstwa aplikacji

Czas teraz na bardziej szczegółowe przedstawienie procesu komunikacji z wykorzystaniem warstw. Omówimy go sobie na przykładzie wysyłania wiadomości e-mail. Na początku, użytkownik sieci, korzystając z programu pocztowego lub przeglądarki internetowej tworzy wiadomość e-mail. Warstwa aplikacji w odpowiedni sposób koduje te dane i przekazuje do warstwy transportu.

- Utworzenie wiadomości
- Zakodowanie danych
- Przekaznie danych do warstwy transportowej

### Warstwa transportowa

W tej warstwie następuje podział danych na mniejsze część, czyli segmenty, które to łatwiej jest przesłać przez sieć. To tak jakbyśmy chcieli przenieść z miejsca na miejsce ogromny narożnik, trudno byłoby go przenieść w całości, skoro nawet nie mieści się w drzwiach, dlatego też rozłożylibyśmy go na części a nie kombinowali z przeniesieniem go w całości. W tej warstwie również dodawane są informacje sterujące pozwalające później, na urządzeniu końcowym złożyć segmenty w odpowiedniej kolejności (chociaż nie są one dodawane zawsze, zależy to od zastosowanego protokołu tej warstwy), ale przede wszystkim dodawane są też numery portów aplikacji (port aplikacji na serwerze pocztowym oraz port na kliencie), czyli informacje pozwalająca potem stwierdzić, że jest to wiadomość e-mail, a nie np. strona WWW. O portach aplikacji opowiemy więcej kiedy to omawiać będziemy funkcje i protokoły warstwy aplikacji i transportu.

- Podział danych na segmenty i datagramy
- Opcjonalne dodanie informacji o klejności segmentów
- Dodanie do segmentów numeru portów aplikacji

### Warstwa internetu

Dalej segmenty przekazywane są do warstwy internetowej, gdzie nadawane są adresy IP - zarówno urządzenia, które dane wysyła, jak również tego, który jest ich adresatem. Zabieg ten stosowany jest po to aby rutery, czyli urządzenia pośredniczące na drodze między nadawcą a odbiorcą wiadomości, wiedziały gdzie mają ją przesłać. Od tego momentu nasze segmenty są już zaadresowanymi pakietami.

- Nadanie pakietom adresów IP
- Przekazanie pakietów do warstwy dostępu do sieci

### Warstwa dostępu do sieci

Następnie pakiety trafiają do warstwy dostępu do sieci, gdzie tworzone są ramki, opatrywane adresem fizycznym urządzenia wysyłającego wiadomość oraz adresem fizycznym rutera, do którego podłączony jest komputer, z którego wysyłamy wiadomość. Dzięki temu adresowi, ramki potem mogą trafić do tego rutera, który to dalej wyśle je do sieci rozległej.

- Utworzenie ramek
- Nadanie ramkom adresów fizycznych
- Zakodowanie ramek i przekazanie do medium transmisyjnego

## Jakie urządzenia operują na jakich warstwach

Urządzenia sieciowe działają głównie w dolnych warstwach modeli TCP/IP i ISO/OSI, gdzie realizowana jest transmisja danych. Górne warstwy skupiają się na oprogramowaniu, bez dedykowanego sprzętu sieciowego. Poniżej przedstawiono kluczowe urządzenia dla każdej warstwy, z mapowaniem między modelami.
​

### Model TCP/IP

Warstwa aplikacji: Brak typowych urządzeń sieciowych; obsługiwane przez oprogramowanie na hostach

Warstwa transportowa: Bramy, firewalle – kontrolują komunikację end-to-end

Warstwa internetu: Routery, przełączniki warstwy internetu

Warstwa dostępu do sieci: Huby, repeatery, kable, modemy (warstwa fizyczna); mosty, switche, karty sieciowe (warstwa łącza danych).
​

### Model ISO/OSI

Warstwa aplikacji: Brak urządzeń sieciowych; aplikacje użytkownika.

Warstwa prezentacji: Brak urządzeń; konwersja formatów danych.

Warstwa sesji: Brak urządzeń; zarządzanie sesjami.

Warstwa transportowa: Bramy, firewalle.

Warstwa sieciowa: Routery.

Warstwa łącza danych: Switche, mosty, karty sieciowe (adresy MAC).

Warstwa fizyczna: Huby, repeatery, modemy, kable

## Porównanie odpowiedzialnośći warstw TCP/IP i ISO/OSI

| Warstwa|Warstwa OSI (7-warstwowy model) | Warstwa TCP/IP (4-warstwowy model) |
| - |----------------------------- | ---------------------------------- |
| 7 | Aplikacji                    | Aplikacji                          |
| 6 | Prezentacji                  | Aplikacji                          |
| 5 | Sesji                        | Aplikacji                          |
| 4 | Transportowa                 | Transportowa                       |
| 3 | Sieci                        | Sieci                              |
| 2 | Łącza danych                 | Dostępu do sieci                   |
| 1 | Fizyczna                     | Dostępu do sieci                   |

# Co ma zostać wymienione
- Co to jest TCP/IP
- Wymienić warstwy TCP/IP
- Wymienić jakie urządzenia operują na każdej z warstw
- Porównanie TCP/IP i ISO/OSI
- Porównanie TCP i UDP