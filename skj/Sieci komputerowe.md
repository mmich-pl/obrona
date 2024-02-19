## Usługi i protokoły warstwy aplikacji na przykładzie protokołu HTTP.
>[!info] Warstwa aplikacji jest najwyższą warstwą stosowaną w modelach OSI oraz TCP/IP. Tworzy czytelny dla użytkownika interfejs komunikacyjny pomiędzy aplikacjami a siecią komputerową.
  Protokoły warstwy aplikacji działają w wielu systemach końcowych.

Najwyższa warstwa modelu ISO/OSI jak i modelu TCP/IP. Oba modele jednak w inny sposób definiuję szczegóły jak i zastosowanie. Jak nazwa wskazuje warstwa ta przekazuje dane aplikacji i to do nich należy interpretowanie danych. Mogą być to zarówno dane stron internetowych pobierane przy pomocy HTTP jak i zawartość poczty przy pomocy POP3.

Protokół w warstwie aplikacji określa:
- Rodzaje komunikatów – np. komunikaty żądania i odpowiedzi
- Składnię komunikatów – jakie pola zawiera komunikat i jak te pola są oddzielane
- Znaczenie informacji w polach komunikatu
- Zasady określające kiedy i jak procesy wymieniają komunikaty

Protokoły Wiki:
* HTTP
* Telnet
* SSH
* FTP
* SMTP
* DNS
HTTP jest protokołem w modelu klient/serwer określony przez specyfikację RFC. Używa TCP w pierwszych wersjach oraz jest **bezstanowy** – nie utrzymuje informacji o poprzednich połączeniach HTTP. W ramach optymalizacji używa wciąż tego samego łącza.

Jest oparty o model klient\serwer:
- Klient – przeglądarka, która żąda, otrzymuje i wyświetla obiekty WWW
- Serwer – wysyła obiekty w odpowiedzi na żądania

W HTTP mamy 2 typy komunikatów:
- Żądanie – składa się z:
	- Linii żądania - GET /katalog/strona.html HTTP/1.1 (polecenie, adres, wersja HTTP)
	- Nagłówków - np. Host: www.uczelnia.edu.pl, User-agent: Mozilla/4.0
	- Znaku carriage return, line feed (pusta linia) – oznacza koniec nagłówków
	- Danych lub pustej linii
- Odpowiedzi:
- Linii statusu - HTTP/1.1 200 OK (wersja HTTP, kod statusu, jego nazwa)
- Nagłówków – np. Content-Length: 6821, Content-Type: text/html
- Danych - np. Plik HTMP

Metody żądań HTTP:
-  GET – do pobierania danych
- POST – do wysyłania danych
- HEAD – prośba o posłanie odpowiedzi bez żądanego obiektu (danych)
- PUT – do wysyłania pliku, który chcemy umieścić pod danym adresem URL
- DELETE – do usuwania obiektów pod danym adresem URL

Typy kodów odpowiedzi HTTP:
- 1xx – kod informacyjny
- 2xx – kod powodzenia
- 3xx – przekierowania
- 4xx – błąd po stronie klienta 
- 5xx – błąd po stronie serwera
## Usługi warstwy transportu na przykładzie protokołu TCP. 
Warstwa transportu to abstrakcyjny byt określony przez modele takie jak TCP/IP czy ISO/OSI. Dzisiejsze implementacje raczej kierują się do definicji opartych o TCP/IP.

Według modelu ISO/OSI odpowiada ona za transportowanie danych o zmiennej długości między aplikacjami na różnych komputerach w różnych sieciach, zapewniając jednocześnie jakość. Ta warstwa dzieli dane na segmenty i odpowiada za kontrolę utraty danych, która w TCP jest zrealizowana przez retransmisję brakujących elementów.

W obu modelach mogą wystąpić dwa typy transportu - połączeniowe i bezpołączeniowe.

