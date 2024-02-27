## Całka nieoznaczona, oznaczona, zastosowanie i techniki obliczania.

>[!info] Pochodna funkcji
>Nieformalnie miara szybkości funkcji, czyli tempa zmian jej wartości względem zmian jej argumentów.
>
>Niech $y=f(x)$ będzie funkcją rzeczywistą zmiennej rzeczywistej $x$ określoną w otoczeniu punktu $x_{0}$. **Pochodną funkcji** $f(x)$ w punkcie $x_0$ nazywamy granicę (o ile istnieje):
>$$\large \lim_{  \Delta x \to \infty }  {{f(x_{0}+\Delta x) - f(x_{0})}\over {\Delta x}}$$
>jeżeli przyjmiemy, że $x=x_{0}+\Delta x$, to pochodną w punkcie $x_{0}$ można zapisać jako:
>$$\large \lim_{  x \to x_{0} }  {{f(x) - f(x_{0})}\over { x- x_{0}}}$$
>
>Własności pochodnej funkcji:
>- iloczyn pochodnej przez stałą: $(af)'(x)=af'(x)$
>- pochodna sumy funkcji $(f+g)'(x)=f'(x)+g'(x)$
>- pochodna iloczynu funkcji $(fg)'(x)=f'(x)g(x)+f(x)g'(x)$
>- pochodna złożenia funkcji $f'(x)=h'{\big (}g(x){\big )}g'(x),\quad {\text{ dla }}\quad f(x)=h(g(x))$
>- pochodna ilorazu funkcji (_reguła ilorazu_) $\left({\tfrac {f(x)}{g(x)}}\right)'={\frac {f'(x)g(x)-f(x)g'(x)}{g^{2}(x)}},\quad {\text{ o ile }}\quad g(x)\neq 0.$

Funkcja $F(X)$ jest **funkcją pierwotną** funkcji $f(x)$ w przedziale $(a;b)$, jeżeli $F'(x) = f(x)$ dla każdego $x$ z tego przedziału.
Funkcja $f(x)=x^3$ to funkcja pierwotna w stosunku do funkcji $3x^2$ w zbiorze liczb rzeczywistych, ponieważ $f'(x^3)=3x^2$.

### Całka nieoznaczona
**Całką nieoznaczoną** funkcji $f(x)$ nazywamy wyrażenie $F(x)+C$. Całkę funkcji $f(x)$ oznaczamy następująco: $\int_{}^{} f(x) \,dx = F(x) + C$.

$$\int  x^2 \, dx = \frac{x^{2+1}}{2+1} + C = \frac{x^3}{3}+C $$

### Całka oznaczona
Jeżeli $F(x)$ jest funkcją pierwotną funkcji $f(x)$ ciągłej w danym przedziale $[x_{1}, x_{2}]$, to różnicę funkcji pierwotnych $F(x_{1})$ i $F(x_{2})$ nazywamy **całką oznaczoną** dla funkcji $f$ od $x_{1}$ do $x_2$.

$$ \int ^{x_{2}}_{x_{1}} f(x) \, dx = F(x_{2}) - F(x_{1})$$

$$\int ^{3}_{1} x^2\, dx = \left[ \frac{x^3}{3} \right]^{3}_{1} = 9 - \frac{1}{3} = \frac{26}{3}$$
### Całkowanie przez podstawienie, czyli zamianę zmiennej
Całkowanie przez podstawienie stosujemy, gdy wśród funkcji podcałkowej potrafimy wyodrębnić pewną funkcję i jej pochodną.
$$\int x \log x \,dx =
\left|
  \begin{alignedat}{2}
  u       &= \log x             \quad & \,dv &= x \,dx \\
  \,du &= \frac{1}{x} x \,dx \quad & v &= \frac{x^2}{2}
  \end{alignedat}\,
\right|
=
\frac{x^2}{2}\log x - \int \frac{x^2}{2}\frac{1}{x} \,dx
$$

### Całkowanie przez części
Jeżeli funkcje $u$ i $v$ mają na pewnym przedziale $P$ ciągłe pochodne $u'$ i $v'$, to $\large \int f'(x) g(x) \, dx = f(x)g(x) - \int f(x) g'(x) \, dx$ na tym przedziale.

$$\begin{align}
\int x \ln x \,dx &=
\left|
  \begin{alignedat}{2}
  g(x)    &= \ln x    \quad & f'(x) &= x \\
  \,g'(x) &= \frac{1}{x} \quad & f(x)&= \frac{x^2}{2}
  \end{alignedat}\,
\right|\\
&=
\frac{x^2}{2}\ln x - \int \frac{x^2}{2}\frac{1}{x} \,dx \\&= \frac{1}{2}x^2\ln x - \frac{1}{2}\int x \, dx \\&= \frac{1}{2}x^2x\ln x-\frac{1}{4}x^2+c
\end{align}$$

