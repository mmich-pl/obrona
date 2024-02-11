## Konstrukcja obiektów i zarządzanie pamięcią operacyjną w Javie i C++. 

W Javie:
-  Tworzenie obiektów przy pomocy konstruktora
- Wykorzystuje **Garbage collector** do zarządzania pamięcią:
	- Jest to osobny program
	- Jego celem jest usuwanie nieużywanych obiektów z pamięci JVM (java virtual machine)
	- Koncepcja garbage collectora powstała w latach 50. na potrzeby języka LISP
	- Ma 2 typy:
		- Skalarny – dla każdego obiektu licznik odwołań (referencji do niego). W momencie gdy wynosi on 0, obiekt jest usuwany – ma problem bo **nie wykrywa cyklicznych referencji**
		- Wektorowy – rozwiązanie problemu algorytmów skalarnych, obiekty są przedstawiane jako **węzły w grafie** (skierowanym) – jak do danego węzła nie da się dotrzeć z żadnego innego węzła, to jest on usuwany, budowę grafu należy zacząć od obiektów, które na pewno są „żywe” (pełnią one rolę korzenia – by obiekt był żywy, musi być w jakiś sposób połączony z korzeniem)  
	- Ma kilka typów:
		- Serial – najprostszy: na czas działania wątku garbage collectora, inne wątki są zawieszane. Dobry do prostych (najlepiej jednowątkowych) programów 
		- Parallel – jak serial, ale garbage collector może mieć wiele wątków. Tryb domyślny w Javie:  
		- Concurrent Mark Sweep (CMS) – wiele wątków, które są uruchamiane:
			- Podczas oznaczania obiektów, do których istnieją odniesienia w pamięci
			- Jeśli równolegle nastąpi zmiana w pamięci sterty podczas czyszczenia pamięci  

W C++:
- Pamięcią trzeba zarządzać samodzielnie (nie ma garbage collectora)
- Operator **new** – do zapisywania nowego obiektu na stosie lokalnym (jak w javie)
- Oprócz stosu mamy **stertę** (heap) – obszar pamięci wolnej w programie, którą alokujemy zgodnie z potrzebami
- Przy operatorze new musimy podać typ danych i informację o ilości tych danych (na podstawie tego wyliczane jest, ile pamięci sterty należy na daną zmienną zaalokować)
- W momencie, gdy wskaźnik lokalny jest usuwany, **pamięć nie jest zwalniana** – następuje wtedy **wyciek pamięci** (zmienna na stercie istnieje, ale nie mamy do niej żadnego wskaźnika i nie możemy się przez to do niej odwołać)
- Operator **delete** – do zwalniania pamięci, można go stosować tylko do adresu, który został zwrócony przez operator new. Można go zastosować tylko raz do danego adresu
- Tablice trzeba usuwać przy pomocy operatora z nawiasami kwadratowymi: `delete [] my_table`;
- Żeby chronić się przed podwójnym zwalnianiem tego samego adresu, po wykonaniu delete warto ustawić wskaźnik na NULL/nullptr/0 (wszystkie te 3 wartości to to samo)
- Do usuwania obiektów klas należy zdefiniować **destruktor** – „odwrotność konstruktora” (ma tyldę przed nazwą): uruchamia delete dla wszystkich pól wskaźnikowych w klasie:

```cpp
~MyObj() {
	// code...
}
```
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

## Pojęcie dziedziczenia na przykładzie języków Java i C++. 

>[!info] Dziedziczenie
Mechanizm polegający na przejęciu właściwości i funkcjonalności obiektów innej klasy i ewentualnej modyfikacji tych właściwości i funkcjonalności w taki sposób, 
>Klasę z której dziedziczymy nazywamy **klasą bazową**, zaś klasę, która po niej dziedziczy nazywamy **klasą pochodną**. Klasa pochodna może korzystać z funkcjonalności klasy bazowej i z założenia powinna rozszerzać jej możliwości (poprzez dodanie nowych metod, lub modyfikację metod klasy bazowej) by były one bardziej wyspecjalizowane – relacja generalizacja-specjalizacja.  
Dziedziczenie zwiększa **ponowne użycie** kodu

