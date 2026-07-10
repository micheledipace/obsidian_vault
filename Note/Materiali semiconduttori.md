17-05-2026 10:01
Tags: [[Elettronica]] [[Analogica]]

# Materiali semiconduttori
I materiali semiconduttori sono alla base di ogni circuito integrato. La loro conformazione a reticolo cristallino fa si che si comportino da isolanti a basse temperature e da conduttori ad alte temperature.
### Lacune ed elettroni liberi
- Le zone a maggioranza di cariche positive sono chiamate lacune
- Gli elettroni liberi sono attratti dalle zone a carica positiva. 
A temperatura ambiente il semiconduttore è in equilibrio. 
Il rateo di **ricombinazione** tra elettroni liberi e lacune aumenta di un fattore $T^{\frac{3}{2}}$.
Poichè far funzionare i circuiti integrati ad elevate temperature è **impraticabile**, la tecnica del **drogaggio** amplifica il comportamento conduttivo dei semiconduttori.
### Drogaggio p ed n 
Il drogaggio modifica la concentrazione di lacune ed elettroni liberi. Gli atomi dopanti sostituiscono alcuni degli atomi di semiconduttore nel reticolo cristallino.

|                                     | p                                                                 | n                                                            |
| ----------------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------ |
| Come cambia il reticolo cristallino | Aumenta la concentrazione di lacune                               | Aumenta la concentrazione di elettroni liberi                |
| Sostanza dopante                    | Boro (3 elettroni di valenza)                                     | Fosforo (5 elettroni di valenza)                             |
| Cosa succede                        | Gli atomi accettano gli elettroni liberi del reticolo cristallino | Gli atomi donano un elettrone libero al reticolo cristallino |
| Portatori di maggioranza            | lacune                                                            | elettroni liberi                                             |
### Corrente di deriva e corrente di diffusione
- La corrente di deriva si genera dall'inserimento di un campo elettrico in una lastra di semiconduttore. Dipende dalla costante di mobilità del semiconduttore
	- La corrente di diffusione è dovuta allo spostamento di lacune ed elettroni in zone in cui la loro concentrazione è più bassa.
#### Tensione termica
La tensione termica $V_T$ è la relazione tra la costante di diffusione $D$ e quella di mobilità $\mu$ 
$$\frac{D_p}{\mu_p} = \frac{D_n}{\mu_n} = V_T$$
### Giunzione pn 
![[Screenshot 2026-05-17 at 11.55.49.png]]
è la struttura fondamentale dei circuiti integrati. La giunzione pn è quello che costituisce un diodo. Inoltre viene utilizzata per la realizzazione dei transistor MOSFET e BJT.
- Due zone di semiconduttore drogate differentemente sono messe in contatto.
- La corrente di diffusione crea una campo elettrico nel punto di contatto tra le due parti di semiconduttore.
- La zona è chiamata depletion region (regione di carica spaziale).
- Il campo elettrico ha una tensione detta tensione propria della giunzione.
- La situazione di equilibrio si raggiunge quando l'intensità della corrente di deriva è uguale all'intensità della corrente di diffusione.
- La giunzione pn è in **polarizzazione diretta** se la tensione nella regione p è maggiore di quella agli estremi della giunzione n
- La giunzione pn è in **polarizzazione indiretta** se la tensione nella regione n è maggiore di quella agli estremi della giunzione p
#### Giunzione pn con tensione esterna applicata
![[Pasted image 20260517115227.png|516]]

- Le lacune della regione p diventano portatori di minoranza nella regione n
- Gli elettroni della regione n diventano portatori di minoranza nella regione p.
- 
### Regione di Breakdown
![[Screenshot 2026-05-19 at 11.10.57.png|433]]
Il fenomeno del breakdown di una giunzione pn avviene ad un certo valore $V_Z$ caratteristico del semiconduttore che forma la giunzione.
Applicando una tensione minore del valore di **breakdown** il diodo farà scorrere corrente negativa. Questo succede quando il campo elettrico nella regione di carica spaziale romper i legami covalenti tra lacune e elettroni liberi. 
Il movimento *inverso* di elettroni e lacune genera la corrente inversa. 
Diminuendo ulteriormente la tensione un grande numero di portatori di carica viene generato, aumentando esponenzialmente l'intensità di corrente.



# Referenze