TCP tworzy abstrakcyjne strumienie, które pozwalają wysyłać dane między aplikacjami pod spodem dzieląc je na segmenty, które przesyłane są między komputerami w odpowiedniej kolejności. Protokół gwarantuje odpowiednią kolejność przekazywanych danych oraz zapewnia, że każdy segment danych dotrze do komputera docelowego. Pozwala on także na wskazanie portów w celu odróżnienia wielu strumieni dla jednej maszyny (multipleksacja oraz demultipleksacja). Z najważniejszych usług samego TCP (wykład):
* Połączeniowa - wymaga inicjalizacji połączenia
* Niezawodna komunikacja - komunikaty docierają w pełni i prawidłowej kolejności
* Kontrola przepływu - mechanizmy kontrolujące ilość pakietów względem możliwości odbiorcy
* Kontorla przeciążaenia - mechanizmy kontrolujące ilość pakietów względem możliwości sieci
* Jeden nadawca-Jeden odbiorca (**koniec-koniec**)
* Bajty są wysyłane strumieniowo (**nie ma granic komunikatów**)
* Bufory u nadawcy i odbiorcy
* Komunikacja „**full duplex**” – dane mogą przepływać w obie strony w ramach tego samego połączenia
## Protokoły rutingu warstwy sieci na przykładzie protokołu OSPF.
Protokoły routingu/trasowania to protokoły, które koordynują kierowanie pakietów w sieci. Opisują one głównie jak zorientowane są między sobą elementy oraz każdemu elementowi jak wygląda status sieci. Najczęściej celem jest także wskazanie "optymalnej trasy" pod względem wybranej metryki. Mogą się one opierać na analizie dostarczonych danych o stanie całości sieci jednak istnieją algorytmy dynamiczne, które zbierają informacje z sieci.

Typy wymienione na wikipedi:
* Protokoły trasowania wektora odległości - okresowe przekazywanie danych o wszystkich sąsiadach sąsiadom.
* Protokoły trasowania stanu łącza - rozsyłanie informacji tylko o swoich podsieciach
* Protokoły hybrydowe trasowania - łączą dwa powyższe
* Protokoły trasowania typu path-vector - opisują trasy przy pomocy atrybutów

OSPF - Protokół oparty o wiedzę o aktualnym stanie sieci (stanu łącza). Kontroluje on przepływ pakietów wewnątrz "systemu autonomicznego".  Pełne rozwnięcie OSPF to Open Shortest Path First tłumaczone na wikipedii na "pierwszeństwo ma najkrótsza ścieżka".
- Używa algorytmu stanu łącza:
	- Mapa topologii w każdym węźle sieci
	- Obliczanie ścieżek przy użyciu algorytmu Dijkstry
		- **Multipath** – przy ustalaniu ścieżki w grafie, może istnieć wiele ścieżek o tym samym koszcie
- Ogłoszenie OSPF ma jeden wpis dla każdego sąsiadującego rutera
-  Ogłoszenia są rozsyłane do całego AS (przez zalew) – komunikaty są rozsyłane bezpośrednio przez IP (a nie TCP/UDP)
- Dla każdego łącza możemy mieć **wiele miar kosztu ścieżki** (w zależności od rodzaju usługi)
- Zintegrowany ruting unicast i multicast

Hierarchiczny OSPF
- **Dwupoziomowa hierarchia** – obszar lokalny i szkielet (stan jest ogłaszany tylko w obszarze lokalnym, każdy węzeł zna tylko kierunek do sieci w innych obszarach, a nie ich całą topologię)
- **Rutery brzegowe obszarów** – „podsumowują” odległości do sieci w swoim obszarze i ogłaszają te informacje innym ruterom brzegowym obszarów
- **Rutery szkieletowe** – realizują ruting OSPF w sieci szkieletowej
- **Rutery brzegowe** – łączą się z innymi AS
## Usługi warstwy łącza na przykładzie protokołu Ethernet lub protokołów z rodziny 802.11 (WiFi).
Usługi:
* Tworzenie ramek, dostęp do łącza
* Niezawodna komunikacja między sąsiednimi węzłami
* Kontrola przepływu
* Rozpoznawanie błędów
* Korekcja błędow przez kody nadmiarowe
* komunikacja półdupleksowa i w pełni dupleksowa

Możemy mieć dwa typy łącz:
* punkt-punkt - dzisiejszy Ethernet między switchem, a hostem
* punkt-wielopunkt - wspólne medium jak fale radiowe lub wspólny kabel. Stary ethernet lub 802.11