| Java | C++ |
| ---- | ---- |
| Słowo kluczowe **extends** – do dziedziczenia | Zamiast extends używa się dwukropka – class B : public/private/protected A.<br><br><br>Nie ma wspólnej klasy bazowej dla wszystkich klas (takiego jak Object w Javie) |
| Nie ma wieloczedziczenia | Jest wielodziedziczenie |
| Kod przy tworzeniu obiektu wykonuje się w następującej kolejności:<br>1. Wywołanie konstruktora klasy pochodnej (tej, która dziedziczy)<br>2. Jeśli jego pierwsza instrukcja to **super(args)** to wykonywany jest konstruktor nadklasy z argumentami args<br>3. Jeśli nie ma super, to wywoływany jest bezparametrowy konstruktor nadklasy (trochę tak, jakby zawsze była ukryta instrukcja super())<br>4. Jak konstruktor nadklasy się wykona, wykonywane są pozostałe instrukcje klasy pochodnej | 1. Tak jak w Javie, najpierw tworzony jest obiekt nadklasy<br>- Nadklasa musi posiadać konstruktor domyślny (bezargumentowy)<br>2.  Zamiast super jest **lista inicjalizacyjna** – na niej umieszczamy jawnie wywołanie konstruktora dla podobiektu – przy nagłówku konstruktora po dwukropku wywołujemy konstruktor nadklasy.<br>- Jak korzystamy z wielodziedziczenia, to konstruktory nadklas są wywoływane zgodnie z kolejnością w liście inicjalizacyjnej<br><br>- **Destruktory są wywoływane w kolejności odwrotnej do konstruktorów** |
| Problem kruchości interfejsu klasy bazowej – jak zmienimy interfejs klasy bazowej, to prawdopodobnym jest, że będziemy musieli modyfikować kod wielu klas dziedziczących po tej klasie bazowej | Dziedziczenie definicji operatora przypisania  też jest dziedziczone. |
| @Override – pozwala zaznaczyć, że chcemy przysłonić daną metodę | Konstruktory i destruktory nie są dziedziczone |
|  | Zamiast pisania, że klasa jest abstrakcyjna, tworzy się **zerowe** **metody wirtualne** (bez definicji:  `virtual int a())` |
## Istota i zastosowania polimorfizmu na przykładzie języków Java i C++

Polimorfizm jest jednym z kluczowych pojęć w programowaniu obiektowym. Polega on na możliwości wywoływania metod o tej samej nazwie na obiektach różnych klas, ale zachowujących się w różny sposób. W języku Java i C++, polimorfizm jest realizowany poprzez dziedziczenie i interfejsy.

W języku Java, polimorfizm jest wykorzystywany poprzez wywoływanie metod z klasy bazowej na obiektach klas pochodnych. Dzięki temu jedna sekcja kodu może pracować z różnymi typami obiektów, bez konieczności tworzenia osobnych sekcji kodu dla każdego typu.

```java
public interface  {
	public void speak();
}

public class Doggo implements Speakable {
	public void speak() {
		System.out.println("woof");
	}
}

public class Gatto implements Speakable {
	public void speak() {
		System.out.println("meow");
	}
}

public class Main {
	public ststic void main (String[] args) {
		List<Speakable> list = new ArrayList<>(); 
		list.add(new Doggo()); 
		list.add(new Gatto());
		
		list.forEach(Speakable::speak);
	}
 }
```

W języku C++, polimorfizm jest realizowany poprzez przeciążanie operatorów i funkcji wirtualnych. Funkcje wirtualne są funkcjami, które są zdefiniowane w klasie bazowej, ale ich implementacja jest różna w klasach pochodnych. To pozwala na wywoływanie odpowiedniej implementacji w zależności od typu obiektu.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

class Animal {
protected:
    int age;

public:
    Animal(int _age) : age(_age) {}
    virtual void speak() const = 0;
    int getAge() const { return age; }

    // Overriding less-than operator to compare animals by age
    bool operator<(const Animal& other) const {
        return age < other.age;
    }
};

class Doggo : public Animal {
public:
    Doggo(int _age) : Animal(_age) {}
    void speak() const override { std::cout << "woof\n"; }
};

class Gatto : public Animal {
public:
    Gatto(int _age) : Animal(_age) {}
    void speak() const override { std::cout << "meow\n"; }
};

int main() {
    std::vector<Animal*> animals;
    animals.push_back(new Gatto(3));
    animals.push_back(new Doggo(5));
    animals.push_back(new Gatto(1));

    // Sort animals by age
    std::sort(
	    animals.begin(),
	    animals.end(), 
	    [](const Animal* a, const Animal* b) {return *a < *b;}
	);

    // Output sorted animals
    for (const auto& animal : animals) {
        std::cout << "Age: " << animal->getAge() << ", ";
        animal->speak();
    }

    // Free allocated memory
    for (auto animal : animals) {
        delete animal;
    }

    return 0;
}
```

## Użycie tablic oraz innych struktur danych w Javie i C++. Java Collections Framework.
Tablica jest podstawową strukturą danych w Java i C++, pozwala na przechowywanie wielu elementów **tego samego typu**. W Java tablice są obiektami, które można tworzyć za pomocą operatora new i określając rozmiar tablicy.

Java Collections Framework (JCF) to zestaw interfejsów, klas i algorytmów, które umożliwiają programistom przechowywanie i przetwarzanie danych w sposób skuteczny i elastyczny. Ponadto JCF zawiera algorytmy, takie jak sortowanie i wyszukiwanie, które umożliwiają programistom na łatwe i szybkie wykonywanie częstych operacji na danych.
Główne komponenty JCF to interfejsy takie jak
- Collection, 
- List, 
- Set 
- Map

które definiują operacje, które muszą być wspierane przez wszystkie klasy kolekcji. JCF zawiera również gotowe implementacje tych interfejsów:
- ArrayList,
- HashSet,
- HashMap.
---
W C++ tablice są definiowane jako elementy statyczne lub dynamiczne, które można alokować na stosie lub na stercie.

Podczas inicjacji tablicy możemy z góry określić elementy jakie zawiera tablica.
**Tablice statyczne** nie dają nam możliwości decydowania o ich wymiarach podczas działania programu.
```c++
int my_array[5] = { 10, 11, 12, 13, 14};
```

**Deklarując tablicę dynamiczną** należy zadeklarować wskaźnik tego samego typu co elementy tablicy. Następnie rezerwujemy miejsce w pamięci o określonym typie (takim samym jak wskaźnik). Służy do tego rozkaz _new_. **Tablicy dynamicznej** używamy tak samo jak zwykłą tablice statyczną.

```c++
int * my_array = new int[3];

my_array[0] = 11;
my_array[1] = 12;
my_array[2] = 13;

delete [] my_array;
```

Każdy dynamiczny obiekt utworzony podczas działania programu należy na końcu  usunąć poleceniem _delete_. Dzięki użyciu tablicy dynamicznej użytkownik ma możliwość decydowania o rozmiarze tablicy podczas działania programu:

```c++
int size;

cout << "Define size:" << endl;
cin >> size;

int * my_array = new int[size];

delete [] my_array;
```

W C++ popularne struktury danych to:
- Wektory (std::vector)
- Listy (std::list)
- Kolejki (std::queue, std::priority_queue)
- Stosy (std::stack)
- Mapy (std::map)
- Zbiory (std::set)

## Programowanie współbieżne ? mechanizmy i narzędzia na przykładzie języka Java.
> [!info] Proces
> Wykonujący się program wraz z dynamicznie przydzielanymi mu przez system zasobami (pamięcią operacyjną, plikami itp.) + ewentualnie innymi kontekstami wykonania programu (np. obiektami tworzonymi przez program)

> [!info] Wątek 
> Sekwencja działań, która może wykonywać się równolegle z innymi sekwencjami działań w kontekście danego procesu.

Programowanie współbieżne to styl programowania, w którym wiele zadań jest wykonywanych jednocześnie. Celem jest zwiększenie wydajności programu poprzez wykorzystanie wielu rdzeni procesora i jednoczesne wykonywanie kilku zadań. W języku Java programowanie współbieżne jest realizowane za pomocą wielu mechanizmów i narzędzi.

Mechanizmy:
- Wątki (Threads): Są to niezależne części programu, które są wykonywane jednocześnie. W Java można tworzyć wątki za pomocą klasy Thread lub implementując interfejs Runnable.
- Synchronizacja (Synchronization): Mechanizm, który zapewnia, że tylko jeden wątek jest w stanie dostępu do danego zasobu w danym momencie.
-  Wait/Notify: Mechanizm, który pozwala na komunikację między wątkami i współdzielenie danych. Wątek, który chce uzyskać dostęp do zasobu, wstrzymuje swoje wykonanie do czasu, gdy inny wątek udostępni ten zasób.

### Klasa Thread z interfejsu Runnable
Aby stworzyć własny wątek w Java, należy stworzyć klasę, która implementuje interfejs Runnable i zawiera metodę run().

```java
class MyThread extends Thread {
	public void run () {
		// code to execute
	}
}

class Main {
	public static void main(String[] args) {
		MyThread t = new MyThread();
		t.start();
	}
}
```

- Kiedy program wywołuje metodę start(), tworzony jest nowy wątek, a następnie wykonywana jest metoda run().
- Jeśli bezpośrednio wywołamy metodę run(), wówczas nie zostanie utworzony żaden nowy wątek, a metoda run() zostanie wykonana jako normalne wywołanie metody w samym bieżącym wątku wywołującym i nie będzie miała miejsca żadna wielowątkowość
- Wątek możemy „usypiać” na dany czas wywołując metodę sleep. 
- Koniec pracy wątku następuje po wywołaniu metody stop lub interrupt (w przypadku gdy wątek może być kontrolowany przez ExecutorService)
###  Synchronizacja wątków
-  Słowo kluczowe **synchronized** przy metodzie, który chroni przed równoczesnym działaniem wątków na tym samym obiekcie. Jak wątek wywołuje metodę ze słowem sychronized na rzecz jakiegoś obiektu, to "rygiel" tego obiektu jest zamykany (inne wątki muszą czekać aż ten pierwszy wykona tę metodę)
- **Bloki synchronizowane** – w momencie, gdy wątek wchodzi w ten blok, "rygiel" obiektu lock jest blokowany. Wszystkie wątki, które chcemy synchronizować, muszą mieć ten sam obiekt lock w tym miejscu

--- start-multi-column: ExampleRegion1  
```column-settings  
number of columns: 2    
```

```java
synchronized void transferMoney(
	BigDecimal amount, 
	Account fromAccount,
	Account toAccount,
) throws InsufficientFundsException {
  if(fromAccount.balance() >= amount) {
    fromAccount.reduce(amount);
    toAccount.add(amount);
  } else {
    throw new InsufficientFundsException();
  }
}
```

--- end-column ---

```java
void transferMoney(
	BigDecimal amount, 
	Account fromAccount,
	Account toAccount,
) throws InsufficientFundsException {
  synchronized(this) {
    if(fromAccount.balance() >= amount) {
      fromAccount.reduce(amount);
      toAccount.add(amount);
    } else {
      throw new InsufficientFundsException();
    }
  }
}
```

--- end-multi-column

### Koordynacja wątków

>[!info] Koordynacja wątów
>Działania mające na celu zapewnienie współdziałania wątków (m. in. w konkretnej kolejności)

Metody do koordynacji wątków:
-` wait()` – wątek czeka na wydarzenie, które ma się wydarzyć w innym wątku (jak użyjemy go w sekcji krytycznej, to rygiel jest zwalniany), możemy też podać maksymalny czas czekania. Tak jak sleep, rzuca ona `InterruptedException`
- `notify()` – powiadamia konkretny jeden inny wątek o wydarzeniu, co kończy jego czekanie (wątek czeka na danym obiekcie)
- `notifyAll()` – to samo co notify, ale powiadamia wszystkie czekające wątki (zazwyczaj tego się używa, bo nie wiadomo jaki wątek obudzi samo notify)

### Executor 
**Executor** – interfejs do zarządzania wątkami (odseparowanie zadań do wykonania od mechanizmów tworzenia i uruchamiania wątków) – ma metodę void execute(Runnable) – do tworzenia i uruchamiania wątków

Domyślne klasy implementujące Executor:
- Executors.newSingleThreadExecutor() – po kolei uruchamia podane mu zadania w jednym wątku
- Executors.newFixedThreadPool() – dysponuje pulą wątków o określonym maksymalnym rozmiarze
- `Executors.newCachedThreadPool()` – pula o dynamicznym rozmiarze
- `Executors.newScheduled()` – tworzy i wykonuje wątki w określonym czasie i z określoną częstotliwością

`ExecutorService`  - interfejs rozszerzający Executor, ma metody do zamykania Wykonawcy wątków (tak, że nie będzie się dało mu podać nowych zadań do wykonania):
- `shutdown()` – zamyka wykonawcę, ale pozwala dokończyć się już uruchomionym wątkom
- `shutdownNow()` – zamyka wykonawcę i przerywa wszystkie uruchomione wątki
## Typy i metody sparametryzowane (generics) w Javie. Szablony  (templates) w C++. 
## Lambda-wyrażenia i interfejsy funkcyjne w języku Java.

>[!info] **Interfejs funkcyjny** – taki, który zawiera tylko jedną abstrakcyjną metodę (SAM – Single Abstract Method)

Każde Lambda-wyrażenie odpowiada jakiemuś interfejsowi funkcyjnemu i jego typ jest wyznaczany przez rodzaj tego interfejsu

Lambda-wyrażenia są zdefiniowane za pomocą składni:
(lista parametrów) -> {ciało wyrażenia}
- ciałem może być jedno wyrażenie lub blok instrukcji w nawiasach klamrowych  
- jeżeli mamy tylko jeden parametr, to można pominąć nawias, możemy też pomijać typy parametrów jeśli mogą być one określone przez kompilator
- 
```java
import java.util.ArrayList;

public class Main {
  public static void main(String[] args) {
    ArrayList<Integer> numbers = new ArrayList<Integer>();
    numbers.add(5);
    numbers.add(9);
    numbers.add(8);
    numbers.add(1);

	int[] sum = {0}; // Using an array to allow modification inside lambda
	numbers.forEach((n) -> sum[0] += n);

	System.out.println(sum[0]);
  }
}
```
## Przetwarzanie strumieniowe (środki pakietu java.util.stream).
>[!info]  Strumienie 
>Należy rozumieć je jako abstrakcję, która pozwala uprościć przetwarzanie danych. Nie należy ich mylić z kolekcjami, gdyż nie posiadają możliwości przechowywania ani zapisywania danych. Za każdym razem, gdy skończymy przetwarzanie informacji musimy skorzystać np. Z któregoś interfejsu kolekcji.
>
> Ważną cechą strumieni jest brak ingerencji w źródło. W związku z tym metody, które np. filtrują elementy po jakiejś cesze pomniejszając wyjściowy zbiór, tworzą nowy strumień.

>[!info] Potok – ma swoje źródło (może nim być: kolekcja, tablica, plik, napis…), kolejne wykonywane operacje i kończy się redukcją – finalnym efektem w postaci wartości lub zestawu wartości

Rodzaje operacji w potoku:
- **Pośrednie** – dające w wyniku inny strumień (np. operacje map i filter), te dzielą się na:
- **Bezstanowe** – niewymagające od strumienia wiedzy o wartościach poprzednio przetwarzanych elementów (np. filter, forEach) – skupiają się tylko na aktualnym elemencie
- **Stanowe** – wymagają od strumienia pamiętania stanów innych od, od akurat przetwarzanego, elementów (np. sortowanie elementów strumienia)
	- **Terminalne** – kończące przetwarzanie strumienia (collect, forEach)
	- **Skracające** (short-circuit) – takie, które powodują, że wcześniejsze w potoku operacje pośrednie kończą działanie, gdy rezultat operacji skracającej jest jasny. Mogą być zarówno pośrednie jak i terminalne

Cechy operacji strumieniowych:
- **Operacje pośrednie są leniwe** – nie są wykonywane i nie generują żadnych wartości dopóki nie zostanie wywołana jakaś operacja terminalna. Elementy strumienia są przetwarzane tylko w zakresie, jaki jest potrzebny do uzyskania wymaganego wyniku
- **Generatory i  iteratory** – specjalne operacje, które generują elementy strumienia ad hoc – takie strumienie mogą być nieskończone
- **Mogą być przetwarzane równolegle**
-  Wykorzystują lambda-wyrażenia

## Narzędzia programowania operacji wejście-wyjścia w języku Java.
Java posiada bogatą bibliotekę narzędzi do programowania operacji wejścia-wyjścia (I/O). W pakiecie java.io znajdują się klasy i interfejsy, które umożliwiają programistom na odczyt i zapis danych do plików, strumieni i innych urządzeń wejścia-wyjścia.
Niektóre z najważniejszych narzędzi I/O w języku Java to:
- Klasa File: umożliwia programistom na pracę z plikami i katalogami na dysku twardym
- Klasa BufferedReader i BufferedWriter: umożliwiają odczyt i zapis danych z i do pliku w sposób efektywny, poprzez buforowanie danych.
- Klasa PrintWriter: umożliwia programistom na zapis danych do pliku w sposób łatwy i przejrzysty.
- Klasa InputStream i OutputStream: są to abstrakcyjne klasy bazowe, które definiują interfejs do odczytu i zapisu danych z i do strumieni.
- Klasa Serialization: umożliwia programistom na serializację i deserializację obiektów, co pozwala na przechowywanie stanu obiektu w pliku lub przesyłanie go przez sieć.