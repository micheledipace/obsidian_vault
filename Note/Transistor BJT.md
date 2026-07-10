22-05-2026 10:59
Tags: [[Elettronica]] [[Analogica]] [[Transistori]]

# Transistor BJT
Sono componenti elettronici formati da materiali semiconduttori. Questo tipo di transistor è formato da *due giunzioni pn*, la cui polarizzazione determina il comportamento del transistor.
### Due tipologie di transistor.
- transistor *npn*
- transistor *pnp*
La freccia è sempre sull'emettitore e indica il verso della corrente. 
Il terminale più in alto è quello a potenziale maggiore

![[Screenshot 2026-05-27 at 10.45.35.png]]
Ogni transistor BJT è formato da tre terminali:
1. emettitore
2. base (regione meno drogata)
3. collettore
### Regioni di funzionamento

| Emettitore-Base | Emettitore-Collettore | Modalità                               |
| --------------- | --------------------- | -------------------------------------- |
| Diretta         | Inversa               | Zona attiva diretta (*amplificazione*) |
| Inversa         | Inversa               | Interdizione                           |
| Diretta         | Diretta               | Saturazione                            |
### Calcolo della corrente in ZAD
1. Calcoliamo la corrente di collettore $I_C$ come la corrente passante in una giunzione pn. La corrente di collettore **dipende solo** dalla tensione $V_{BE} \approx 0.7\mathrm{V}$ 
$$I_C = I_S e^{\frac{V_{BE}}{V_T}}$$
2. la corrente di base $I_B$ è uguale a $$I_B = \frac{I_B}{\beta}$$ $\beta$  è un valore tecnologico del transistor.
3. La corrente di emettitore $I_E$ è uguale a $$I_E = I_B + I_C = \frac{I_C}{\alpha}$$
con $\alpha = \frac{\beta}{\beta +1}$
### Modello per grandi segnali (DC)
Transistor npn
![[Screenshot 2026-05-27 at 11.09.41.png|Transistor npn]] 

Transistor pnp
![[Screenshot 2026-05-27 at 11.11.24.png|Transistor pnp]]

### Effetto Early 
Curva caratteristica $i_c - v_{CB}$ 
 ![[Screenshot 2026-05-27 at 11.56.06.png|Curva caratteristica|inlL|417]]
Sebbene, secondo quanto precedentemente detto, la corrente di collettore $i_C$ dipenda esclusivamente dal valore $V_{BE}$, la *configurazione ad emettitore comune* (emettitore in corto con GND) mostra curve caratteristiche diverse.
- Sia $v_{CE} = v_{BE}+ v_{CB}$ per un transistor npn
Sperimentalmente si nota che la corrente di collettore dipende anche dalla tensione del collettore. 
Si ottengono più curve per diversi valori di $v_{BE}$ con pendenza $\frac{\partial i_C}{\partial v_{CE}}$ pari alla resistenza in uscita $r_o = \frac{V_A}{I'_C}$ con $I'_C$ corrente di collettore senza contare l'effetto early
I prolungamenti delle curve incontrano l'asse delle ascisse nel punto $-V_A$ , tensione di Early (*valore tecnologico*).
La resistenza $r_o$ influisce sul guadagno degli amplificatori a transistor in configurazione ad emittore comune.
### Operazione in modalità saturazione
Quando $v_{CE} \le 0.4 \mathrm{V}$ il transistor entra in modalità saturazione.
La curva caratteristica ha una pendenza uguale alla *resistenza di saturazione* e vale poche decine di Ohm.
Modellano la tensione tra collettore ed emettitore con il valore $$V_{CE\mathrm{sat}} \approx 0.2 \mathrm{V}$$ il valore della resistore $R_{CE\mathrm{sat}}$ è ignorabile.
	In modalità saturazione $i_c$ diminuisce, mentre $i_b$ aumenta
# Referenze

