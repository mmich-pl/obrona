## Zarządzanie projektem budowy oprogramowania: rodzaje działań, dobór metodyki oraz kontekst pozatechniczny.
>[!info] **Metodyka** – zestaw pojęć, notacji, modeli, języków, technik i sposobów postępowania służących do analizy dziedziny stanowiącej przedmiot projektowanego systemu oraz do projektowania pojęciowego, logicznego i/lub fizycznego

Podział metodyk ze względu na podejście do procedur, dokumentów itp.:
1. Ciężkie – duża formalność, wiele dokumentów, zatwierdzeń, stosowane do dużych projektów:
	- Prince2
	- PMBoK/PMI
2. Lekkie (zwinne) – mniej formalne, dokumentacja nie gra dużej roli:
	- SCRUM
	- XP
	- XPrince

Metodyka ustala:
- Fazy projektu
- Role uczestników projektu
- Scenariusze postępowania w każdej z faz
- Reguły przechodzenia między fazami
- Notacje, których należy używać
- Dokumentację powstającą w każdej z faz

Zarządzanie projektem budowy oprogramowania jest procesem planowania, wykonywania i kontrolowania projektu oprogramowania. Celem jest zapewnienie, że projekt jest wykonywany w terminie, budżecie i zgodnie z wymaganiami i oczekiwaniami klienta.
Podstawowe działania związane z zarządzaniem projektem oprogramowania to:
- Planowanie: określenie wymagań, budżetu, harmonogramu i zasobów potrzebnych do realizacji projektu.
- Organizacja: zdefiniowanie zespołu projektowego, ustalenie odpowiedzialności i przydzielenie zadań.
- Realizacja: wykonywanie i kontrolowanie prac nad projektem w celu zapewnienia jego postępu.
- Kontrola: regularne sprawdzanie postępu projektu i wprowadzanie ewentualnych poprawek, tak aby był on realizowany zgodnie z planem.
- Zarządzanie zmianami: zarządzanie zmianami wymagań, harmonogramu i budżetu, tak aby projekt był realizowany zgodnie z oczekiwaniami klienta.
- Wybór odpowiedniej metodyki zarządzania projektem oprogramowania zależy od wielu czynników, takich jak wielkość projektu, skala i złożoność, dostępność zasobów i oczekiwania klienta. Popularne metodyki to m.in. Scrum, Waterfall, Kanban i Agile.

Kontekst pozatechniczny zarządzania projektem budowy oprogramowania obejmuje wpływ czynników zewnętrznych, takich jak polityka i regulacje prawne, kultura organizacyjna, dostępność zasobów i relacje między zespołem projektowym a klientem. Ważne jest, aby uwzględniać te czynniki w trakcie planowania i realizacji projektu, aby uniknąć potencjalnych problemów i zapewnić sukces projektu.
## Język UML – charakterystyka oraz sposób wsparcia różnorodnych modeli danych.
## Wzorce projektowe oraz ramy programistyczne (frameworks) – charakterystyka, przykłady, zastosowania. 

**Wzorce projektowe** – wielokrotnie powtarzające się i pozytywnie zweryfikowane schematy rozwiązań często spotykanych problemów projektowych. Dotyczą architektury całej aplikacji, a nie pojedynczej klasy. Stosowanie ich pozwala na pisanie **lepszych, bardziej efektywnych, skalowalnych, łatwiej modyfikowalnych, mniej narażonych na błędy programów**

Wzorce projektowe to dobrze udokumentowane i ustandaryzowane sposoby rozwiązywania często powtarzających się problemów w programowaniu. Są to gotowe rozwiązania, które można łatwo zastosować w wielu różnych sytuacjach, zapewniając jednocześnie przewidywalne i stabilne działanie oprogramowania. Wzorce projektowe są szczególnie przydatne w programowaniu obiektowym, takim jak Java.