### Metoda prostokątów
Dzielimy dany przedział $**[a, b]**$ na $n$ odcinków. W każdym odcinku wyliczamy wartości funkcji dla argumentów z początku i końca odcinka. Uśredniony wynik to wysokość prostokąta o podstawie równej długości odcinka.
### Metoda trapezów
Przedział całkowania dzielimy na $n$ równych odcinków. Następnie obliczamy wartości funkcji $f(x)$ w punktach $a$ i $b$ oraz w punktach, które są końcami dwóch odcinków. Wtedy całkę obliczamy następująco:
$$\int ^a_{b} f(x) \, dx \approx h\left( \frac{f(a)}{2} + \sum_{i=2}^n f(x_{i}) + \frac{f(b)}{2} \right)$$
### Zastosowanie całek
- obliczanie pól figur płaskich
- obliczanie długości łuku krzywej
- obliczanie pola powierzchni bryły obrotowej
- obliczanie pracy wykonywanej przez zmienną siłę
## Wielomian i szereg Taylora funkcji rzeczywistej. 
**Szereg Taylora to wielomian, który przybliża funkcję** w bliskim otoczeniu. Przybliżenie to **dotyczy dowolnego punktu** $x$, a nie tylko jednego konkretnego i wyróżnionego punktu. Wzór Taylora jest bardzo ogólny i **opisuje funkcję jako całość**.

**Definicja**
Jeśli funkcja $f$ ma w punkcie $x_{0}$ pochodną rzędu $k$, to **wielomianem Taylora rzędu $k$** funkcji $f$ w $x_0$ nazywamy wielomian