Abstrakcyjna warstwa opisana tylko w modelu ISO/OSI. Opisuje ona strukturę danych kodowanych w medium fizycznym. Podstawowe dwa poznane w ramach studiów to Ethernet przy połączeniach kablowych oraz rodzina 802.11 używany do połączeń bezprzewodowych.  Protokoły tej warstwy mogą, ale nie muszą naprawiać błędy generowane przez medium warstwy niższej - przykładem jest korekcja kolizji transmisji w sieciach bezprzewodowych.

Ethernet to "dominująca" technologia LAN, która nadążyła za potrzebą prędkości (10/100/1000Megabit/s). Technolofia nie zapewnia potwierdzenia odbioru z czego wynika zawodność - możliwość gubienia danych.

**Ethernet to usługa:**
-  Bezpołączeniowa – nie ma sygnalizacji pomiędzy nadającym i odbierającym adapterem
-  Zawodna – odbierający adapter nie wysyła ACK ani NAK do nadającego adaptera (ciąg przekazywanych pakietów może mieć luki. Są one wypełniane, jeśli aplikacja używa TCP)

Ethernet używa **CMSA/CD** (Carrier Sense Multiple Access with Collision Detection):
- Adapter nie transmituje jeśli słyszy transmisję innego adaptera, czyli nasłuchiwanie (carrier sense)
-  Transmitujący adapter przerywa gdy zauważy, że inny adapter transmituje, czyli wykrywanie kolizji (collision detection)
- Zanim adapter rozpocznie retransmisję, czeka przez losowy okres czasu


802.11 to rodzina protokołów przeznaczona do komunikacji bezprzewodowej. Ulega ona znacznie większym zakłóceniom oraz współdzieli medium transportu. Posiada mechanizm rezerwacji łącza- urządzenie może wysłać krótki komunikat, którego celem jest "uproszenie" wolnego łącza.

Charakterystyka łącza bezprzewodowego:
- **Słabsza moc sygnału** – sygnał radiowy ulega tłumieniu przy przechodzeniu przez materię
- Zakłócenia przez inne źródła – standardowe częstotliwości (np. 2.4 GHz) są współdzielone przez różne urządzenia (np. telefony). Mogą być też zakłócane przez np. silniki
- **Propagacja wielościeżkowa** – sygnał radiowy odbija się od przeszkód i gruntu, dochodząc do celu w różnym czasie, co utrudnia komunikację

Unikanie kolizji – wymiana RTS-CTS:
- RTS – request to send – krótka ramka wysyłana przez nadawcę, która zawiera długość planowanej transmisji
-  CTS – clear to send – odpowiedź odbiorcy na ramkę RTS (zawiadamia też „ukryte” węzły o chęci komunikacji, żeby nie doszło do zakłóceń)
- Przez ustalony czas, ukryte węzły nie będą transmitowały
## Metody ochrony informacji stosowane w bankowości Internetowej.
Metody ochrony informacji stosowane w bankowości internetowej są niezbędne do zapewnienia bezpieczeństwa i poufności informacji finansowych klientów. Oto kilka z najważniejszych metod ochrony informacji stosowanych w bankowości internetowej:
- Szyfrowanie: Dane i transakcje są szyfrowane za pomocą protokołów bezpieczeństwa takich jak SSL lub TLS, aby zapobiec przechwyceniu danych przez nieautoryzowane osoby.
- Autentykacja użytkownika: Banki stosują różne metody autentykacji użytkownika, takie jak nazwa użytkownika i hasło, uwierzytelnianie dwuskładnikowe lub tokeny bezpieczeństwa, aby upewnić się, że tylko upoważniona osoba jest w stanie wykonać transakcje.
- Ochrona przed atakami: Banki stosują zaawansowane technologie, takie jak firewall, detekcja i prewencja włamań, aby chronić swoje systemy przed atakami hakerskimi i innymi zagrożeniami cyberbezpieczeństwa.
- Regularne aktualizacje bezpieczeństwa: Banki stale uaktualniają swoje systemy bezpieczeństwa, aby zapewnić, że są one zabezpieczone przed nowymi zagrożeniami.
- Monitoring i audyty: Banki regularnie monitorują swoje systemy i przeprowadzają audyty, aby wcześniej wykryć i naprawić jakiekolwiek potencjalne luki bezpieczeństwa.