Wzorce projektowe dzielą się na 3 klasy:
1. **Konstrukcyjne** – tworzenie obiektów, delegowanie procesu tworzenia do innych klas, kontrola nad sposobem tworzenia obiektów:
	- **Factory** – mamy jedną klasę, która tworzy obiekty innych klas – scentralizowany sposób tworzenia obiektów jest prostszy w modyfikacji
	- **Factory method** – mamy interfejs funkcyjny Factory do tworzenia obiektów klas implementujących interfejs Product (rozszerzenie factory, bo nie mamy jednej konkretnej implementacji, ale interfejs) – implementujemy te interfejsy do tworzenia fabryk i produktów – pozwala łatwo zmienić sposób tworzenia obiektów bez modyfikacji np. argumentów konstruktora w każdym miejscu
	- **Abstract factory** – rozszerzenie factory method: Interface AbstactFactory ma wiele metod do tworzenia wielu rodzajów produktów
	- **Singleton** – zapewnia, że klasa będzie miała tylko jedną instancję i zapewnia globalny dostęp do tego obiektu. Dodatkowo mechanizm „lazy instantiation”: obiekt jest tworzony tylko wtedy, gdy jest potrzebny.
	- **Builder** – pozwala tworzyć obiekty etapami krok po kroku. Mamy interfejs Builder, który ma kilka metod: po jednej na etap tworzenia obiektu.
	- **Prototype** – do kopiowania już istniejących obiektów bez tworzenia zależności między kodem a klasami obiektów. 
2. **Strukturalne** – zarządzanie strukturą obiektów i strukturami złożonymi z obiektów:
	- **Adapter** – do współdziałania obiektów o niekompatybilnych interfejsach. Klasa Adapter implementuje interfejs jednego obiektu i opakowuje drugi obiekt.
	- **Bridge** – do dzielenia dużej klasy lub zestawu spokrewnionych klas na dwie hierarchie – abstrakcję (np. GUI) i implementację (np. API).
	- **Composite** – łączenie część-całość w taki sposób, że części jak i całość mogą być traktowane w ten sam sposób. 
	- **Decorator** – do dodawania nowych obowiązków obiektom poprzez opakowywanie ich w inne obiekty – chroni przed psuciem kodu tam, gdzie dany obiekt jest już w danej formie używany + pozwala rozszerzać obiekty tam, gdzie nie możemy użyć dziedziczenia
	- **Facade** – do dostarczania uproszczonego interfejsu złożonym bibliotekom i frameworkom
	- **Flyweight** – do klas, które odwołują się do bardzo duże liczby podobnych (takich samych) obiektów, np. ramki wokół komponentów w GUI. Mamy klasę, która tworzy singletony powtarzających się obiektów, dzięki czemu klasy korzystające z tych obiektów współdzielą jedną instancję i oszczędzają pamięć (ten singleton powinien być niezmienny)
	- **Proxy** – do tworzenia obiektów zastępczych w miejsce innych obiektów (pośrednik do obiektu) – daje kontrolę dostępu i pozwala prowadzić dziennik żądań
3. **Behawioralne** – zachowanie obiektów i komunikacji między nimi:
	- **Chain of responsibility** – dajemy obiekt jakimś klasom, które po kolei coś robią z tym obiektem i przekazują go dalej.
	- **Command** – pozwala na enkapsulację zlecenia do wykonania jako obiekt klasy implementującej określony interfejs. Uniezależnia logikę działania aplikacji od konkretnych zleceń do wykonania – upraszcza modyfikowalność
	- **Interpreter** – tłumaczy jedną rzecz na inną.
	- **Iterator** – pozwala przechodzić obiekt po obiekcie niezależnie od użytej struktury danych (listy, stosu, drzewa itd.). – Kolekcje w Javie mają swoje iteratory
	- **Mediator** – do komunikacji między obiektami, redukuje chaos zależności między obiektami (taki kontroler lotów, który pilnuje, kto kiedy ląduje)
	- **Memento** – uzewnętrznia stan obiektu, zazwyczaj żeby móc go przywrócić (np. do poprzedniego stanu – operacja undo, rollback)
	- **Observer** – jeżeli obiekt „obserwowany” zmienia stan, „obserwator” jest o tym powiadamiany. Pozwala na komunikację między niepowiązanymi obiektami.
	- **State** – do reprezentacji stanu aplikacji, pozwala zmieniać zachowanie obiektu w zależności od jego stanu  – stan aplikacji jest w jednym obiekcie, a nie mieszance zmiennych w całej aplikacji
	- **Strategy** – do definiowania rodziny algorytmów, umieszczania ich w osobnych klasach tak, by były wymienialne – pozwala wykorzystywać różne warianty algorytmu w zależności od sytuacji, nawet w trakcie działania programu
	- **Template** – definiujemy szkielet algorytmu w klasie bazowej, a podklasy mogą nadpisywać pewne etapy tego algorytmu bez zmiany całej jego struktury.
	- **Visitor** – definiuje operacje, które są wykonywane naobiektów innych klas, pozwala to wprowadzać nowe operacje bez zmieniania klas tych obiektów. Mamy intefejs Visitor, który definiuje metody operacji na obiektach jakichś klas, a w tych klasach dodajemy metodę accept(visitor), która wykonuje operację visitora na this.