$$\begin{align}
T_{x_{0}} &= f(x_{0}) + \frac{f'(x_{0})}{1!}(x-x_{0}) + \dots + \frac{f^{(k)}(x_{0})}{k!}(x-x_{0})^k \\ \\
&= f(x_{0}) + \sum^{k-1}_{i=1}\frac{f^{(i)}(x_{0})}{i!}(x-x_{0})^i
\end{align}
$$
W szczególnym przypadku gdy $x_{0} =0$ wielomian
$$T_{0}(x) = f(0)+\frac{f'(0)}{1!}x+\dots+\frac{f^{(k)}(0)}{k!}x^k$$
nazywamy **wielomianem MacLaurina rzędu $k$ funkcji $f$.**

**Wzór Taylora z resztą w postaci Lagrange'a**

Jeśli funkcja $f$
1. ma ciągłą pochodną rzędu _n-1_ w przedziale $[x_{0}, x]$
2. ma pochodną rzędu n w przedziale otwartym $(x_{0}, x)$
to istnieje punkt $c \in (x_{0},x)$, taki że:
$$f(x)= T_{x_{0}}(x) + R_{n}(x)= f(x_{0}) + \sum^{k-1}_{i=1}\frac{f^{(i)}(x_{0})}{i!}(x-x_{0})^i + R_{n}(x)$$
gdzie $\large R_{n}=\frac{f^{(n)}(c)}{n!}(x−x_{0})^n$ dla pewnego $c \in (x_{0}, x)$.

Pomijając we wzorze Taylora resztę $R_{n}(x)$ otrzymujemy w otoczeniu punktu $x_{0}$ przybliżenie funkcji $f$ wielomianem stopnia (co najwyżej) $n-1$. n-ta reszta z wzoru Taylora to po prostu liczba wskazująca na _błąd przybliżenia liczby $f(x)$ liczbą_ $T_{x_{0}}(x)$
## Układy równań liniowych: różne metody rozwiązywania, liczba rozwiązań. 

### Wzory Cramera
Możemy ich użyć gdy:
- liczba równań jest równa liczbie niewiadomych
- wyznacznik główny macierzy jest różny od 0
	- W przeciwnym przypadku, gdy $det ( a 1 , … , a n ) = 0$ układ jest
		- _sprzeczny_ (nie ma rozwiązań), gdy choć jeden wyznacznik we wzorach Cramera zawierający jest różny od zera;
		- _nieoznaczony_ (ma więcej niż jedno rozwiązanie) lub sprzeczny, gdy wszystkie wyznaczniki we wzorach Cramera zawierające są równe zeru.

$W$ - wyznacznik główny
$W_{x}, W_{y}, W_{z}, \dots$ - wyznaczniki, w których współczynniki przy $x,y,z,\dots$ zastępujemy wyrazami wolnymi

$$
\begin{align*}
&\begin{cases}
2x+5y+3z = 5  \\[.75em]
4x+2y+5z = 4   \\[.75em]
3x+8y+4z = 9   \\[.75em]
\end{cases}   \\[1.25em]


W = &\begin{bmatrix} 
 2 & 5 & 3\\
 4 & 2 & 5\\
 3 & 8 & 6 \\
\end{bmatrix} = 9 \\[1.25em]

W_{x} = \begin{bmatrix} 
 5 & 5 & 3\\
 4 & 2 & 5\\
 9 & 8 & 6 \\
\end{bmatrix} = 27 \: \: \: \: \: \: \: \:

W_{y} = &\begin{bmatrix} 
 2 & 5 & 3\\
 4 & 4 & 5\\
 3 & 9 & 6 \\
\end{bmatrix} = 9 \: \: \: \: \: \: \: \:

W_{z} = \begin{bmatrix} 
 2 & 5 & 5\\
 4 & 2 & 4\\
 3 & 8 & 9 \\
\end{bmatrix} = -18\\[1.25em]

&\begin{cases}
x = \frac{W_{x}}{W} = \frac{27}{9} = 3  \\[.75em]
y = \frac{W_{y}}{W} = \frac{9}{9} = 1  \\[.75em]
z = \frac{W_{z}}{W} = \frac{-18}{9} = -2  \\[.75em]
\end{cases}   \\[1.25em]
\end{align*} 
$$

### Metoda Gaussa
>[!info] Rząd macierzy
>Chcąc obliczyć rząd macierzy musimy znaleźć największą macierz, której wyznacznik jest różny od zera, wielkość tej niezerowej macierzy będzie szukaną wartością, czyli jeśli największą macierzą, której wyznacznik jest różny od zera jest macierz 3x3 to rząd macierzy jest równy 3.

#### Twierdzenie Kroneckera-Capellego
To twierdzenie jest nam pomocne przy określaniu **liczby rozwiązań** układu równań liniowych. W przeciwieństwie do Twierdzenia Cramera, tutaj układ równań może być dowolny (tzn. liczba równań i niewiadomych nie muszą być sobie równe).

$$
\begin{align*}
&\begin{cases}
x+2y-z = 5  \\[.75em]
3x+4y+z = 9   \\[.75em]
2x-2y+3z = 1   \\[.75em]
\end{cases}   \\[1.25em]
&A = \left[
\begin{array}{ccc}
1 & 2 & -1  \\
3 & 4 & 1  \\
2 & -2 & 3  \\
\end{array}
\right]\\[1.2em]
&U = \left[
\begin{array}{ccc|c}
1 & 2 & -1 & 5 \\
3 & 4 & 1 & 9 \\
2 & -2 & 3 & -1 \\
\end{array}
\right]
\end{align*}
$$
 Warunkiem koniecznym i wystarczającym na to, aby układ miał rozwiązanie jest równość rzędów macierzy głównej $A$ i macierzy uzupełnionej $U$ czyli: $r(A)=r(U)$.
- Jeśli $r(A)=r(U)=n$ , gdzie $n$ jest liczba niewiadomych, to układ ma dokładnie jedno rozwiązanie. 
- Jeśli $r(A)=r(U)<n$, to układ ma nieskończenie wiele rozwiązań zależnych od $n-r$ parametrów.
- Jeśli $r(A) \neq r(U)$, to układ nie ma rozwiązań i nazywa się układem sprzecznym. 
---
1. Układ równań jest zapisywany pod postacią macierzy współczynników
2. Następuje przekształcenie wierszy za pomocą operacji elementarnych
	- dodanie lub odjęcie do dowolnego wiersza pomnożonego przez liczbę lub w niezmienionej postaci
	- pomnożenie dowolnego wiersza przez liczbę inną niż 0
	- zamiana miejscami dwóch wierszy
3. Przekształcenia mają na celu otrzymanie macierzy schodkowej czyli spełniającej warunki
	- na schodkach są tylko liczby różne od 0
	- pod schodkami są tylko 0
4. Z otrzymanej macierzy układane są rozwiązania równań zaczynając od ostatniego wiersza.
$$
\begin{align*}
&\begin{cases}
x+2y-z = 5  \\[.75em]
3x+4y+z = 9   \\[.75em]
2x-2y+3z = 1   \\[.75em]
\end{cases}   \\[1.25em]


&\left[
\begin{array}{ccc|c}
1 & 2 & -1 & 5 \\
3 & 4 & 1 & 9 \\
2 & -2 & 3 & -1 \\
\end{array}
\right]

\begin{array}{c}
~\\
-3w_{1} \\
-2w_{1} \\
\end{array} \longrightarrow

\left[
\begin{array}{ccc|c}
1 & 2 & -1 & 5 \\
0 & -2 & 4 & -6 \\
0 & -6 & 5 & -11 \\
\end{array}
\right]

\begin{array}{c}
~\\
~ \\
* -1 \\
\end{array} \longrightarrow \\[1.25em]

&\left[
\begin{array}{ccc|c}
1 & 2 & -1 & 5 \\
0 & -2 & 4 & -6 \\
0 & 6 & -5 & 11 \\
\end{array}
\right]

\begin{array}{c}
~\\
~ \\
+3w_{2} \\
\end{array} \longrightarrow

\left[
\begin{array}{ccc|c}
1 & 2 & -1 & 5 \\
0 & -2 & 4 & -6 \\
0 & 0 & 7 & -7 \\
\end{array}
\right]\\[1.25em]



&\begin{cases}
x+2y-z=5 \Rightarrow x=2 \\[.75em]
-2y + 4z = -6 \Rightarrow y = 1 \\[.75em]
7z = -7 \Rightarrow z = -1 \\[.75em]
\end{cases} 
\end{align*} 
$$
## Wartości własne macierzy i ich zastosowanie w informatyce.

>[!info] Endomorfizm liniowy – przekształcenie liniowe przestrzeni $V$ zgodnie ze wzorem $f: V \rightarrow V$ (przejście w taką samą przestrzeń).  Macierz endomorfizmu jest macierzą kwadratową  

$v \in V$ – **wektor własny** endomorfizmu $f$, jeśli $v \neq 0$ oraz istnieje $\lambda \in R$ takie, że $f(v) = \lambda*v$ 
W tym równaniu, $\lambda$ – **wartość własna** endomorfizmu $f$.

Przykład endomorfizmu: $f: R^3 \rightarrow R^3$
Dla $f([1,1,1]) = [5,5,5] = 5*[1,1,1]$ -> wektor własny to $[1,1,1]$, a wartość własna to $5$.

Zastosowanie wartości własnych w informatyce:
- Rankingowanie stron internetowych w wyszukiwarce Google (algorytm PageRank – linki między stronami i wagi tych linków są zapisane w macierzach, wartość własna przyspiesza liczenie tych wag)
- PCA (principal component analysis – do zmniejszania wymiarowości danych używanych przy uczeniu maszynowym, przy zmniejszaniu wymiarów, tworzona jest macierz kowariancji zmiennych (powinienem to opisać w zagadnieniu 9 lub 10)  po znalezieniu jej wektora własnego, wektor ten wyznacza kierunek hiperpłaszczyzny, na którą rzutujemy atrybuty danych)
- Algorytm partycji grafów (dzielenie grafów na kilka mniejszych, które są ze sobą połączone pojedynczymi przejściami, druga najmniejsza wartość własna w macierzy przejść daje nam dolną granicę optymalnego przecięcia grafu)

## Grafy i ich typy, metody reprezentacji grafów. 
**Graf** –  struktura matematyczna służąca do przedstawiania i badania relacji między obiektami. W uproszczeniu graf to zbiór wierzchołków, które mogą być połączone krawędziami w taki sposób, że każda krawędź kończy się i zaczyna w którymś z wierzchołków.

Wierzchołki grafu mogą być numerowane i czasem stanowią reprezentację jakichś obiektów, natomiast krawędzie mogą wówczas obrazować relacje między takimi obiektami. Wierzchołki należące do krawędzi nazywane są jej końcami.

**Droga**(ścieżka): naprzemiennych wierzchołków i krawędzi $v_{0}, e_{0}, v_{1}, \dots v_{k-1}, e_{k}, v_{k}$, taki, że krawędź $e_{k}$ zawsze łączy wierzchołki $v_{k-1}$ i $v_{k}$.

**Cykl** jest ścieżką, która rozpoczyna się i kończy w tym samym wierzchołku. Aby stwierdzić, czy graf zawiera jakiś cykl, przechodzimy go algorytmem DFS. Jeśli w trakcie przechodzenia natrafimy na wierzchołek już odwiedzony, a nie jest to wierzchołek, z którego przyszliśmy, to graf jest cykliczny.
### Rodzaje grafów
#### Graf nieskierowany  
**Graf nieskierowany**  to zbiór wierzchołków i krawędzi, wierzchołki należące do krawędzi są  jej końcami.
```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,3) {B};
    \node (C) at (2.5,4) {C};
    \node (D) at (2.5,1) {D};
    \node (E) at (2.5,-3) {E};
    \node (F) at (5,3) {F} ;
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
    \path (A) edge (B);
    \path (B) edge (C);
    \path (A) edge (D);
    \path (D) edge (C);
    \path (A) edge (E);
    \path (D) edge (E);
    \path (D) edge (F);
    \path (C) edge (F);
    \path (E) edge (F); 
\end{scope}
\end{tikzpicture}
\end{document}
```

#### Graf skierowany  
W grafie **skierowanym** krawędzie oznaczane strzałkami pokazują nam konkretny kierunek, w którym możemy poruszać się po grafie.

```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,3) {B};
    \node (C) at (2.5,4) {C};
    \node (D) at (2.5,1) {D};
    \node (E) at (2.5,-3) {E};
    \node (F) at (5,3) {F} ;
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
    \path [->] (A) edge (B);
    \path [->] (B) edge (D);
    \path [->] (B) edge (C);
    \path [->] (A) edge (D);
    \path [->] (D) edge (C);
    \path [->] (A) edge (E);
    \path [->] (D) edge (E);
    \path [->] (D) edge (F);
    \path [->] (C) edge (F);
    \path [->] (E) edge (F); 
\end{scope}
\end{tikzpicture}
\end{document}
```

#### Graf spójny i niespójny
Następnie spójność - graf jest **spójny** jeżeli dla każdej pary wierzchołków istnieje ścieżka, która je łączy.
```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,3) {B};
    \node (C) at (2.5,4) {C};
    \node (D) at (2.5,1) {D};
    \node (E) at (2.5,-3) {E};
    \node (F) at (5,3) {F} ;
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
    \path (A) edge (B);
    \path (D) edge (E);
    \path (D) edge (F);
    \path (E) edge (F); 
\end{scope}
\end{tikzpicture}
\end{document}
```

#### Graf pełny
Graf **pełny** - to taki graf prosty, w którym dla każdej pary wierzchołków istnieje krawędź je łącząca.

```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,3) {B};
    \node (C) at (2.5,4) {C};
    \node (D) at (3,1) {D};    
    \node (E) at (2.5,-3) {E};
    \node (F) at (5,3) {F} ;
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
    \path (A) edge (B);
    \path (A) edge (C);
    \path (A) edge (D);
    \path (A) edge (E);
    \path (A) edge (F);
    \path (B) edge (C);
    \path (B) edge (D);
    \path (B) edge (E);
    \path (B) edge (F);
    \path (C) edge (D);
    \path (C) edge (E);
    \path (C) edge (F);
    \path (D) edge (E);
    \path (D) edge (F);
    \path (E) edge (F);
   
\end{scope}
\end{tikzpicture}
\end{document}
```
#### Graf dwudzielny  
Zbiór wierzchołków **grafu dwudzielnego** można podzielić na dwa rozłączne zbiory tak, że krawędzie nie łączą wierzchołków tego samego zbioru. Jeśli pomiędzy wszystkimi parami wierzchołków należących do różnych zbiorów istnieje krawędź to taki graf nazywamy grafem **pełnym dwudzielnym**.

```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,1.5) {B};
    \node (C) at (0,-1.5) {C};
    \node (D) at (3,1) {D};    
    \node (E) at (3,4.5) {E};
    \node (F) at (3,3) {F} ;
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
    \path (A) edge (D);
    \path (B) edge (E);
    \path (B) edge (F);
    \path (A) edge (F);
    \path (C) edge (D);
   
\end{scope}
\end{tikzpicture}
\end{document}
```

#### Graf z wagami (graf ważony)
To taki graf, w którym każdej krawędzi przypisana jest pewna wartość liczbowa. Wartość ta może oznaczać np. długość krawędzi lub jej przepustowość.
```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,3) {B};
    \node (C) at (2.5,4) {C};
    \node (D) at (2.5,1) {D};
    \node (E) at (2.5,-3) {E};
    \node (F) at (5,3) {F} ;
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
    \path [->] (A) edge node {$5$} (B);
    \path [->] (B) edge node {$3$} (C);
    \path [->] (A) edge node {$4$} (D);
    \path [->] (D) edge node {$3$} (C);
    \path [->] (A) edge node {$3$} (E);
    \path [->] (D) edge node {$3$} (E);
    \path [->] (D) edge node {$3$} (F);
    \path [->] (C) edge node {$5$} (F);
    \path [->] (E) edge node {$8$} (F); 
\end{scope}
\end{tikzpicture}
\end{document}
```

### Sposoby prezentacji
#### Lista krawędzi
Lista krawędzi polega na tym, że mamy listę zawierającą definicję krawędzi. Definicja krawędzi w najprostszej postaci to para wierzchołków. Dla poniższego grafu wyglądałoby to następująco: [(A, B), (C,A), (A,D), (B,C)].

```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,3) {B};
    \node (C) at (2.5,2) {C};
    \node (D) at (2.5,-2) {D};
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
 \path [->] (A) edge (B);
 \path [->] (A) edge (D);
 \path [->] (B) edge (C);
 \path [->] (C) edge (A);
\end{scope}
\end{tikzpicture}
\end{document}
```

#### Lista sąsiedztwa
Lista sąsiedztwa jest listą list. Kolejne indeksy w tej liście odpowiadają wierzchołkom grafu, a pod nimi znajdziemy listę wierzchołków, do których możemy z niego dostać się bezpośrednio. 

Taka struktura sugeruje użycie do grafu skierowanego, ale możemy też zastosować ją w grafach nieskierowanych, tylko trzeba będzie powielić krawędź (żeby z obu wierzchołków dało się dojść do siebie nawzajem).

Dla poniższego grafu wyglądałoby to następująco: [A:[B, D], B:[C], C:[A], D:[]].
```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,3) {B};
    \node (C) at (2.5,2) {C};
    \node (D) at (2.5,-2) {D};
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
 \path [->] (A) edge (B);
 \path [->] (A) edge (D);
 \path [->] (B) edge (C);
 \path [->] (C) edge (A);
\end{scope}
\end{tikzpicture}
\end{document}
```


#### Macierz sąsiedztwa
Jest to macierz o wymiarach ilośćWęzłów$\times$ilośćWęzłów, w której wartości wskazują, czy wierzchołki są ze sobą połączone, czy też nie. W grafach nieważonych zwykle stosujemy wartości 0 (brak krawędzi) i 1 (istnieje krawędź), jednak w przypadku ważonego grafu możemy stosować inne wartości numeryczne i `null` dla braku krawędzi.

Dla poniższego grafu wyglądałoby to następująco: 

|     | A   | B   | C   | D   |
| --- | --- | --- | --- | --- |
| A   | 0   | 1   | 0   | 1   |
| B   | 0   | 0   | 1   | 0   |
| C   | 1   | 0   | 0   | 0   |
| D   | 0   | 0   | 0   | 0   |


```tikz
\usetikzlibrary{arrows.meta}
\begin{document}
\begin{tikzpicture}
\begin{scope}[every node/.style={circle,thick,draw}]
    \node (A) at (0,0) {A};
    \node (B) at (0,3) {B};
    \node (C) at (2.5,2) {C};
    \node (D) at (2.5,-2) {D};
\end{scope}

\begin{scope}[>={Stealth[black]},
              every node/.style={fill=white,circle},
              every edge/.style={draw=black,very thick}]
 \path [->] (A) edge (B);
 \path [->] (A) edge (D);
 \path [->] (B) edge (C);
 \path [->] (C) edge (A);
\end{scope}
\end{tikzpicture}
\end{document}
```

## Relacje binarne, własności i metody reprezentacji. 

### Iloczyn kartezjański zbiorów  
Rozważa się dwa zbiory $X$ i $Y$. Zbiór wszystkich uporządkowanych par elementów należących odpowiednio do tych zbiorów, nazywa się iloczynem (albo produktem) kartezjańskim zbiorów $X$ i $Y$. Iloczyn kartezjański oznacza się jako $X \times Y$. Można to zapisać w następujący sposób: $X \times Y={(x,y): x \in X \text{ i } y \in Y}$.

$$
% determinant form
\begin{align*}
X \times Y = \{1,2,3,4\} \times \{a,b,c\} =\begin{vmatrix}
(1, a) & (1, b) & (1, c)\\
(2, a) & (2, b) & (2, c)\\
(3, a) & (3, b) & (3, c)\\
(4, a) & (4, b) & (4, c)\\
\end{vmatrix}
\end{align*}
$$
Operacja iloczynu kartezjańskiego nie jest przemienna.

### Relacje binarne
>[!info] Relacje binarne
 Relacja binarna (dwuargumentowa) to podzbiór iloczynu kartezjańskiego dwóch zbiorów.
 >
 >Jeśli weźmiemy $A = X \times Y$ , to $W_{A}$,  oznacza pewną własność, a zarazem podzbiór, iloczynu kartezjańskiego $X \times Y$ . 
>
>Ten podzbiór, czyli zbiór par o pewnej własności, to właśnie relacja — relacja pomiędzy pierwszą a drugą zmienną w iloczynie kartezjańskim.
>Relacje będziemy oznaczać grecką literą $\rho$. Także jeśli rozpatrujemy relację \$rho$ pomiędzy elementami zbioru $X$ a elementami zbioru $Y$ , czyli relację w iloczynie kartezjańskim $X \times Y$ , to formalnie $\rho \subseteq X \times Y$.
>
>Piszemy
> - $(x, y) \in \rho$ i mówimy, że para $(x, y)$ należy do relacji $\rho$, albo piszemy
> - $x \: \rho \: y$ i wtedy mówimy, że element $x$ jest w relacji $\rho$ z elementem $y$, dla $x \in X$ oraz $y \in Y$ .

#### Własności relacji
Rozważamy relację $\rho \subseteq X \times X$ dla dowolnego zbioru $X$.
- **zwrotność** Relacja $\rho$ jest zwrotna, $\Longleftrightarrow$ dla każdego $x \in X$ zachodzi $x \: \rho \: x$. Innymi słowy, zwrotność relacji oznacza, że każdy element jest w relacji ze sobą.
- **symetria** Relacja $\rho$ jest symetryczna, $\Longleftrightarrow$ dla dowolnych $x, y \in X$ jeśli $x \: \rho \: y$, to $y \rho x$. Intuicyjnie, symetria relacji oznacza, że możemy zamienić $x$ z $y$ w parze $(x, y)$ o ile w ogóle $(x, y) \in \rho$. Tak więc kolejność występowania elementów w relacji nie ma tutaj znaczenia.
- **antysymetria** Relacja $\rho$ jest antysymetryczna, $\Longleftrightarrow$ dla dowolnych $x, y \in X \text{ jeśli } x \: \rho \: y \text{ oraz } y \: \rho \: x, \text{ to } x = y$. Tak więc antysymetria relacji oznacza, że kolejność występowania różnych elementów w relacji jest istotna. To znaczy, że dla x 6 = y albo $x \: \rho \: y$, albo $y \: \rho \: x$, albo nie zachodzi ani jedno, ani drugie. 
- **przechodniość** Relacja $\rho$ jest przechodnia, $\Longleftrightarrow$ dla dowolnych $x, y, z \in X$ jeśli $x \: \rho \: y$ oraz $y \: \rho \: z$, to również $x \: \rho \: z$.

>[!example]
>Niech X = zbiór wszystkich ludzi (o jasno określonej płci). Dla $x, y \in X$ określamy relację $/rho$ w następujący sposób "$x  \: \rho \: y \Longleftrightarrow x$ jest tej samej płci co $y$".
>- **zwrotność**: Zawsze człowiek $x$ jest tej samej płci co $x$, tzn. $x  \: \rho \: x$, więc relacja jest zwrotna.
>- **symetria**: Jeśli człowiek $x$ jest tej samej płci co człowiek $y$, to również na odwrót, $y$ jest tej samej płci co $x$. Zatem relacja ρ jest symetryczna.
>- **przechodniość**: Załóżmy, że człowiek $x$ jest tej samej płci co $y$ oraz, że $y$ jest tej samej płci co $z$. Wówczas wszyscy $x, y, z$ są tej samej płci, w szczególności $x$ jest tej samej płci co $z$. Zatem relacja ρ jest przechodnia.
#### Sposób reprezentacji
 **Grafowa**
 ```tikz
\usetikzlibrary{positioning,chains,fit,shapes,calc}

\begin{document}

\definecolor{myblue}{RGB}{80,80,160}
\definecolor{mygreen}{RGB}{80,160,80}

\begin{tikzpicture}[thick,
  every node/.style={draw,circle},
  fsnode/.style={fill=myblue},
  ssnode/.style={fill=mygreen},
  every fit/.style={ellipse,draw,inner sep=-2pt,text width=2cm},
  ->,shorten >= 3pt,shorten <= 3pt
]

\begin{scope}[start chain=going below,node distance=7mm]
\foreach \i in {1,2,...,4}
  \node[fsnode,on chain] (f\i) [label=left: x\i] {};
\end{scope}

\begin{scope}[xshift=4cm,yshift=-0.5cm,start chain=going below,node distance=7mm]
\foreach \j in {1,2,...,4}
  \node[ssnode,on chain] (s\j) [label=right: y\j] {};
\end{scope}

\node [myblue,fit=(f1) (f4),label=above:$X$] {};
\node [mygreen,fit=(s1) (s4),label=above:$Y$] {};

\draw (f1) -- (s1);
\draw (f2) -- (s2);
\draw (f3) -- (s3);
\draw (f4) -- (s4);
\end{tikzpicture}

\end{document}
```

**Wykres współrzędnych**
```tikz
\begin{document} 
\begin{tikzpicture}[domain=0:4] 
\draw[very thin,color=gray] (-0.1,-1.1) grid (3.9,3.9); 
\draw[->] (-0.2,0) -- (4.2,0) node[right] {$x$}; 
\draw[->] (0,-1.2) -- (0,4.2) node[above] {$f(x)$}; 
\draw[color=red] plot (\x,{\x}) node[right] {$f(x)=x$};
\end{tikzpicture} \end{document} 
```
**Macierzowa**

$$
\begin{align*}
M_{R} &= (m_{ij})                   \\[.75em]
%
m(i,j) & = \begin{cases}
            1    & (a_{i},b_{j}) \in R        \\[.75em]
            0    & (a_{i},b_{j}) \notin R    \\
           \end{cases}              \\[.75em]
 i &= 1,2,\dots m                   \\[.75em]
 j &= 1,2,\dots n
    \end{align*}
$$

| R | $b_1$ | $b_2$ | $b_3$ |
| ---- | ---- | ---- | ---- |
| $a_1$ | 0 | 1 | 0 |
| $a_2$ | 0 | 0 | 1 |
| $a_3$ | 1 | 0 | 0 |
| $a_4$ | 0 | 0 | 0 |

## Zasada indukcji matematycznej. 
Chcąc udowodnić wzór, w którym zmienna jest liczbą naturalna, najpierw musimy sprawdzić czy jest on prawdziwy, dla chociaż jednego przypadku (początkowego), czyli dla liczby $n$. Jeśli jest to prawdą, to można założyć, że jest to prawdą dla liczby naturalnej $k$, która jest równa lub większa od $n$. Wykorzystując warunek, że wzór jest prawdziwy dla liczby naturalnej $k$, udowadnia się, że wzór jest prawdziwy dla liczby naturalnej $k+1$ (czyli o jeden większej).  
Jest to o tyle genialna metoda, że udowadnia w trzech korkach i sprawdza wszystkie liczby naturalne.

Schemat **indukcji matematycznej**:  
1) udowodnienie prawdziwości twierdzenia dla pewnej liczby naturalnej $n$,  
2) założenie, że twierdzenie jest prawdziwe dla liczby naturalnej 𝑘, takiej że $k \geq n$,  
3) udowodnienie prawdziwości twierdzenia dla $k+1$.
## Twierdzenie Bayesa. 
Tradycyjna metoda obliczania prawdopodobieństwa warunkowego (prawdopodobieństwa zajścia jednego zdarzenia przy zaistnieniu innego zdarzenia) polega na wykorzystaniu wzoru na prawdopodobieństwo warunkowe, obliczeniu łącznego prawdopodobieństwa wystąpienia pierwszego i drugiego zdarzenia w tym samym czasie, a następnie podzieleniu go prawdopodobieństwem wystąpienia drugiego zdarzenia. Jednak prawdopodobieństwo warunkowe można również obliczyć w nieco inny sposób, korzystając z twierdzenia Bayesa.

