27-05-2026 11:53
Tags: [[Elettronica]] [[Analogica]] [[Transistori]] [[Amplificatori]]

# Amplificatori a transistor

### Modello per piccoli segnali
Esempio per configurazione ad emettitore comune con segnale in ingresso sulla base. La **resistenza di piccolo segnale** si trovera sulla base.
![[Screenshot 2026-05-27 at 16.34.57.png|292]]
- il piccolo segnale è $v_{be}$. L'approssimazione per piccoli segnali è valida quando $v_{be} << V_T$ 
- Si può calcolare $i_C=I_Se^{\frac{V_{BE}+v_{be}}{V_T}}=I_C + i_c$ 
- Si ottiene $$i_c = g_m v_{be}, \ g_m=\frac{I_C}{V_T}$$
	$g_m$ è la *transconduttanza* per il piccolo segnale
- E' possibile calcolare la corrente di base del piccolo segnale e la resistenza di piccolo segnale.
	$i_b = \frac{i_c}{\beta}=\frac{g_m v_{be}}{\beta} \ r_{\pi} = \frac{v_{be}}{i_b}=\frac{\beta}{g_m}$ 
- La resistenza di piccolo segnale è in parello alla resistenza in uscita $r_o$ dovuta all'[[Transistor BJT#Effetto Early|effetto Early]].
- Analogamente è possibile calcolare la corrente di emettitore e la resistenza di emettitore per piccolo segnale
### Modello a $\pi$ ibrido (modello utilizzato da DDV)
![[Screenshot 2026-05-27 at 16.55.27.png]]
Modelli per amplificatori rispetivamente di tensione e corrente.
### Configurazioni per [[Transistor BJT|transistor BJT]]
- Configurazione ad emettitore comune
	L'emettitore è shortato con il gnd. Base ed emettitore sono anche loro collegati al ground.
	- La base è il **terminale di ingresso**
	- L'uscita è riferita tra il collettore e l'emettitore (massa)
	![[Screenshot 2026-05-27 at 16.26.48.png|263]]
- Configurazione a base comune
- Configurazione a collettore comune 
### Amplificatore come blocco funzionale
![[Screenshot 2026-05-27 at 17.33.41.png]]
#### Valori caratteristici per l'amplificatore
- Resistenza di ingresso
	$R_{in} = \frac{v_i}{i_i}$
- Resistenza di uscita
	$R_o = \frac{v_x}{i_x}$ (da misurare con $v_i = 0$)
- Guadagno in anello aperto
	$A_{vo} = \frac{v_o}{v_i}$ con la resistenza di carico che tende all'infinito.
- Tensione in ingresso 
	$v_i = v_{sig} \frac{R_{in}}{R_{sig} + R_{in}}$ 
- Guadagno dell'amplificatore (base-collettore)
	$A_v = \frac{v_o}{v_i}=A_{vo}\frac{R_L}{R_L+R_o}$ 
- Tensione di uscita
	$v_o = A_{vo}v_i \frac{R_L}{R_o + R_L}$ 
- Guadagno complessivo
	$G_v = \frac{v_{o}}{v_{sig}} = A_{vo}\frac{R_{in}}{R_{sig} + R_{in}}\frac{R_L}{R_o + R_L}$ 
#### Caratteristiche per BJT ad emettitore comune
- $R_{in} = R_{\pi}$ 
- $A_{vo} = -g_m R_C$ (la corrente di collettore entra nel terminale collettore)
- $R_o = R_C$ (un eventuale carico va messo in parallelo con $R_C$)
#### Caratteristiche per BJT ad emettitore comune con resistenza di emettitore $R_e$
1. La resistenza di input aumenta di un fattore $(1+g_mR_e)$
	La resistenza di ingresso è $(\beta +1)$ volte la resistenza totale dell'emettitore $(r_e + R_e)$ 
2. Il guadagno base collettore diminuisce di un fattore $(1+g_mR_e)$
3. $v_i$ non coincide più con $v_{\pi}$

![[Screenshot 2026-05-28 at 16.07.44.png|697]]
da fare con modello pi greco
# Referenze