## Zapewnienie jakości oraz testowanie oprogramowania – normy, metody, kryteria. 
Zapewnienie jakości i testowanie oprogramowania to procesy mające na celu zagwarantowanie, że oprogramowanie jest działające zgodnie z wymaganiami i spełnia wymagania jakościowe. W celu osiągnięcia tego celu stosuje się różne normy, metody i kryteria.
### Testowanie
> [!info] **Weryfikacja** – testowanie zgodności systemu z wymaganiami zdefiniowanymi w fazie określenia wymagań. W skład weryfikacji wchodzą: przeglądy, inspekcje, testowanie, sprawdzanie, audytowanie

Główne cele testowania:
- Wykrycie i usunięcie błędów w systemie
- Ocena niezawodności systemu

Czynności związane z weryfikacją:
- Przeglądy techniczne oraz inspekcja oprogramowania
- Sprawdzanie zgodności wymagań na oprogramowanie z wymaganiami użytkownika
- Sprawdzanie zgodności komponentów projektu z wymaganiami na oprogramowanie
- Testowanie jednostek oprogramowania (modułów)
- Testowanie integracji oprogramowania, testowanie systemu
- Testowanie akceptacji systemu przez użytkowników

>[!info] **Przegląd** – proces lub spotkanie, podczas którego produkt roboczy lub ich zbiór jest prezentowany personelowi projektu, kierownictwie, użytkownikom, klientom lub innym zainteresowanym strono w celu uzyskania komentarzy, opinii i akceptacji. Może być formalny lub nieformalny

Rodzaje przeglądów formalnych:
-  Przegląd techniczny – oceniane są elementy oprogramowania na zgodność postępu prac z przyjętym planem
- Przejście (walkthrough) – ocena dokumentów/modeli/projektów/kodu w celu szybkiego wykrycia defektów lub błędów stylistycznych (jak np. wcięcia w kodzie) i szkolenia
- Audyt – ocena projektu przez osoby niezależne od zespołu projektowego w celu potwierdzenia zgodności projektu z wymaganiami, standardami, procedurami, kontraktami itp. – ma dostarczyć obiektywną ocenę. JEST ZWIĄZANY Z NORMAMI JAKOŚCI
	- Posiada możliwości by osiągnąć sukces (zasoby, kompetencje, metody, standardy)
	- Optymalnie wykorzystuje te możliwości
	- Rzeczywiście osiąga założone cele (cząstkowe)

>[!info] **Inspekcja** – formalna technika oceny, gdzie wymagania są szczegółowo badane przez osoby nie będące autorami, w celu wykrycia błędów/naruszeń standardów/innych problemów. Stosowane dla „elitarnych” systemów

Rodzaje testów:
1. **Wykrywanie błędów** ­– mają wykryć jak najwięcej błędów w programie
2. **Testy statystyczne** – wykrywają przyczyny najczęstszych błędów + ocena niezawodności systemu
3. **Testy dynamiczne** – wykonywanie fragmentów programu i porównywanie uzyskanych wyników z wynikami poprawnymi
4. **Testy statyczne** – analiza kodu bez jego uruchamiania (wykonywanie kodu w myśli). Nieefektywne dla większych programów. Metody matematyczne weryfikacji programów też są testami statycznymi

**Typowe fazy testowania systemu**:
- **Testy modułów** – już w fazie implementacji, tuż po skończeniu modułu
- **Testy systemu** – integrowanie modułów i testowanie podsystemów i systemu jako całości
- **Testy akceptacji** – wykonywane przez przyszłego użytkownika: **testy alfa** – jak system jest na zamówienie i dajemy go klientowi do przetestowania; **testy beta** – jak system chcemy wypuścić na rynek i przekazujemy za darmo kilka kopii do przetestowania

