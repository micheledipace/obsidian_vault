**	28-04-2026 17:54
Tags:[[Elettronica]] [[Analogica]] [[Amplificatori]]

# Amplificatori operazionali
Per via della loro versatilitá gli amplificatori operazionali sono circuiti fondamentali per l'elaborazione di segnali.
Solitamente un amplificatore operazionale ha in ingresso due segnali e ha una uscita. 
Un amplificatore operazionale amplifica la differenza di tensione tra i due terminali di ingresso.
$$v_o = A(v_2 - v_1)$$

#### Caratteristiche
- hanno guadagno in anello aperto infinito (caso ideale)
- hanno banda passante infinita
- hanno impedenza in ingresso infinita
- hanno impedenza in uscita nulla
- corto circuito virtuale se il terminale non invertente é collegato a massa $(v_2 = v_1)$
- funzionano con segnali in corrente continua
Un sistema con guadagno in anello aperto infinito deve essere retroazionato per poter essere utilizzato. Il collegamento in retroazione fa si che le caratteristiche del sistema retroazionato dipendano solamente dai componenti presenti sul ramo di retroazione.

#### Configurazione invertente
![[amplificatore operazionale in retroazione negativa.png]]
Poiché un amplificatore operazionale ha impedenza in ingresso infinita, tutta la corrente generata dalla tensione in ingresso passa per $R_2$.
Per via del guadagno in anello aperto, $v_2 = v_1 = 0$. La corrente che scorre sul ramo in retroazione é quindi uguale a $$i_1 = i_2 = \frac{v_i}{R_1}$$Applicando la legge di Ohm sul ramo di retroazione $$i_1R_2 + v_o = 0$$ $$v_o = -i_1R_2 = -\frac{v_i R_2}{R_1}$$
Il guadagno in anello chiuso é 
$$G = -\frac{R_2}{R_1}$$
Il segnale nella configurazione invertente é *sfasato di 180 gradi*. Il guadagno è negativo.
Per configurazioni in cui il guadagno in anello aperto é finito, il cortocircuito virtuale non esiste piú. Il segnale nell'ingresso invertente é $-\frac{v_o}{A}$
#### Resistenza in ingresso ed uscita
La resistenza di ingresso deve essere sufficientemente alta affinchè l'Op Amp non assorba segnale.
Tutta via $R_2$ potrebbe assumere valori troppo elevati per raggiungere un guadagno sufficiente.
### Configurazione non invertente
![[Screenshot 2026-05-12 at 16.23.47.png]]
Poichè un Op Amp ideale ha guadagno statico infinito
$$v_2-v_1 = \frac{v_O}{A} = 0, A \rightarrow \infty$$
Nella configurazione non invertente i due ingressi hanno stesso potenziale: nel nodo 2 il potenziale è $v_I$. 
Possiamo 
- Calcolare la corrente che passa in $R_1$
- Calcolare la corrente che passa in $R_2$ 
- Calcolare $v_O$ attraverso le leggi di Kirchhoff
$$G=\frac{v_O}{v_I} = (1 + \frac{R_2}{R_1}) $$
Il ramo di retroazione fa annullare la differenza di potenziale tra i due ingressi di input dell Op Amp portando una parte (partitore di tensione) del segnale di output nel ramo di input.
#### Resistenza in ingresso
La resistenza in ingresso è idealmente infinita perchè idealmente nessuna parte del segnale viene assorbita dall'amplificatore.
#### Problema dell'inseguimento
Un amplificatore operazionale può seguire il segnale di input se in configurazione non invertente questo ha impedenza di ingresso infinita ($R_1$) e impedenza di uscita nulla ($R_2$)
# Referenze