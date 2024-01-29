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
> - $(x, y) \in \rho$ i mówimy, że para $(x, y)$ należy do relacji \rho, albo piszemy
> - $x \: \rho \: y$ i wtedy mówimy, że element $x$ jest w relacji $\rho$ z elementem $y$, dla $x \in X$ oraz $y \in Y$ .

#### Własności relacji
Rozważamy relację $\rho \subseteq X \times X$ dla dowolnego zbioru $X$.
- **zwrotność** Relacja $\rho$ jest zwrotna, $\Longleftrightarrow$ dla każdego $x \in X$ zachodzi $x \: \rho \: x$. Innymi słowy, zwrotność relacji oznacza, że każdy element jest w relacji ze sobą.
- **symetria** Relacja $\rho$ jest symetryczna, $\Longleftrightarrow$ dla dowolnych $x, y \in X$ jeśli $x \: \rho \: y$, to $y \rho x$. Intuicyjnie, symetria relacji oznacza, że możemy zamienić $x$ z $y$ w parze $(x, y)$ o ile w ogóle $(x, y) \in \rho$. Tak więc kolejność występowania elementów w relacji nie ma tutaj znaczenia.
- **antysymetria** Relacja $\rho$ jest antysymetryczna, $\Longleftrightarrow$ dla dowolnych $x, y \in X \text{ jeśli } x \: \rho \: y \text{ oraz } y \: \rho \: x, \text{ to } x = y$. Tak więc antysymetria relacji oznacza, że kolejność występowania różnych elementów w relacji jest istotna. To znaczy, że dla x 6 = y albo $x \: \rho \: y$, albo $y \: \rho \: x$, albo nie zachodzi ani jedno, ani drugie. 
- **przechodniość** Relacja $\rho$ jest przechodnia, $\Longleftrightarrow$ dla dowolnych $x, y, z \in X$ jeśli $x \: \rho \: y$ oraz $y \: \rho \: z$, to również $x \: \rho \: z$.
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
## Twierdzenie Bayesa. 
## Testowanie hipotez statystycznych. 
## Wyznaczanie przedziałów ufności.
