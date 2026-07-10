03-04-2026 17:33
Tags: [[Elettronica]] [[Progettazione Logica]] [[Circuiti Sequenziali]]

# Flip-flop
- Costituiscono le celle elementari di memoria.
- Si differenziano in base alle combinazioni di input che possono ricevere in ingresso.
- Possono avere ingressi di CLEAR e ENABLE.
- L'input viene letto e lo *stato* del FF viene aggiornato ad ogni impulso di clock (rising edge/falling edge)
### S-R Flip Flop
La combinazione S = R = 1 é vietata

| S   | R   | Q   | Q+        |
| --- | --- | --- | --------- |
| 0   | 0   | 0   | 0         |
| 0   | 0   | 1   | 1         |
| 0   | 1   | 0   | 0         |
| 0   | 1   | 1   | 0         |
| 1   | 0   | 0   | 1         |
| 1   | 0   | 1   | 1         |
| 1   | 1   | 0   | forbidden |
| 1   | 1   | 1   | forbidden |

### J-K Flip Flop
La combinazione J=K=1 ha funzione di toggle.

| J   | K   | Q   | Q+  |
| --- | --- | --- | --- |
| 0   | 0   | 0   | 0   |
| 0   | 0   | 1   | 1   |
| 0   | 1   | 0   | 0   |
| 0   | 1   | 1   | 0   |
| 1   | 0   | 0   | 1   |
| 1   | 0   | 1   | 1   |
| 1   | 1   | 0   | 1   |
| 1   | 1   | 1   | 0   |
Se lo stato presente é 0, l'ingresso K é don't care. Se lo stato presente é 1, l'ingresso J é don't care

| J   | K   | Q   | Q+  |
| --- | --- | --- | --- |
| 0   | X   | 0   | 0   |
| X   | 0   | 1   | 1   |
| 0   | X   | 0   | 0   |
| X   | 1   | 1   | 0   |
| 1   | X   | 0   | 1   |
| X   | 0   | 1   | 1   |
| 1   | X   | 0   | 1   |
| X   | 1   | 1   | 0   |
### T Flip Flop
É uguale ad un flip flop JK i cui ingressi sono entrambi alti o bassi

| T   | Q   | Q+  |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |

### D Flip Flop
Lo stato futuro é uguale all'ingresso in input 

| D   | Q   | Q+  |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 1   |
| 1   | 1   | 1   |


# Referenze