17-05-2026 10:03
Tags: [[Elettronica]] [[Analogica]] [[Diodo]]

# Circuiti raddrizzatori
Hanno lo scopo di eliminare le oscillazioni di un segnale AC.
A differenza dei trasformatori non hanno lo scopo di cambiare l'ampiezza del segnale sinusoidale, ma quello di creare un **segnale DC** il più stabile possibile.

![[Screenshot 2026-05-20 at 09.18.25.png]]

1. Il primo blocco fondamentale è un trasformatore che riduce la tensione in arrivo ad un valore vicino a quello desiderato
2. Il circuito raddrizzatore elimina le semionde negative del segnale
3. Un filtro *passa alto* (capacitivo) riduce sensibilmente le oscillazioni. La parte ancora dipendente dal tempo è chiamata **ripple** 
4. Un regolatore di tensione cerca di rendere il più costante possibile il segnale.

#### Caratteristiche di un circuito raddrizzatore
- Peak inverse voltage (PIV), la tensione inversa massima che il diodo deve sostenere senza cadere nella regione di breakdown.
- Intensità di corrente massima che il diodo può far scorrere
#### Raddrizzatore a semi-onda
Schematizzato da una resistenza in parallelo ad un diodo. AI capi nel diodo è applicato il segnale da raddrizzare. Il PIV è uguale all'ampiezza massima del segnale.
Il segnale viene annullato durante la semi-onda negativa del segnale.
#### Raddrizzatore a doppia semi-onda a ponte 
![[Screenshot 2026-05-20 at 11.12.16.png]]
1. Quando $v_s$ è nella sua semi-onda positiva, $D_1$ e $D_2$ sono attivi. 
2. $v_o$ ha una caduta di tensione pari a $2 V_D$ . I due diodi sono in serie
3. Il PIV in semi onda positiva è $$\mathrm{PIV} = v_o + v_{D2} = V_s - 2V_D + V_D = V_s - V_D$$
#### Raddrizzatore con filtro capacitivo (diodo ideale)
![[Screenshot 2026-05-20 at 10.54.32.png|535]]
![[Screenshot 2026-05-20 at 10.55.07.png|650]]
Il segnale raddrizzato non è utilizzabile da apparecchi a corrente continua perchè non sufficiente costante. Un filtro capacitivo risolve il problema:
- Il condensatore viene caricato dall'elevata intensità di corrente che passa nel diodo quando è in polarizzazione diretta
- Scegliendo opportunamente la resistenza e la capacità $RC >> T$ il condensatore manterrà la tensione pressochè costante: $I_L = \frac{V_p}{R_L}$ 
- $v_O = V_p -V_r, t = T$ (1.)
- Dall'equazione del condensatore $v_O = V_p e^{-\frac{t}{CR}} \approx V_p(1-\frac{T}{CR})$ (2.)
- Combinando 1. e 2. $V_r = \frac{V_p}{fCR}$ (3.)
- $\cos(\omega \Delta t)$ è l'angolo di conduzione. L'intervallo di conduzione è $V_p \cos(\omega \Delta t) = V_p - v_r$ 
- per $V_r << V_p$,  $\omega \Delta t = \sqrt{\frac{2V_r}{V_p}}$ (4.)
- In media $i_{Dav} = i_{Cav} - I_L$ 
- Eguagliando la quantità di carica acquisita e persa dal condensatore$$Q_{fornita} = Q_{persa}; \ i_{Cav}\Delta t = CV_r $$
- Unendo tutte queste precedenti equazioni si trova $I_{Dav}$ per un circuito raddrizzatore a semi-onda con filtro capacitivo.
- La frequenza di un circuito raddrizzatore a doppia semi-onda capacitiva è doppia, mentre la corrente che passa nel diodo è circa la metà
- $$i_{Dav} = I_L(1+\pi \sqrt{2\frac{V_P}{v_r}})$$
$$i_{Dmax} = I_L(1+2\pi \sqrt{2\frac{V_P}{v_r}})$$
- A volte non si considerano i diodi ideali, ma si utilizza il modello a caduta costante $$V_p -2v_D\ \mathrm{full \ wave \ rectifier} \ , V_p - V_D$$
# Referenze