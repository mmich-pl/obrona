## Podstawowe cechy relacyjnych baz danych.
Relacyjna baza danych to rodzaj bazy danych, który pozwala przechowywać powiązane ze sobą elementy danych i zapewnia do nich dostęp.

Są oparte na modelu relacyjnym — jest to prosty i intuicyjny sposób przedstawiania danych w tabelach. Każdy wiersz tabeli jest **rekordem** z **unikatowym identyfikatorem** nazywanym **kluczem**. Kolumny tabeli zawierają **atrybuty danych**, a każdy rekord zawiera zwykle wartość dla każdego atrybutu.
## Podstawowe elementy i znaczenie diagramów związków encji oraz zasady  prawidłowego projektowania schematów bazy danych.
## Mechanizm współbieżności pracy wielu użytkowników w systemie zarządzania bazami danych.
## Podstawowe obiekty, konstrukcje i znaczenie języka SQL.

**Język SQL** (Structured Query Language) jest językiem **danych** , używanym wyłącznie do wykonywania operacji na bazie danych. **Nie jest językiem programowania** – nie zawiera 
struktur programistycznych wymaganych od takich języków (zmienne, instrukcje warunkowe, instrukcje pętli).

### Dialekty SQL
- DQL – Data Query Language - zestaw poleceń **odczytania danych z bazy** – wszystkie polecenia rozpoczynają się od słowa kluczowego SELECT, a ich realizacja nie ma wpływu na stan danych.
- DML – Data Manipulation Language - zestaw poleceń odpowiedzialnych za operowanie danymi.
	- **INSERT** – wpisywanie nowych danych (rekordów) do bazy danych,
	- **UPDATE** – aktualizacja (zmiana) danych już istniejących,
	- **DELETE** – usuwanie danych (rekordów) z bazy.
- DDL – Data Definition Language - zestaw poleceń odpowiedzialnych za operacje na obiektach bazy danych (tabele, widoki, indeksy, procedury, wyzwalacze, bazy)
	- **CREATE** – polecenie utworzenia nowego obiektu bazy danych,
	- **ALTER** – zmiana struktury obiektu już istniejącego,
	- **DROP** – polecenie usunięcia z bazy istniejącego obiektu.
- DCL – Data Control Language- zestaw poleceń odpowiedzialnych za nadawanie uprawnień do operacji na bazie danych
	- **GRANT** – przyznawanie uprawnień do operacji na obiektach bazy danych,
	- **REVOKE** – odebranie uprawnień do operacji na obiektach bazy danych,
	- **DENY** – zabrania operacji na obiektach bazy danych.
	- 
### Instrukcje COMMIT i ROLLBACK
W bazach danych operujemy pojęciem **TRANSAKCJA** pod którym rozumiemy pewien zbiór poleceń DML, które powinny zostać zrealizowane na zasadzie: **wszystkie poprawnie, albo żadna**.
- **COMMIT** – zatwierdź zmiany, które zostały wprowadzone od ostatniego polecenia Commit lub Rollback.
- **ROLLBACK** - wycofaj zmiany, które zostały wprowadzone od ostatniego polecenia Commit lub Rollback.
- 
### Having
**HAVING** jest kolejnym krokiem po **GROUP BY**. W przypadku, gdy w kwerendzie nie użyto **GROUP BY**, **HAVING** ma takie samo zastosowanie jak WHERE

|Where |Having|
|:-:|:-:|
|Klauzula WHERE pozwala zdefiniować warunek, który muszą spełniać rekordy odczytywane z bazy danych.|Klauzula HAVING pozwala zdefiniować warunek, który muszą spełniać rekordy powstałe jako wynik operacji grupowania i obliczenia funkcji podsumowujących.
|Klauzula WHERE może być używana wraz z poleceniami SELECT, INSERT oraz UPDATE | Klauzula HAVING może być używana jedynie z poleceniem SELECT
|W klauzuli WHERE nie można używać funkcji agregujących.| W klauzuli HAVING można używać funkcji agregujących.

### Łączenie tabel w SQL

```tikz 
\usepackage{tikz}
\begin{document}

\def\firstcircle{(0,0) circle (1.5cm)}
\def\secondcircle{(0:2cm) circle (1.5cm)}

\colorlet{circle edge}{blue!50}
\colorlet{circle area}{blue!20}

\tikzset{filled/.style={fill=circle area, draw=circle edge, thick},
    outline/.style={draw=circle edge, thick}}

\begin{tikzpicture}
    \begin{scope}
        \clip \firstcircle;
        \fill[filled] \secondcircle;
    \end{scope}
    \draw[outline] \firstcircle node {$A$};
    \draw[outline] \secondcircle node {$B$};
    \node[anchor=west, xshift=1.5cm, align=center, text width=3cm] at (current bounding box.east) {Inner JOIN - only the things that match on the left and on the right};
    \node[anchor=west, xshift=1.5cm, align=left] at (current bounding box.east) {SELECT *\\ FROM table1\\ INNER JOIN table2 \\ON table1.key = table2.key};
\end{tikzpicture}
\end{document}
```
<br>

