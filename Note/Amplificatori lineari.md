28-04-2026 16:56
Tags: [[Elettronica]] [[Analogica]] [[Amplificatori]]

# Amplificatori lineari
Questi rappresentano una delle funzioni fondamentali per il processing dei signali. Infatti segnali di piccola ampiezza rendono poco preciso qualsiasi tentativo di elaborazione.
#### Principio di linearitá
É necessario che il segnale in input sia una sinusoide per poter godere del principio di linearitá: dopo l'amplificazione, il segnale non verrá in alcun modo disturbato o distorto.
#### Relazione di amplificazione
$$ v_s(t) = A v_o(t)$$
Con $A$ *guadagno di amplificazione* 

#### Differenza con i trasformatori
É importante notare che gli amplificatori lineari non mantengono la potenza invariata.

#### Tipi di amplificatore (ideali)

| Nome                              | Guadagno                                                      | Resistenza in ingresso | Resistenza in uscita |
| --------------------------------- | ------------------------------------------------------------- | ---------------------- | -------------------- |
| Amplificatore di tensione         | A = $\frac{V_o}{V_i}$ (gen. tensione controllato in tensione) | $R_i = \infty$         | $R_o = 0$            |
| Amplificatore di corrente         | $A = \frac{I_o}{I_i}$ (gen. corrente controllato in corrente) | $R_i = 0$              | $R_o = \infty$       |
| Amplificatore di transconduttanza | $G = \frac{i_o}{V_i}$ (gen. corrente controllato in tensione) | $R_i = \infty$         | $R_o = \infty$       |
| Amplificatore di transresistenza  | $G = \frac{V_o}{i_i}$ (gen. tensione controllato in corrente) | $R_i = 0$              | $R_o = 0$            |

#### Modello per un amplificatore di tensione![[modello per amplificatore lineare tensione.png]]
Idealmente l'amplificatore non deve perdere segnale dall'input e sul carico deve passare tutto il potenziale amplificato. 
Matematicamente $R_i >> R_s, R_L >> R_o$
#### Amplificatori a cascata
Per rispettare le specifiche di progetto é possibile collegare piú amplificatori in cascata. L'ultimo stadio di amplificazione é rappresentato da un amplificatore *buffer* che aumenta la potenza del segnale, ma non ne modifica l'ampiezza.
# Referenze