17-05-2026 10:03
Tags: [[Elettronica]] [[Analogica]] [[Materiali semiconduttori]]

# Diodo
Il diodo è una [[Materiali semiconduttori#Giunzione pn|giunzione pn]] con tutte le sue peculiarità.
- La corrente scorre dall'anodo al catodo 
- Può essere utilizzato nei circuiti in due configurazioni
	- Polarizzazione diretta
	- Polarizzazione inversa
- La curva caratteristica di un diodo non ideale **non è lineare**
### Curva caratteristica
![[Screenshot 2026-05-19 at 10.49.59.png]]
Dal grafico si possono notare 3 regioni differenti 
- Regione di polarizzazione diretta
	Il diodo si comporta da circuito aperto e fa passare corrente all'aumentare della tensione. La caduta di tensione in polarizzazione diretta del diodo dipende dal materiale semiconduttore
- Regione di polarizzazione inversa
	Il diodo si comporta come circuito chiuso (idealmente). In realtà lascia passare una corrente *di saturazione* dell'ordine dei nA, microA. Dipende strettamente dalla temperatura.
- Regione di Breakdown
	Secondo le caratteristiche fisiche del semiconduttore, il diodo oltre la tensione di breakdown si comporta fa passare corrente in senso inverso (catodo $\rightarrow$ anodo). I diodi Zener sono costruiti in modo da poter sfruttare questa proprietà.

### Risoluzione di circuiti: modelli per la regine di polarizzazione diretta
#### Modello esponenziale
La curva è approssimabile all'espressione 
$$ i= I_S (e^{\frac{v}{nV_T}} -1)$$
per $i >> I_S$ la relazione è uguale a $I_S \  e^{\frac{v}{nV_T}}$
- $I_S$ è la corrente di saturazione diretta. 
	E' detta di saturazione perchè nella regione di polarizzazione inversa $i = -I_S$ 
- $V_T$ è la tensione termica della giunzione pari a $25 \ \mathrm{mV}$ a temperatura ambiente
- $n$ è una costante che dipende dal materiale semiconduttore (di solito pari a 1).
La risoluzione di un circuito non lineare richiede l'utilizzo di un metodo grafico o iterativo.
In particolare il metodo iterativo consiste nel
1. Calcolare la corrente che scorre nel diodo attraverso le leggi di Kirchhoff, assumendo che il diodo abbia una caduta di tensione di 0.7 V a 1 mA
2. Calcolare la $V_D$ utilizzando il metodo esponenziale considerando come $I_D$ la corrente calcolata al punto 1.
3. Ripetere l'iterazione fino ad ottenere l'approssimazione desiderata.
$$V_2 -V_1 = 2.3 n V_T \log(\frac{I_2}{I_1})$$
#### Modello a tratti
Il diodo viene modellizzato come un generatore di caduta di tensione $V_D$ in serie ad una resistenza $r_d$
#### Modello a tensione costante
Il diodo è modellato come un generatore di caduta di tensione $V_D$.
#### Modello per piccoli segnali 
Viene utilizzato quando il piccolo segnale in questione è molto minore della tensione termica.
Il modello è utile per analizzare segnali dc *sporchi* (ripple).
$$v_D(t) = V_D + v_d(t)$$
$$i_D(t) = e^{\frac{(v_d + V_D)}{nV_T}}$$ se $\frac{v_d}{nV_T} << 1$ è possibile espandere in serie di Taylor la relazione fermandoci al grado 1.
$$i_D(t) = I_D + i_d(t) \approxeq I_D(1 + \frac{v_d}{nV_T})$$
Il diodo ha resistenza al piccolo segnale pari a 
$$r_d = \frac{nV_T}{I_D}$$
### Modello per polarizzazione inversa: diodo Zener
![[Screenshot 2026-05-20 at 09.05.05.png|432]]
Il diodo è modellato come un generatore di caduta di tensione reale. Il diodo Zener non deve essere operato nella regione $0>V_D >V_ {ZK}$ per evitare instabilità. 
$V_{Z0}$ è il punto in cui la retta di coefficiente angolare $\frac{1}{r_z}$ interseca l'asse $v$. 
Solitamente questi valori sono indicati nel datasheet del componente.
![[Screenshot 2026-05-20 at 09.06.03.png]]
$$V_Z = V_{Z0} + r_z I_Z$$
I diodi Zener vengono utilizzati per la regolazione del voltaggio come se fossero piccole resistenze in parallelo quando ai loro capi ci sono picchi di tensione non desiderati.