Obliczając prawdopodobieństwo warunkowe za pomocą twierdzenia Bayesa, należy wykonać następujące kroki:

- Określ prawdopodobieństwo spełnienia warunku B, zakładając, że warunek A jest prawdziwy.
- Określ prawdopodobieństwo, że zdarzenie A będzie prawdziwe.
- Pomnóż oba prawdopodobieństwa przez siebie.
- Podziel przez prawdopodobieństwo wystąpienia zdarzenia B.

Oznacza to, że wzór na twierdzenie Bayesa można wyrazić w następujący sposób:

$$P(A|B) = \frac{P(B|A)*P(A)}{P(B)}$$

## Testowanie hipotez statystycznych. 

>[!info] Hipotezy statystyczne 
> To **dowolne przypuszczenie dotyczące rozkładu populacji**. Formułowanie hipotezy statystycznej rozpoczyna się od zebrania informacji na temat populacji i jej możliwego rozkładu. Dzięki temu możliwe jest zbudowanie zbioru hipotez dopuszczalnych $\Omega$, czyli zbioru rozkładów, które mogą charakteryzować badaną populację. 

**Hipoteza zerowa** – hipoteza, której prawdziwość poddajemy w wątpliwość i która jest testowana celem ewentualnego odrzucenia, oznaczana jako