Testowaniu podlegają:
- Wydajność systemu
- Interfejsy systemu
- Własności operacyjne systemu
- Zużycie zasobów
- Zabezpieczenia
- Przenaszalność (np. na różne systemy operacyjne)
- Niezawodność (jak często są awarie)
- Odtwarzalność (ile czasu potrzeba na naprawę awarii)
- Kompletność i jakość funkcji

| Testy białej skrzyki | Testy czarnej skrzynki |
| :--: | ---- |
| Logika wewnątrz programu może być sprawdzona | Nie znamy logiki wewnętrznej programu (nie widzimy, co się w środku dzieje) |
| Stosujemy do tego kody diagnostyczne i debuggery, które pozwalają śledzić np. zawartość zmiennych | Obejmuje cały zakres danych wejściowych |
| Wymagają przygotowania danych testowych (tak, by przetestować każdą możliwą ścieżkę w programie – wszystkie ify/else ify, maksymalnie dużo obrotów pętli/przeciętnie dużo obrotów pętli/ani jeden obrót pętli) | Żeby tych danych nie było nieskończoność (**kombinatoryczna ekspozja**), tworzymy „klasy równoważności” – dzielimy możliwe dane na takie grupy, jakie będą powodować te same błędy (np. liczby ujemne, dodatnie i zero), podział ten zależy od wymagań (warto też sprawdzać wartości graniczne względem tych wymagań) |
| Nie pozwalają pokazać brakujących funkcji w programie | Często wymaga testowania kombinacji różnych typów danych – używamy do tego tablic decyzyjnych lub grafów przyczyna-skutek |

Techniki testów systemu:
-  Testy wstępujące – najpierw testujemy pojedyncze moduły i stopniowo wchodzimy na coraz wyższy poziom aż do poziomu całego systemu – nie zawsze możliwe, moduły mogą być od siebie niezależne
-  Testy zstępujące – najpierw testujemy moduły wyższego poziomu, a te niższego poziomu zastępujemy implementacjami szkieletowymi. Po testach na wyższym poziomie, dokładamy moduły niższego poziomu. Robimy tak, aż zintegrujemy cały system

**Testy obciążeniowe** – badają wydajność i niezawodność systemu, wymuszają obciążenie równe lub większe niż maksymalne

**Testy odporności** – testy tego, co się stanie w przypadku zaniku zasilania, awarii sprzętowej, wprowadzenia niepoprawnych danych lub wydania sekwencji niepoprawnych poleceń

### Jakość
>[!info] **Zapewnienie jakości** – zespół działań zmierzających do wytworzenia u wszystkich zainteresowanych przekonania, że dostarczony projekt realizuje swoje funkcje i odpowiada aktualnym wymaganiom i standardom.

>[!info] Pomiar jakości
>Proces, w którym atrybutom  świata rzeczywistego przydziela się liczby lub symbole według jasno określonych zasad.
#### Cykl Deminga
Zwany także Kołem Deminga, cyklem poprawy lub cyklem PDCA (Plan, Do, Check, Action), zakłada cykliczną realizację wyżej kolejnych etapów: planowanie, wykonanie, sprawdzenie (kontrolę) i działanie.

Cykl Deminga składa się z czterech etapów:
- **Planowanie**, czyli dokładna analiza obecnej sytuacji i określenie czynności, które są niezbędne do otrzymania efektu najwyższej jakości
- **Wykonanie** zgodnie ze wszystkimi punktami zamierzonego planu. Przetestowanie wybranych rozwiązań, które może m.in. obejmować przeszkolenie pracowników w zakresie wprowadzanych ulepszeń.
- **Badanie wyników**, a więc sprawdzanie, jak wybrane i podjęte działania pozwoliły osiągnąć cel i co można zrobić, by ulepszyć dany proces. W tym momencie zostaje podjęta decyzja o tym czy plan działa. Często dane rozwiązanie musi zostać zmodyfikowane lub odrzucone.
- **Działanie**, które polega na udoskonalaniu procesu i włączeniu pomysłów do kolejnego planu. Wprowadza się także obecny plan, jako najlepsze na ten moment rozwiązanie, z równoczesnym poinformowaniem o tym reszty organizacji.
## Rodzaje, metody specyfikowania oraz rola wymagań w procesie wytwarzania oprogramowania.

