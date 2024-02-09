## Konstrukcja obiektów i zarządzanie pamięcią operacyjną w Javie i C++. 
## Rola klas, interfejsów i mixinów w programowaniu na przykładzie języka Java. 

### Klasa
- **Klasy**:
    - Są szablonami, z których tworzone są obiekty.
    - Definiują pola (atrybuty) i metody (funkcje), które opisują stan i zachowanie obiektów.
	    - Specjalna metoda nazywana **konstruktorem**, która pozwalaj na inicjowanie obiektów przy ich tworzeniu.
		    - Zawsze ma taką samą nazwę jak klasa
			- Nie ma typu wyniku (NAWET NIE JEST TYPU VOID)
			- Ma listę parametrów (która może być pusta – np. hibernate wymaga bezparametrowego konstruktora)
    - Klasy mogą dziedziczyć po innych klasach, co umożliwia reużywanie kodu.
    - Klasy mogą również implementować interfejsy, co oznacza, że muszą dostarczyć ciała dla metod zdefiniowanych w interfejsie.

```java
class Circle {
	private int radius;

	public Circle(int radius) {
		this.radius = radius;
	}

	public int area() {
		// code...
	}
}
```

Klasy w Javie realizują idee:
- **Abstrakcji obiektowej –** możemy definiować własne typy danych, ich cechy (atrybuty) i usługi (metody) – do tego, program jest pisany w tym samym języku, co problem, który ma rozwiązać (obiekty są pewną reprezentacją rzeczywistości)
- **Enkapsulacji/Hermetyzacji** (to to samo) – ukrywanie widoczności pól danej klasy dla innych klas w celu ochrony danych (operatory private/public/protected (protected – brak operatora, po prostu nic nie piszemy)
- **Ponownego użycia –** jak mamy w programie wiele danych o tych samych cechach, to zamiast definiować to samo kilkukrotnie, możemy to zawrzeć w klasie i tylko tworzyć nowe obiekty tej klasy

### Interfejs
- **Interfejsy**:
    - Są zbiorem **publicznych** metod **abstrakcyjnych** (metod bez podanej implementacji), które klasa musi zaimplementować, aby spełnić dany interfejs.
    - Interfejsy nie mogą zawierać metod domyślnych ani prywatnych, ani metod statycznych.
    - Klasa może implementować wiele interfejsów jednocześnie.

Interfejsy w Javie mają na celu rozwiązanie problemów związanych z **wielodziedziczeniem** (gdzie klasa dziedziczy po kilku innych klasach).

**Implementacja interfejsu w klasie** – zdefiniowanie w tej klasie wszystkich metod interfejsu (oznaczane słowem kluczowym _implements_) – chyba, że jest klasą abstrakcyjną (taką, w ramach której nie można tworzyć obiektów), wtedy może implementować interfejs bez definiowania jego metod (klasy dziedziczące po tej klasie będą musiały to zrobić)

```java
public interface Item {
	void setName(String name);
	String getName();
} 

public class DocumentItem implements Item {
	private String name;     
	
	@Override     
	public void setName(String name) {
		this.name = name;     
	}     
	
	@Override     
	public String getName() {
		return name;
	}
}
```

## Pojęcie dziedziczenia na przykładzie języków Java i C++. Istota i zastosowania polimorfizmu na przykładzie języków Java i C++. 

>[!info] Dziedziczenie
Mechanizm polegający na przejęciu właściwości i funkcjonalności obiektów innej klasy i ewentualnej modyfikacji tych właściwości i funkcjonalności w taki sposób, 
>Klasę z której dziedziczymy nazywamy **klasą bazową**, zaś klasę, która po niej dziedziczy nazywamy **klasą pochodną**. Klasa pochodna może korzystać z funkcjonalności klasy bazowej i z założenia powinna rozszerzać jej możliwości (poprzez dodanie nowych metod, lub modyfikację metod klasy bazowej) by były one bardziej wyspecjalizowane – relacja generalizacja-specjalizacja.  
Dziedziczenie zwiększa **ponowne użycie** kodu

| Java | C++ |
| ---- | ---- |
| Słowo kluczowe **extends** – do dziedziczenia | Zamiast extends używa się dwukropka – class B : public/private/protected A.<br><br><br>Nie ma wspólnej klasy bazowej dla wszystkich klas (takiego jak Object w Javie) |
| Nie ma wieloczedziczenia | Jest wielodziedziczenie |
| Kod przy tworzeniu obiektu wykonuje się w następującej kolejności:<br>1. Wywołanie konstruktora klasy pochodnej (tej, która dziedziczy)<br>2. Jeśli jego pierwsza instrukcja to **super(args)** to wykonywany jest konstruktor nadklasy z argumentami args<br>3. Jeśli nie ma super, to wywoływany jest bezparametrowy konstruktor nadklasy (trochę tak, jakby zawsze była ukryta instrukcja super())<br>4. Jak konstruktor nadklasy się wykona, wykonywane są pozostałe instrukcje klasy pochodnej | 1. Tak jak w Javie, najpierw tworzony jest obiekt nadklasy<br>- Nadklasa musi posiadać konstruktor domyślny (bezargumentowy)<br>2.  Zamiast super jest **lista inicjalizacyjna** – na niej umieszczamy jawnie wywołanie konstruktora dla podobiektu – przy nagłówku konstruktora po dwukropku wywołujemy konstruktor nadklasy.<br>- Jak korzystamy z wielodziedziczenia, to konstruktory nadklas są wywoływane zgodnie z kolejnością w liście inicjalizacyjnej<br><br>- **Destruktory są wywoływane w kolejności odwrotnej do konstruktorów** |
| Problem kruchości interfejsu klasy bazowej – jak zmienimy interfejs klasy bazowej, to prawdopodobnym jest, że będziemy musieli modyfikować kod wielu klas dziedziczących po tej klasie bazowej |  |
| @Override – pozwala zaznaczyć, że chcemy przysłonić daną metodę | Konstruktory i destruktory nie są dziedziczone |


W C++:

- 
- Polimorfizm osiąga się przez **rzutowanie w górę (upcasting)** – wskaźnik nadklasy pokazuje na obiekt podklasy (np. chcemy mieć adres obiektu klasy Shape&, a podajemy adres klasy Triangle):

- Niejawne rzutowanie w górę zachodzi tylko, jeśli klasa pochodna dziedziczy z klasy bazowej publicznie (słowo public w dziedziczeniu)
- Jeśli nie, trzeba użyć operatora **static_cast** lub **dynamic_cast**  
     

- 
- Dziedziczenie definicji operatora przypisania (w C++ możemy ustalać, co dla danej klasy znaczy +, -, = itd.  ) też jest dziedziczone (co może sprawić problemy, jeśli tego nie przedefiniujemy – pola z nowej klasy będą przypisywane w sposób dostarczony przez system – pole po polu, prawdopodobnie nieprawidłowo) – przy przedefiniowaniu operatora w podklasie, można wywołać operator z nadklasy poprzez rzutowanie _this_ na nadklasę:  
     
- Jest wielodziedziczenie – class C : public A, B (dziedziczy publicznie z A i prywatnie z B)
- Zamiast pisania, że klasa jest abstrakcyjna, tworzy się **zerowe** **metody wirtualne** (bez definicji:  
    virtual int a())

- **Zerowe metody wirtualne** – takie, dla których w klasie pochodnej musimy dostarczać implementacji (nie można tworzyć obiektów klasy z tą metodą, jeśli jej nie zaimplementujemy):  
    virtual int f() = 0;
- **Zwykłe metody wirtualne** (bez = 0 na końcu) – metoda, której wywołanie jest polimorficzne (zakładamy, że będzie przysłoniona w podklasie) – **bez tego polimorfizm nie działa w C++**

- Jak po danej klasie zamierzamy dziedziczyć publicznie, to powinniśmy definiować destruktor jako metodę wirtualną (wtedy polimorficznie możemy usuwać obiekty i każda podklasa będzie musiała w swoim destruktorze usunąć swoją część)

29. Istota i zastosowania polimorfizmu na przykładzie języków Java i C++.

Nawet jeśli dany obiekt jest wskazywany przez referencję przeznaczoną dla jego nadklasy, to i tak wywoływana jest metoda tego konkretnego obiektu, np.:

Vehicle v = new Car();  
v.start(); //Nawet jeśli Vehicle ma metodę start, to I tak będzie tu wywołana metoda z klasy Car

**Dynamic/late binding** – dla metod wirtualnych, oznacza to, że **wiązanie odwołań z kodem** następuje **w fazie wykonania**, a nie w fazie kompilacji (w fazie kompilacji nie wiemy, jaki konkretnie obiekt podstawimy pod referencję typu Vehicle – może to być Car, Bike itp.)

**W Javie wszystkie metody są wirtualne (o konkretnej wersji metody decyduje typ dynamiczny – omówiony w części C++ tego zagadnienia) oprócz:**

- Metod statycznych (bo nie dotyczą obiektów)
- Metod ze specyfikatorem **final** (bo nie można jej przedefiniować w podklasie)
- Metod prywatnych

Polimorfizm sprawia, że wszystkie przyszłe podklasy mają już zapewnioną daną funkcjonalność (nie musimy się przejmować tym, że dana klasa nie potrafi czegoś zrobić), i pozwala zdecydować o sposobie realizacji tej funkcjonalności

Przykład polimorfizmu w Javie – metoda toString() – każdy obiekt możemy chcieć wypisać (nigdy nie ma tego problemu, że podanie obiektu do System.out.println() spowoduje błąd kompilacji), i w każdej klasie możemy zdecydować, jak dany obiekt wypisać

W C++:

- Wyróżniamy dwa typy obiektów:

- **Typ statyczny** – to, co mówi nam wskaźnik (jak w przykładzie z Javy: typem statycznym byłby Vehicle) – znany w trakcie kompilacji
- **Typ dynamiczny –** rzeczywisty obiekt, na który pokazuje wskaźnik (dla przykładu z Javy byłby to Car) – znany w trakcie wykonania programu

- Metodami wirtualnymi są tylko metody ze słowem kluczowym **virtual –** tylko dla metod wirtualnych znaczenie ma typ dynamiczny obiektu (dla zwykłych metod decydujący jest typ statyczny – **early binding**)
- Różnica wynika z tego, że late binding jest mniej wydajny, a C++ stawia na wydajność – znalezienie odpowiedniej wersji metody w trakcie wykonania programu jest czasochłonne + każdy obiekt klasy polimorficznej posiada adres do tablicy wszystkich wersji metody wirtualnej
- **Konstruktor nigdy nie może być wirtualny** (destruktor zazwyczaj jest)
- Słowo virtual do metody piszemy tylko w klasie bazowej (na szczycie hierarchii dziedziczenia) – w podklasach ta metoda też będzie wirtualna (możemy w nich pisać virtual, ale wpływa to tylko na czytelność kodu)
- **Polimorfizm można wyłączyć** poprzez odwołanie się do wersji metody konkretnie z nadklasy:  
    obiektB->A::fun(); (obiektB będący obiektem klasy B wywołuje wersję metody fun() pochodzącą z klasy A, po której klasa B dziedziczy)
- Na odwrót to nie działa: nie możemy zrobić a.B::fun(), bo klasa A nie wie nic o dziedziczącej po niej klasie B
## Użycie tablic oraz innych struktur danych w Javie i C++. Java Collections Framework.
## Programowanie współbieżne ? mechanizmy i narzędzia na przykładzie języka Java.
## Typy i metody sparametryzowane (generics) w Javie. Szablony  (templates) w C++. 
## Lambda-wyrażenia i interfejsy funkcyjne w języku Java.
## Przetwarzanie strumieniowe (środki pakietu java.util.stream).
## Narzędzia programowania operacji wejście-wyjścia w języku Java.