**Hipoteza alternatywna** ­– hipoteza, która będzie przyjęta, jeśli odrzucimy hipotezę zerową, oznaczana jako  
Hipoteza zerowa i alternatywna mają się wzajemnie wykluczać  
Staramy się udowodnić hipotezę alternatywną, co pozwoli na odrzucenie hipotezy zerowej. **Odrzucenie hipotezy alternatywnej nie oznacza, że hipoteza zerowa jest prawdziwa ani fałszywa** (mówimy wtedy, że „nie możemy odrzucić hipotezy zerowej”)

**Błąd I rodzaju** – błąd polegający na przyjęciu  gdy hipoteza  jest prawdziwa.  
**Poziom istotności testu** – prawdopodobieństwo popełnienia błędu pierwszego rodzaju, oznaczane grecką literą α

**Statystyka testowa** – statystyka, na której podstawie orzekamy prawdziwość , oznaczana dużą literą Z (statystyka to kwantyl danego rozkładu. Z karty wzorów patrzymy na odpowiedni kwantyl, zależny od poziomu istotności, i sprawdzamy, czy nasza statystyka testowa jest od niego większa. To znaczy, że należy ona do zbioru krytycznego). W zależności od typu hipotezy, mamy różne wzory na statystykę testową (mieliśmy do tego kartę wzorów)


