## Model architekturalny komputera wg. von Neumanna a model obliczeniowy komputera na podstawie maszyny Turinga i ich rola w informatyce.

### von Neumann
Model architekturalny komputera wg. von Neumanna opiera się na idei, że komputer składa się z czterech głównych elementów:
- Pamięci komputera – zawiera dane programu i jego instrukcje (wspólna pamięć na obie te rzeczy)
- Jednostki sterującej – pobiera dane i instrukcje z pamięci i dba o ich sekwencyjne przetwarzanie
- Jednostki arytmetyczno/logicznej – wykonuje podstawowe operacje arytmetyczne
- Urządzeń wejścia/wyjścia – służą do interakcji z operatorem

**Model ten jest uważany za jeden z pierwszych formalnych modeli komputera**.

- Obliczenia są wykonywane na danych zapisanych w pamięci i rejestrach komputera
- Kolejność wykonywania instrukcji jest ustalona przez programistę:
	- Poprzez kolejność ich zapisu
	- Poprzez instrukcję przemieszczenia (zmiany) sterowania: skok (go to), wywołanie podprogramu (np. wywołanie funkcji), powrót z podprogramu (return) itp.
- Kolejność instrukcji jest wyznaczana przez **licznik rozkazów (program counter)** – zawiera on adres następnej instrukcji w pamięci po aktualnie wykonywanej
- Jeśli aktualna instrukcja nie zawiera rozkazu zmiany sterowania, to ustawia ona nową zawartość licznika rozkazów – podaje nowy adres następnej instrukcji do wykonania
- Korzysta z **języków imperatywnych** ­– takich języków programowania, w których programista określa bezpośrednio (explicite) i dokładnie jakie obliczenia mają się wykonać i dokładnie w jakiej kolejności

> [!info] Model obliczeniowy
>  określa w jaki sposób będą programowane i wykonywane obliczenia w programie. Składa się z modelu architekturalnego systemu i języka programowania

Model obliczeniowy komputera na podstawie maszyny Turinga został zaproponowany przez Alana Turinga. Jest pierwszym, uniwersalnym modelem obliczeniowym. Opiera się na idei, że komputer jest maszyną, która jest w stanie wykonywać obliczenia na podstawie serii instrukcji i danych wejściowych. 
- Służy porównywaniu własności różnych algorytmów i programów pochodzących z różnych komputerów
- Składa się z następujących elementów:
	- Skończony alfabet symboli: a,b,c,…,m
	- Skończony zbiór stanów: S0,S1,S2,…,Sk
	- Nieskończona taśma z polami na zapis symboli
	- Głowica czytająco/pisząca na taśmie, która może przesuwać się o jedno pole w zadanym kierunku
	- Diagram przejść między stanami – tablica przejść określająca następny stan, zapis symbolu pod głowicą i kierunek następnego ruchu
- Działanie mechanizmu sterowania:
	- Maszyna w stanie „i” czyta znak „z” pod głowicą
	- Dla stanu „i” oraz znaku „z” maszyna określa z tabeli przejść:
		- Stan, do którego ma przejść
		- Znak, który ma być wpisany w polu pod głowicą
		- Kierunek ruchu głowicy o 1 miejsce L – w lewo, R – w prawo
	- Głowica wpisuje nowy znak i przesuwa się w zadanym kierunku

Obydwa te modele odgrywają kluczową rolę w informatyce, ponieważ stanowią podstawy dla projektowania i budowy komputerów. Model architekturalny komputera wg. von Neumanna umożliwia projektowanie i budowę komputerów, które są w stanie przetwarzać dane i instrukcje, natomiast model obliczeniowy komputera na podstawie maszyny Turinga jest niezbędny do rozwoju teorii algorytmów.
## Logika boolowska i jej zastosowania w warstwie sprzętowej komputerów.

