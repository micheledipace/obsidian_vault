07-05-2026 18:50
Tags: [[Elettronica]] [[Analogica]] [[Amplificatori]]

# Amplificatori differenziali
Lo scopo di un amplificatore operazionale differenziale è quello di eliminare i segnali comuni ($v_{Icm})$ ed amplificare la differenza tra i due segnali ($v_{Id}$). 
Nei casi reali
$$v_O = A_{Id} v_{Id} + A_{cm}v_{cm}$$
L'efficacia è misurata dal **common mode rejection ratio** 
### Op Amp differenziale a singolo stadio
Intuitivamente possiamo costruire l'amplificatore combinando la configurazione [[Amplificatori operazionali#Configurazione non invertente |non invertente]] (gain negativo) e quella [[Amplificatori operazionali#Configurazione invertente|invertente]] (gain positivo) di un Op Amp.
Possiamo ridurre il guadagno della configurazione non invertente ($1+\frac{R_2}{R_1}$) utilizzando un partitore di tensione.
$$(\frac{R_4}{R_3 + R_4}) (1 + \frac{R_2}{R_1}) = \frac{R_2}{R_1}$$
Soddisfatta per 
$$\frac{R_4}{R_3} = \frac{R_2}{R_1}$$

### Calcolo del guadagno differenziale

![[Screenshot 2026-05-13 at 09.52.13.png]]
- Utilizzare il metodo della superposizione. Le due configurazioni ottenute sono quella invertente e quella non invertente. Risulta $A_d = \frac{R_2}{R_1}$
- Calcolare il guadagno di modo comune, uguale a zero nei casi ideali.
### Drawbacks
- L'amplificatore operazionale richiede un'alta resistenza di ingresso.
- Per aumentare il guadagno, l'amplificatore differenziale richiede una bassa resistenza di ingresso
Per questo è difficile calibrare accuratamente un'amplificatore differenziale.
# Referenze