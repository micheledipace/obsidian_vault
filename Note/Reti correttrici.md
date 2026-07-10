`09-06-2026 17:28
Tags: [[Automatica]] [[Diagrammi di Bode]] [[Diagrammi di Nyquist]]

# Reti correttrici
### Rete anticipatrice (lead compensator)
Produce un anticipo di fase, come una rete PD, ma l'amplificazione alle alte frequenze rimane limitata. 
Lo zero deve avere una pulsazione di break **minore** di quella del polo.
$$D_c(s) = \frac{T_Ds + 1}{\alpha T_D s +1 }, \alpha < 1$$
- $\sin \phi_{max} = \frac{1-\alpha}{1+\alpha}$ 
- $\alpha = \frac{1- \sin \phi_{max}}{1 + \sin \phi_{max}}$ 
- $\omega_{\phi_{max}} = \frac{1}{T_D \sqrt{\alpha}}$  
- $\frac{1}{\alpha}$ è il rapporto tra la costante di tempo dello zero e quella del polo.
#### Progettazione 
1. Trovare $K$ che soddisfi le specifiche di progetto in termini di risposta agli errori.
2. La rete anticipatrice ha un guadagno di $-10\log{\alpha} = 10\log{\frac{1}{\alpha}}$ (**da trascurare**)
3. Trovare la nuova pulsazione di crossover a seguito del guadagno della rete anticipatrice
4. $w_{\phi \mathrm{max}} = \frac{1}{\tau \sqrt{\alpha}} = \omega_c$ 
### Rete ritardatrice (lag compensator)
Il polo deve avere una pulsazione di break **minore** di quella dello zero. Le pulsazioni di break della rete ritardatrice devono essere comunque minori di quelle del plant.
$$D_c(s) =\frac{\alpha T_I s + 1}{T_I s + 1}, \alpha < 1$$
La pulsazione di crossover dopo la correzione $\omega_c$ è tale se 
$$20 \log_{10} |KG(j\omega_c)| + 20 \log_{10} \alpha = 0$$
#### Progettazione
1. Trovare K che rispetti la specifica di reiezione degli errori a regime
2. Con il margine di fase richiesto dalla specifica calcolare la nuova pulsazione di crossover (solo plant).
3. Dalla relazione citata al paragrafo precedente, $\alpha = | \frac{1}{KG_p(j\omega_c)}|$
4. il nuovo $\omega_c$ deve essere una decade o un'ottava più piccolo della pulsazione di break della rete ritardatrice 
### Controllore PID 

$$D_c(s) = k_P (\frac{1 + T_Is + T_IT_D s^ 2}{T_I s})$$
#### Taratura con Ziegler - Nichols
$T_{CR}$  è il periodo dell'oscillazione alla pulsazione di crossover della fase $\omega_{\pi}$ 
$K_{CR}$ è il guadagno di anello aperto critico. $K_{CR} = \frac{1}{|G(j\omega_{\pi})|}$
### Predittori di Smith
sia $G_I(s) = G(s) e^{-\tau s}$ l'equazione del plant. Questo sistema con ritardo puro non può essere corretto con l'analisi standard. Smith trovò un modo per estrarre dalla retroazione il ritardo puro $e^{-\tau s}$ .
![[Screenshot 2026-06-10 at 09.21.07.png|617]]
$$D'(c) = \frac{D_c(s)}{1 + D_c(s)(G(s)- e^{-\tau s}G(s))}$$
La f.d.t del feedback loop del plant è 
$$T(s) = \frac{D_c(s)G(s)}{1 + D_c(s) G(s)}  e^{-\tau s} $$
Solitamente il controllore è progettato come 
$$G_c(s) = \frac{K_c(s+z_c)}{s+p_c}$$
$z_c$ si trova con le specifiche richieste (tempo di assestamento e coefficiente di smorzamento)
$p_c$ si trova con l'appartenenza al LdR di $G_c(s) G_p(s)$ 
$K_c$ si trova ponendo il modulo di $G_c(s)G_p(s)$ a 1 
# Referenze