Logika boolowska jest dziedziną matematyki i teorii informacji, która opiera się na dwóch stanach logicznych: "prawda" i "fałsz". W logice boolowskiej operacje logiczne (takie jak "i", "lub" i "negacja") są wykonywane na tych dwóch stanach.

W warstwie sprzętowej komputerów, logika boolowska jest używana do implementacji układów logicznych, takich jak bramki AND, OR i NOT. Bramki te są elementami składowymi procesora i są wykorzystywane do wykonywania obliczeń bit po bicie. Logika boolowska jest również używana do projektowania i implementacji układów scalonych, takich jak pamięci i układy wejścia-wyjścia.

Ogólnie rzecz biorąc, logika boolowska jest niezbędna do projektowania i budowy komputerów na poziomie sprzętowym, ponieważ pozwala na realizację prostych i skutecznych obliczeń logicznych, które są niezbędne dla funkcjonowania komputera.
## Zapis binarny liczb całkowitych, zapis zmiennoprzecinkowy liczb rzeczywistych, arytmetyka komputerowa. 

### Liczby całkowite
Zapis binarny liczb całkowitych to sposób zapisywania liczb całkowitych (czyli bez ułamków) przy użyciu tylko dwóch cyfr binarnych: 0 i 1. Każdą liczbę naturalną da się przedstawić w systemie binarnym i  ma dokładnie jedną reprezentację. 

Przypisujemy kolejnym pozycjom od prawej do lewej kolejne potęgi dwójki: …256, 128 ,64, 32, 16, 8, 4, 2, 1.
### Liczby rzeczywiste
1. Nie występuje ciągłość liczb – nie każda liczba rzeczywista ma swoją (dokładną) reprezentację 
2. Obliczenia nie są dokładne – zawsze występuje błąd przybliżenia. Po kilku tysiącach/milionach takich działań błąd obliczeń może urosnąć do nieakceptowalnych rozmiarów.
3. Szybkie algorytmy, które wykonują niewiele działań mają mniejsze prawdopodobieństwo popełnienia błędu podczas obliczeń.
4. Zauważone przez Carla Gaussa – zwiększanie dokładności nie zawsze prowadzi do polepszenia wyniku końcowego. Istnieje pewna wartość graniczna $\Delta x$ po przekroczeniu, której dokładność obliczeń znowu maleje – spowodowane jest to przez błąd przybliżeń.

#### Format stałoprzecinkowy

Mamy jeden bit na znak, pozostałe na liczby. Bity na liczby podzielone są na **część całkowitą** i **część ułamkową**. Miejsce przecinka binarnego jest umowne (nie ma na nie odrębnego bitu).  
- część całkowita – potęgi liczby 2 rosnące w lewą stronę od przecinka  
- część ułamkowa – ujemne potęgi liczby 2 (1/2, 1/4, 1/8…) malejące w prawą stronę od przecinka  
- przecinek bitowy – między bitami oznaczającymi 1 oraz 0,5  

Ułamki możemy reprezentować jedynie z pewną dokładnością, zależną od ilości wykorzystanych bitów  

#### Format zmiennoprzecinkowy

liczba jest przedstawiana w postaci iloczynu:  
$$A=m*p^C$$  
- A – dana liczba,
- m – **mantysa** liczby A,
- p – **podstawa** używanego systemu (w systemie binarnym to jest 2),
- C – **cecha (wykładnik)** użytej potęgi podstawy  
Cecha i mantysa są przedstawiane osobno w postaci dwóch stałoprzecinkowych liczb binarnych w zadanym zapisie binarnym.

Mantysa ma znak i przecinek, może być dodatnia/ujemna oraz całkowita/ułamkowa/mieszana  

Cecha jest zawsze całkowita, ale też ma znak i może być dodatnia/ujemna. Cecha pełni rolę skali liczbowej (ona przemieszcza przecinek) z formatu stałoprzecinkowego  
np. dla 3-bitowej cechy (zakres cech to <-4,3>, bo w tym przykładzie jest zapis uzupełnienia do 2) i 4-bitowej mantysy:  

