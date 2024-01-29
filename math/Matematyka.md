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


## Całkowanie przez podstawienie, czyli zamianę zmiennej



$$\int x \log x \,dx =
\left[
  \begin{alignedat}{2}
  u       &= \log x             \quad & \,dv &= x \,dx \\
  \,du &= \frac{1}{x} x \,dx \quad & v &= \frac{x^2}{2}
  \end{alignedat}\,
\right]
=
\frac{x^2}{2}\log x - \int \frac{x^2}{2}\frac{1}{x} \,dx
$$
## Wielomian i szereg Taylora funkcji rzeczywistej. 
## Układy równań liniowych: różne metody rozwiazywania, liczba rozwiązań. 
## Wartości własne macierzy i ich zastosowanie w informatyce.
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
| A   | 0    | 1    | 0    | 1    |
| B   | 0    | 0    | 1    | 0    |
| C   | 1    | 0    | 0    | 0    |
| D   | 0    | 0    | 0    | 0    |


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
## Zasada indukcji matematycznej. 
## Twierdzenie Bayesa. 
## Testowanie hipotez statystycznych. 
## Wyznaczanie przedziałów ufności.