**Błąd II rodzaju** – błąd polegający na przyjęciu , gdy hipoteza  jest prawdziwa

Proces testowania hipotez statystycznych składa się z kilku kroków:
- **Formułowanie hipotezy**: Formułuje się hipotezę na temat parametrów populacji na podstawie danych teoretycznych lub wcześniejszych badań.
- **Wybór statystyki testowej**: Wybiera się odpowiednią statystykę testową, która będzie używana do oceny hipotezy.
- **Wybór poziomu istotności**: Wybiera się poziom istotności, który określa, jak wysokie prawdopodobieństwo omyłki jesteśmy gotowi zaakceptować.
- **Otrzymanie danych empirycznych**: Przeprowadza się badanie lub gromadzi dane empiryczne, które będą użyte do testowania hipotezy.
- **Ocena hipotezy**: Porównuje się otrzymane dane empiryczne z wartościami teoretycznymi i ocenia, czy hipoteza jest potwierdzona lub odrzucona.
- **Podejmowanie decyzji**: Na podstawie wyniku testu podejmuje się decyzję, czy hipoteza jest potwierdzona lub odrzucona.
## Wyznaczanie przedziałów ufności.
Przedział ufności jest narzędziem statystycznym, które służy do określenia, jak dokładnie znana jest wartość parametru populacji na podstawie danych empirycznych. Przedział ufności jest określany jako zakres wartości, który z określoną pewnością zawiera prawdziwą wartość parametru populacji.

Wyznaczanie przedziału ufności można wykonać na kilka sposobów, w tym:
- Metoda naiwna: Przedział ufności jest wyznaczany na podstawie otrzymanego rozkładu danych empirycznych i jest oparty na założeniu, że jest on bliski rozkładowi normalnemu
- Metoda bootstrap: W tej metodzie przedział ufności jest wyznaczany na podstawie symulacji danych na podstawie istniejących danych empirycznych.
- Metoda kwantyli: W tej metodzie przedział ufności jest wyznaczany na podstawie kwantyli rozkładu danych empirycznych