| Cecha | Mantysa | Liczba |
| :--: | ---- | ---- |
| 000 | 0100 | $1\over2$ |
| 000 | 0101 | $5\over_{8}$ |
| 010 | 0100 | $2 \frac{1}{2}$ |
### Liczby ujemne 
Są 3 systemy kodowania liczb ujemnych: 
1. Kod znak–moduł prosty
2. Kod znak–moduł odwrotny (uzupełnieniowy do 1)
3. Kod uzupełnieniowy (do dwóch)

#### KOD ZNAK–MODUŁ PROSTY
Wszystkie bity poza najstarszym mają takie samo znaczenie jak w naturalnym kodzie binarnym. Wyróżniony bit w tym zapisie jest bitem znaku. Jeżeli ma on wartość 0 to dana liczba jest nieujemna, jeżeli 1, to liczba jest niedodatnia.

>[!warning] Podane kodowanie prowadzi do dość dziwnej sytuacji, że zero reprezentujemy na 2 sposoby: nieujemne zero (0000) i niedodatnie zero (1000).

### KOD ZNAK–MODUŁ ODWROTNY 
Liczby dodatnie zapisywane są jak w naturalnym kodzie binarnym, dla liczb ujemnych wszystkie wartości są zamieniane na przeciwne.

| Znak moduł odwrotny | Reprezentacja dziesiętna | Znak moduł odwrotny | Reprezentacja dziesiętna |
| :--: | ---- | ---- | ---- |
| 0111 | 7 | 1000 | -7 |
| 0110 | 6 | 1001 | -6 |
| 0000 | 0 | 1111 | -0 |

>[!warning] W tym kodowaniu również występują dwie reprezentacje 0.

### KOD UZUPEŁNIENIOWY
Dla przypadku liczb 4 bitowych patrząc od prawej bity mają wartości $−8, 4, 2, 1$. Z trzech młodszych bitów generujemy wszystkie wartości od 0 do 7, a jeśli włączymy bit −8, to dodanie do niego tych wartości da nam liczby od −8 do −1. W kodzie uzupełnieniowym na n bitach da się zapisać liczby z zakresu: $−2 ^{𝑛−1}$ , $2 ^{𝑛−1} – 1$

| Kod uzupełnieniowy | Reprezentacja dziesiętna |
| :--: | ---- |
| 0111 | 7 |
| 0110 | 6 |
| 1010 | -6 |
| 1001 | -7 |
| 1000 | -8 |

Zapis zmiennoprzecinkowy liczb rzeczywistych to sposób zapisywania liczb rzeczywistych (czyli z ułamkami) w komputerach. W tym zapisie liczba jest dzielona na część całkowitą i ułamkową, a każda z tych części jest zapisywana za pomocą zapisu binarnego.
Arytmetyka komputerowa to dziedzina informatyki, która zajmuje się realizacją obliczeń matematycznych na komputerach. W arytmetyce komputerowej omawia się m.in. sposoby obliczania wartości funkcji, rozwiązywania równań, a także przeprowadzania obliczeń zmiennoprzecinkowych i liczb całkowitych. Celem arytmetyki komputerowej jest zapewnienie dokładności i wydajności obliczeń matematycznych w komputerach.

## Miary efektywności obliczeniowej procesorów, pojemności pamięci komputerowej oraz wydajności systemów obliczeniowych.

O efektywności działania systemu komputerowego decydują zarówno elementy odpowiedzialne ze szybką realizację obliczeń numerycznych (zegar procesora, wielkość i organizacja pamięci notatnikowej, szybkość działania magistrali wewnętrznych itp.), jak i elementy odpowiadające za szybkość i niezawodność wymiany danych. Aby być pewnym dostępności poprawnych danych w maksymalnym stopniu pamięci masowe muszą zapewniać następujące wymagania:
1. szybki dostęp do danych
2. duża pojemność
4. skalowalność
5. wysokie bezpieczeństwo przechowywanych informacji
6. odporność na zdarzenia losowe
7. niski koszt konstrukcji i eksploatacji systemów pamięciowych

