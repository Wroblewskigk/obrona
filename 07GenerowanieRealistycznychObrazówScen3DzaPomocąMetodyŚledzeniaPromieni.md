# 07 Generowanie realistycznych obrazów scen 3-D za pomocą metody śledzenia promieni

## Czym jest metoda śledzenia promieni?

Algorytm śledzenia promieni jest algorytmem umożliwiającym tworzenie
obrazów o bardzo wysokim poziomie fotorealizmu. Swoje działanie opiera na fakcie, że światło w jednorodnym ośrodku porusza się po linii prostej. Dlatego symulując przebieg promienii od obserwatora przez rzutnię jesteśmy w stanie określić barwę jaką obserwator powinien zobaczyć.


## Jak działa  metoda śledzenia promieni?

### Opis w języku naturalnym

W klasycznym ray tracingu symulujemy zachowanie promienia Ƒwiatųa na scenie trójwymiarowej skųadajČcej siħ z
róǏnych obiektów. Istotne jest to, Ǐe Ƒledzenie zaczynamy od oka obserwatora, generujČc promieŷ skierowany w
ŐųČb sceny. _ledzimy zatem promieŷ zaczynajČc od koŷca. Z tej przyczyny moǏna siħ czasami spotkađ z nazwČ
wsteczny ray tracing. Promieŷ, który Ƒledzimy moǏe: albo trafiđ w jakiƑ obiekt na scenie, albo nie trafiđ w nic. JeǏeli
trafi w pewien obiekt, moǏemy obliczyđ kolor tego promienia, korzystajČc z modelu oƑwietlenia, np. modelu Phonga.
JeǏeli nie trafi w Ǐaden obiekt, przyjmujemy pewien ustalony kolor takiego promienia, zazwyczaj kolor tųa. Po tym jak
promieŷ uderza w powierzchniħ jakiegoƑ obiektu, moǏemy Ƒledziđ kolejne promienie: np. odbity i zaųamany.
Zazwyczaj takie Ƒledzenie zrealizowane jest w sposób rekurencyjny. Powstaje wówczas drzewo promieni, z których
kaǏdy ma wpųyw na ostateczny kolor pierwotnego promienia. Dziħki rekurencyjnemu Ƒledzeniu moǏemy uzyskađ
efekt obrazu przedmiotów, w których odbijajČ siħ inne przedmioty, albo efekt zaųamania Ƒwiatųa na granicy
ŽƑrodków.

### Opis krokowy

1. Rzutnie dzielimy na części, najczęściej taką część stanowi pojedynczy piksel obrazu
2. Dla każdej takiej części prowadzimy promień od obserwatora, przez rzutnie sprawdzając czy zaistnieje kolizja z obiektem na scenie. Jeżeli kolizji nie będzie przyjmujemy że obserwator powinien zobaczyć kolor tła
3. Jeżeli kolizja istnieje określamy barwę oświetlonego obiektu wykorzystując model oświetlenia. Następnie przekzujemy tę barwę na ekran

Taka metoda nie przewiduje jednak interakcji między poszczególnymi obiektami na scenie, a bardzo często barwa jednego obiektu potrafi rozświetlić rób zaciemnić inny obiekt. Rekurencyjny algorytm śledzenia rozwiązuje problem braku interakcji między poszczególnymi obiektami:

1. W momencie trafienia w obiekt tworzoną są promienie wtórne zgodnie z zasadami odbicia światła i prawa załamania Snella. Dla następnego trafienia w obiekt promieniem wtórnym rekurencyjnie wykonujemy ten sam program.
2. Występuje potrzeba określenia warunków wyjścia z rekurencji. Najczęściej spotykanymi są:
- W momencie nie trafienia w żaden obiekt, algorytm zwraca kolor tła, przerywając rekurencję.
- Sztywne ograniczenie głębokości rekurencji, każde kolejne odbicie wpływa coraz
mniej na ostateczny efekt, dlatego można skorzystać z tego typu ograniczenia bez
znacznej utraty realistyki

## Modele oświetlenia

### Model Phonga

Model Phonga to empiryczny model oświetlenia lokalnego punktów na powierzchni
zaprojektowany przez Bui Tuong Phonga. Model ten uwzględnia trzy rodzaje oświetlania:

- Światło otoczenia (ang. ambient) – jednorodnie oświetlające cały obiekt
- Światło rozproszone (ang. diffuse) – wpływ bezpośredniego oświetlenia
- Światło kierunkowe (ang. specular) – refleksy odbite zgodnie z prawem Snella

#### Druga definicja składowych modelu Phonga

- Światło otoczenia – Stałe światło, które dodajemy do każdego miejsca przecięcia,
pozwala w sposób wystarczający ukryć niedoskonałości metody w renderowaniu scen
oświetlonych światłem dziennym.
- Światło rozproszone – Najważniejszy rodzaj światła, który wywodzi się z faktu
chropowatości otaczających nas przedmiotów, światło padające na obiekt jest
rozpraszane ( tzn odbijane w różnych kierunkach ) Im mniejszy jest kąt jaki tworzy
normalna płaszczyzny i padające światła tym mniej światła jest rozproszone. Nasze oko
wykorzystuje takie informacje do oszacowania kształtu obiektów.
- Światło odbite – Światło tworzące połysk, pozwala ono na symulowanie materiałów
gładkich na tyle by zachować się jak lustro. Które nie rozprasza światła a je odbija.
Najczęściej tworzy małe jasne punkciki na obiektach
- Dodatkowym efektem używanym w modelu Phonga jest zjawisko tłumienia
atmosferycznego. Zakłada ono, że im obserwator jest dalej od obiektu, tym mniej
odbitego światła zdoła do niego dotrzeć. Odpowiednie wykorzystanie tego zjawiska
pozwala na bardzo realistyczną symulacje różnych stanów pogody takich jak deszcz,
mgła.

### Inne modele oświetlenia

https://fizyka.umk.pl/~jacek/dydaktyka/3d/grafika3d_animacja/2013L_OpenGLES_PhysX/referaty/2013-06-10_MMoczadlo_ModeleOswietleniaWGrafice3D.pdf

## Zalety metody śledzenia promieni

Uzyskanie obrazów fotorealistycznych. Fotorealistycznych w znaczeniu wyglądających jak stworzonych za pomocą fizycznej kamery, pomimo wykorzystania grafiki komputerowej 

## Wady metody śledzenia promieni

Ray tracing charakteryzuje siħ wysokim kosztem obliczeniowym. Dla kaǏdego piksela wynikowego obrazu naleǏy
przeprowadziđ caųČ procedurħ Ƒledzenia promieni. Dla kaǏdego promienia trzeba sprawdziđ, czy przecina on jakieƑ
obiekty na scenie, a jeƑli przecina, to wyznaczyđ taki punkt przeciħcia, który jest najbliǏszy poczČtkowi promienia. Z
drugiej strony, natura ray tracingu umoǏliwia przeprowadzanie równolegųych obliczeŷ dla kaǏdego piksela obrazu, a
nawet dla kaǏdego promienia. Ta cecha pozwala na przyspieszenie obliczeŷ.

# Co ma zostać wymienione
- Czym jest ray tracing
- Algorytm ray tracing'u
- Wady i zalety ray tracing'u

# Czym jest piksel?