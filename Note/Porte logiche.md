17-03-2026 08:59
Tags: [[Algebra Booleana]] [[Elettronica]] [[Progettazione Logica]]
 
# Porte logiche
Le porte logiche sono gli elementi fondamentali per la sintesi dei circuiti di commutazione (*switching circuits*). 
Possono essere realizzate con [[Diodo|diodi]] in parallelo.
### Porta NOT
Base di ogni porta logica

| A   | B   |
| --- | --- |
| 0   | 1   |
| 1   | 0   |

### Porta AND

| A   | B   | F   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |
### Porta OR

| A   | B   | F   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 1   |
## Porte logiche composte
### Porta NAND
| A   | B   | F   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |

### Porta NOR
| A   | B   | F   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 0   |

### Porta EXOR
Equivalente alla somma diretta  

| A   | B   | F   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |
# Referenze