Miary efektywności obliczeniowej procesorów to wskaźniki opisujące, jak szybko procesor jest w stanie wykonać określone zadania. Najbardziej popularne miary efektywności obliczeniowej to:
- Częstotliwość zegara – decyduje o szybkości wykonywania operacji na komputerze  Szybkość obliczeń mierzymy w **_(to są te miary wydajności systemów obliczeniowych)_**:  
	- **MIPS (Millions of Instructions per Second)** –  określa liczbę operacji (stałoprzecinkowych) jakie procesor jest w stanie wykonać w czasie sekundy.
	- **MFLOPS (Millions of Floating Point Operations per Second)** – mierzy liczbę operacji zmiennoprzecinkowych, jakie procesor jest w stanie wykonać w ciągu jednej sekundy.
	- MHz (Megahertz) lub GHz (Gigahertz) - określają częstotliwość taktowania procesora, czyli liczbę cykli pracy na sekundę.
	- IPC (Instructions Per Clock) 

Pojemność pamięci komputerowej jest mierzona w bajtach (B) lub kilobajtach (KB), megabajtach (MB), gigabajtach (GB) i terabajtach (TB). Miarami wydajności systemów są pamięć i czas.

Na wydajność procesora ma też wpływ:
- Liczba i cechy bloków wykonawczych – liczba jednostek wykonujących operacje określone w instrukcjach programu w języku wewnętrznym oraz ich cechy funkcjonalne
- Struktura i parametry pamięci – liczba poziomów pamięci (w tym liczba poziomów pamięci podręcznej). Organizacja zapisywanej informacji, pojemności
- Cechy i parametry listy rozkazów – typy i format instrukcji języka wewnętrznego, dostępne tryby adresowania, metoda realizacji instrukcji wejścia/wyjścia  

**_Trzy kolejne określają wydajność obliczeniową procesora:_**
- **Liczba i rozmiary rejestrów danych**
- **Liczba i rozmiary rejestrów adresowych**
- **Szerokość szyn danych i adresów**
## Prawo Moore’a i implikacje z niego wynikające w kontekście rozwoju sprzętu komputerowego.

Prawo Moore'a to prawo, które stwierdza, że liczba tranzystorów na jednostkę powierzchni układu scalonego podwaja się co około 1,2-1,3 roku. To prawo zostało opublikowane po raz pierwszy przez Gordona Moore'a w 1965 roku i od tego czasu stało się jednym z najbardziej znanych i niezawodnych trendów w historii rozwoju elektroniki.

Implikacje związane z Prawem Moore'a są znaczne i dotyczą nie tylko samego rozwoju sprzętu komputerowego, ale także szeroko pojętej technologii informacyjnej. Oto kilka kluczowych implikacji:
- **Postęp technologiczny**: Dzięki ciągłemu wzrostowi liczby tranzystorów na jednostkę powierzchni, sprzęt komputerowy staje się coraz bardziej zaawansowany i wydajny, co przyczynia się do jego rozwoju.
- **Zmniejszanie cen**: Zwiększenie liczby tranzystorów na jednostkę powierzchni układu scalonego prowadzi do niższych cen i dostępności komputerów dla szerokiej publiczności.
- **Nowe aplikacje**: Zwiększona wydajność sprzętu komputerowego pozwala na stworzenie nowych aplikacji i usług, takich jak sztuczna inteligencja czy chmura obliczeniowa.
- **Zmiana sposobu życia**: Prawo Moore'a i jego implikacje sprawiają, że technologia informacyjna jest coraz bardziej dostępna i powszechna, co zmienia sposób, w jaki ludzie żyją, pracują i komunikują się.