```tikz 
\usepackage{tikz}
\begin{document}

\def\firstcircle{(0,0) circle (1.5cm)}
\def\secondcircle{(0:2cm) circle (1.5cm)}

\colorlet{circle edge}{blue!50}
\colorlet{circle area}{blue!20}

\tikzset{filled/.style={fill=circle area, draw=circle edge, thick},
    outline/.style={draw=circle edge, thick}}

\begin{tikzpicture}
    \begin{scope}
        \clip \firstcircle;
        \fill[filled] \secondcircle;
    \end{scope}
    \begin{scope}
        \clip \firstcircle;
        \draw[filled, even odd rule] \firstcircle node {$A$}
                                     \secondcircle;
    \end{scope}
    \draw[outline] \firstcircle
                   \secondcircle node {$B$};
    \draw[outline] \firstcircle node {$A$};
    \draw[outline] \secondcircle node {$B$};
    \node[anchor=west, xshift=1.5cm, align=center, text width=3cm] at (current bounding box.east) {LEFT (OUTER) JOIN - everything on the left + anything on the right that matches};
    \node[anchor=west, xshift=1.5cm, align=left] at (current bounding box.east) {SELECT *\\ FROM table1\\ LEFT JOIN table2 \\ON table1.key = table2.key};
\end{tikzpicture}
\end{document}
```
<br>

```tikz 
\usepackage{tikz}
\begin{document}

\def\firstcircle{(0,0) circle (1.5cm)}
\def\secondcircle{(0:2cm) circle (1.5cm)}

\colorlet{circle edge}{blue!50}
\colorlet{circle area}{blue!20}

\tikzset{filled/.style={fill=circle area, draw=circle edge, thick},
    outline/.style={draw=circle edge, thick}}

\begin{tikzpicture}
    \begin{scope}
        \clip \firstcircle;
        \fill[filled] \secondcircle;
    \end{scope}
    \begin{scope}
        \clip \secondcircle;
        \draw[filled, even odd rule] \secondcircle node {$B$}
                                     \firstcircle;
    \end{scope}
    \draw[outline] \secondcircle
                   \firstcircle node {$A$};
    \draw[outline] \secondcircle node {$A$};
    \draw[outline] \firstcircle node {$A$};
    \node[anchor=west, xshift=1.5cm, align=center, text width=3cm] at (current bounding box.east) {RIGHT (OUTER) JOIN - everything on the rigth + anything on the left that matches};
    \node[anchor=west, xshift=1.5cm, align=left] at (current bounding box.east) {SELECT *\\ FROM table1\\ RIGHT JOIN table2 \\ON table1.key = table2.key};
\end{tikzpicture}
\end{document}
```
<br>

```tikz 
\usepackage{tikz}
\begin{document}

\def\firstcircle{(0,0) circle (1.5cm)}
\def\secondcircle{(0:2cm) circle (1.5cm)}

\colorlet{circle edge}{blue!50}
\colorlet{circle area}{blue!20}

\tikzset{filled/.style={fill=circle area, draw=circle edge, thick},
    outline/.style={draw=circle edge, thick}}

\begin{tikzpicture}
    \draw[filled] \firstcircle node {$A$}
                  \secondcircle node {$B$};
    \node[anchor=west, xshift=1.5cm, align=center, text width=3cm] at (current bounding box.east) {(FULL) OUTER JOIN - everything on the left + everything on the right};
    \node[anchor=west, xshift=1.5cm, align=left] at (current bounding box.east) {SELECT *\\ FROM table1\\ OUTER JOIN table2 \\ON table1.key = table2.key};
\end{tikzpicture}
\end{document}
```


### Funkcje agregujące
- `Count` – liczba wszystkich rekordów, zwykle COUNT(1)
- `Avg` – wartość średnia argumentu
- `Sum` – suma
- `Max` – maksymalna wartość
- `Min` – minimalna wartość

Argumentem tych funkcji może być wyrażenie (odpowiedniego typu) lub **DISTINCT** wyrażenie. Argumentem funkcji **COUNT** może być cokolwiek – liczone są wiersze wchodzące w skład wyniku. Pseudowartości Null nie są brane pod uwagę przy obliczaniu wartości funkcji.

### CASE
Konstrukcja CASE użyta w klauzuli **SELECT** pozwala na zdefiniowanie listy wartości, której poszczególne elementy zostaną użyte w miejsce wyrażenia z  listy **SELECT**, zależnie od jego wartości. Wyrażenie może być albo wartością stałą(simple **CASE**), albo wyrażeniem logicznym (searched **CASE**).

```sql 
SELECT player_name, weight, 
	CASE WHEN weight > 250 THEN 'over 250' 
		 WHEN weight > 200 THEN '201-250' 
		 WHEN weight > 175 THEN '176-200' 
		 ELSE '175 or under' END AS weight_group 
FROM benn.college_football_players
```

## Podstawowe zasady optymalizacji zapytań, w tym rodzaje i znaczenie indeksów w bazie danych.