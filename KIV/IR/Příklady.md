### Jaccardův koeficient

- měření překryvu dvou množin (dotazu a dokumentu)
- $\displaystyle \text{JACCARD}(A, B) = \frac{|A \cap B|}{|A \cup B|}$

```
Q = IDES OF MARCH
D = CAESAR DIED IN MARCH

JACCARD = 1 / 6
```

### TF-IDF

- $\text{wtf} = 1 + \log_{10} tf$
- $\text{idf} = \log_{10} \left( \frac{N}{df} \right)$
- $\text{tf-idf} = \text{wtf} \cdot \text{idf}$

|         | tf: d1 | tf: d2 | wtf: d1 | wtf: d2 |
| ------- | ------ | ------ | ------- | ------- |
| affect  | 115    | 58     | 3,06    | 2,76    |
| jealous | 10     | 7      | 2,00    | 1,85    |
| gossip  | 2      | 0      | 1,30    | 0,00    |

|         | df  | idf  | tfidf: d1 | tfidf: d2 |
| ------- | --- | ---- | --------- | --------- |
| affect  | 2   | 0,00 | 0,00      | 0,00      |
| jealous | 2   | 0,00 | 0,00      | 0,00      |
| gossip  | 1   | 0,30 | 0,39      | 0,00      |

### Normalizace

$\text{normalizace} = \sqrt{ 3.06^2 + 2.00^2 + 1.30^2 + 0.00^2 } = 3.88$

$\displaystyle \frac{3.06}{3.88} = 0.789$

|      | wtf: d1 | wtf: d2 |
| ---- | ------- | ------- |
| aff  | 0,789   | 0,832   |
| jeal | 0,515   | 0,555   |
| goss | 0,335   | 0,000   |
| wct  | 0,000   | 0,000   |

### Cosine

$\cos(d1, d2) = d1 \cdot d2^T = 0.832 \cdot 0.789 + 0.555 \cdot 0.515 + 0 \cdot 0.335 + 0 \cdot 0 = 0.942$

### Boolean - úprava

$A \cdot (A + B) = AA + AB = A + AB = A$

$(A + B) \cdot (A + C) = AA + AC + BA + BC = A + BC$

$(A + \overline{B} + \overline{C}) \cdot (A + \overline{B} + C) \cdot (A + B + \overline{C}) =$
$(AA + A\overline{B} + AC + \overline{B}A + \overline{BB} + \overline{B}C + \overline{C}A + \overline{CB} + \overline{C}C) \cdot (A + B + \overline{C}) =$
$(A + \overline{B}) \cdot (A + B + \overline{C}) = AA + AB + A\overline{C} + \overline{B}A + \overline{B}B + \overline{BC} =$
$A + \overline{BC}$

### Boolean - dotaz

| term  | docs       |
| ----- | ---------- |
| kočka | 13, 27, 41 |
| pes   | 13, 34     |
| dům   | 27, 34, 55 |

`kočka AND pes =` $\{13, 27, 41\} \cap \{13, 34\} = \{13\}$

`kočka AND NOT pes =` $\{13, 27, 41\} - \{13, 34\} = \{27, 41\}$

`dům AND (NOT kočka OR NOT pes) = dům AND NOT (kočka AND pes) =` $\{27, 23, 55\} - \{13\} = \{27, 23, 55\}$

`dům OR (NOT kočka OR NOT pes) = dům OR NOT (kočka AND pes) = NOT (NOT dům AND kočka AND pes) = UNIVERZUM - (NOT dům AND kočka AND pes) = UNIVERZUM - ((kočka AND pes) - dům) =` $U - \{13\}$

### KD stromy

`x 5,4 ( y 2,6 [ x 3,1 ] ; y 13,3 [ x 10,2 ; x 8,7 ] )`

**Hledáme souseda pro (9, 4)**

|     | node | var | comp  | dir |
| --- | ---- | --- | ----- | --- |
| 1.  | 5,4  | x   | 9 > 5 | →   |
| 2.  | 13,3 | y   | 4 > 3 | →   |
| 3.  | 8,7  | x   | 9 > 8 | →   |

**Backtracking**
- $\text{dist} = \sqrt{ (x_{1}-x_{2})^2 + (y_{1}-y_{2})^2 }$
- $\text{vardist} = |x_{1}-x_{2}|$

|     | node | var | child | var dist | dist | dir |
| --- | ---- | --- | ----- | -------- | ---- | --- |
| 1.  | 8,7  | x   | no    | -        | 3,16 | ↑   |
| 2.  | 13,3 | y   | yes   | 1        | 4,12 | ←   |
| 3.  | 10,2 | x   | no    | -        | 2,24 | ↑   |
| 4.  | 5,4  | x   | yes   | 4        | 4    | -   |

U 2. podle **var y** máme var distance $|4-3| = 1$
- to je menší než aktuálně nejlepší, tedy $1 < 3.16$
- proto prohledáme podstrom

U 4. podle **var x** máme var distance $|9-5| = 4$
- to je větší než aktuálně nejlepší, tedy $4 > 2.24$
- proto neprohledáváme podstrom

Jsme v rootu, nejbližší soused je tedy **(10, 2)**


### LSH

|           | (1, 2) | (2, 3) | (3, 3) | (6, 5) | (7, 8) | (8, 8) | (9, 1) | (4, 2) | (5, 4) |
| --------- | ------ | ------ | ------ | ------ | ------ | ------ | ------ | ------ | ------ |
| h1: x+y-5 | -      | -      | +      | +      | +      | +      | +      | +      | +      |
| h2: x-y   | -      | -      | -      | +      | -      | -      | +      | +      | +      |
| h1: x-4   | -      | -      | -      | +      | +      | +      | +      | -      | +      |
| h2: y-4   | -      | -      | -      | +      | +      | +      | -      | -      | -      |

```
point:  (5,4)
H1:   { (6,5), (9,1), (4,2) }
dist: {  1,41,     5,  2,24 }
H2:   { (9,1) }
dist: {     5 }

nejlepší soused: (6,5)
```

### Edit distance

|     |     | f   | a   | s   | t   |
| --- | --- | --- | --- | --- | --- |
|     | 0   | 1   | 2   | 3   | 4   |
| c   | 1   | 1↖  | 2↖  | 3↖  | 4↖  |
| a   | 2   | 2↖  | 1↖  | 2←  | 3←  |
| t   | 3   | 3↖  | 2↑  | 2↖  | 2↖  |
| s   | 4   | 4↖  | 3↑  | 2↖  | 3↖  |

| znaky jsou stejné      | znaky jsou jiné    |
| ---------------------- | ------------------ |
| min( ↖, ↑ + 1, ← + 1 ) | min( ↖, ↑, ← ) + 1 |