Specyfikowanie wymagań jest procesem identyfikowania i dokumentowania oczekiwań dotyczących oprogramowania. Jest to kluczowy element w procesie wytwarzania oprogramowania, ponieważ odpowiada za określenie, czego klienci i użytkownicy oczekują od oprogramowania i jakie funkcje muszą być dostarczone.

Rola wymagań w procesie wytwarzania oprogramowania jest kluczowa, ponieważ służą jako punkt wyjścia do projektowania i tworzenia oprogramowania. Wymagania określają, co oprogramowanie powinno robić i jak powinno działać, co pomaga zapewnić, że oprogramowanie jest funkcjonalne i odpowiada potrzebom użytkowników. Wymagania są również istotne dla procesu testowania, ponieważ pomagają określić, jakie testy należy przeprowadzić, aby upewnić się, że oprogramowanie spełnia oczekiwania.

Poziomy ogólności opisu wymagań:
-  Definicja wymagań – ogólny opis w języku naturalnym, wynik wstępnych rozmów z klientem
- **Specyfikacja wymagań** – ustrukturalizowany zapis wykorzystujący język naturalny + proste, częściowo sformalizowane notacje
- **Specyfikacja oprogramowania** – formalny opis wymagań, podzielenie wymagań na zwięzłe punkty. Podstawa fazy testowania

Dobry opis wymagań powinien:
- Być kompletny i niesprzeczny
- Opisywać zewnętrzne zachowanie systemu, a nie sposób jego realizacji
- Obejmować ograniczenia przy jakich musi pracować system
- Brać pod uwagę możliwe zmiany wymagań wobec systemu
- Opisywać zachowanie systemu w skrajnych lub niepożądanych sytuacjach

Metody rozpoznania wymagań:
- **Wywiady i przeglądy** – lista pytań podzielona na odrębne zagadnienia, powinna pokrywać całość tematu. Wywiad powinien być przeprowadzany na reprezentatywnej grupie użytkowników, i powinien doprowadzić do szerokiej zgody i akceptacji projektu
- **Studium nad istniejącym oprogramowaniem** – ma ustali dobre i złe strony oprogramowania, które nasz projekt zastępuje
- **Studia osiągalności** – określenie realistycznych celów systemu i metod ich osiągnięcia
- **Prototypowanie** – Zbudowanie prototypu systemu działającego w zmniejszonej skali, z uproszczonym interfejsem

>[!info] Rodzaje wymagań 
>dzielą sie na funkcjonalne, niefunkcjonalne i wymagania regulacyjne. Wymagania funkcjonalne odnoszą się do tego, jak oprogramowanie powinno działać, natomiast wymagania niefunkcjonalne dotyczą cech takich jak niezawodność, bezpieczeństwo i wydajność. Wymagania regulacyjne związane są z wymaganiami prawnymi i przepisami.

Rodzaje wymagań:
1. **Funkcjonalne** – opisują funkcje wykonywane przez system lub systemy zewnętrzne:
	- Określenie wszystkich rodzajów użytkowników w systemie
	- Dla każdego rodzaju użytkownika – określenie funkcji oraz sposobów korzystania z systemu
	- Określenie systemów zewnętrznych
2. **Niefunkcjonalne** – opisują ograniczenia, przy których system ma realizować swoje funkcje:
	- **Wymagania dotyczące produktu** – np. możliwość operowania systemem wyłącznie przy pomocy klawiatury
	- **Wymagania dotyczące procesu** – np. realizacja harmonogramów ma być zgodna z jakimś dokumentem
	- **Wymagania zewnętrzne** – np. system musi współpracować z jakąś konkretną bazą danych bez zmiany jej struktury

**Metody specyfikacji wymagań**:
- **Język naturalny** – najczęściej stosowany, ale ma problemy z niejednoznacznością i nadmierną elastycznością (możliwością wyrażenia tego samego na wiele sposobów)
- **Formalizm matematyczny** – tylko dla specyficznych celów
- **Język naturalny strukturalny** – ograniczone słownictwo i składnia. Tematy i zagadnienia w punktach i podpunktach
- **Tablice, formularze** – zazwyczaj dwuwymiarowe tablice, pozwalają kojarzyć ze sobą różne aspekty (np. typ użytkownika z rodzajem usługi_
- **Diagramy blokowe** – forma graficzna przedstawiająca cykl przetwarzania
- **Diagramy przypadków użycia** – do przedstawienia aktorów i funkcji systemu