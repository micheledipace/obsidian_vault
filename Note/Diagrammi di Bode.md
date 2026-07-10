209-06-2026 16:17
Tags: [[Automatica]]

# Diagrammi di Bode
Rappresentano analiticamente la risposta armonica di una funzione di trasferimento su scala logaritmica. Trasformare la funzione di trasferimento in forma di costanti di tempo
Ci sono alcune regole per il tracciamento del grafico

|                                                                                                                            | Guadagno di ampiezza                                                                    | Guadagno di fase                      | Pulsazione di break                                                |
| -------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------- | ------------------------------------------------------------------ |
| polo nell'origine $\frac{1}{s^{\mu}}$                                                                                      | $-\mu 20 \mathrm{dB}$ per decade                                                        | la fase parte da $-\mu \frac{\pi}{2}$ |                                                                    |
| polo a fase minima $\frac{1}{(\tau s + 1)}$                                                                                | - 20 $\mathrm{dB}$ per decade                                                           | $-\frac{\pi}{2}$ asintoticamente      | $\omega_B = \frac{1}{\tau}$                                        |
| polo a fase non minima $\frac{1}{\tau s - 1}$                                                                              | same                                                                                    | $\frac{\pi}{2}$ asintoticamente       | same                                                               |
| zero a fase minima $1+ \tau s$                                                                                             | 20 $\mathrm{dB}$ per decade                                                             | $\frac{\pi}{2}$ asintoticamente       | same                                                               |
| zero a fase non minima $1- \tau s$                                                                                         | same                                                                                    | $-\frac{\pi}{2}$ asintoticamente      | same                                                               |
| coppia di poli complessi e coniugati a fase minima $\frac{1}{\frac{s^ 2}{\omega_n ^ 2} + \frac{2 \delta}{\omega _n}s + 1}$ | $-40 \mathrm{dB}$ per decade picco di risonanza: $\|G(j\omega_R)\| = \frac{1}{2\delta}$ | $- \pi$ asintoticamente               | $\omega_R = \omega_n \sqrt{1-2\delta ^ 2}$ Pulsazione di risonanza |
| coppia di zeri complessi e coniugati a fase minima$\frac{s^ 2}{\omega_n ^ 2} + \frac{2 \delta}{\omega _n}s + 1$            | $40 \mathrm{dB}$ per decade picco di risonanza: $\|G(j\omega_R)\| = 2\delta$            | $\pi$ asintoticamente                 | same                                                               |
| ritardo puro                                                                                                               | $\|e^{-j\omega T_D}\|$ = 1 per ogni $\omega$                                            | la fase è $-\omega T_D$               |                                                                    |



### Margine di ampiezza
Sia $\omega_{\pi}$ la frequenza di crossover per la fase (phase = -180), il margine di ampiezza $GM$ è uguale a $$GM =\frac{1}{|KG(j\omega_{\pi})|}$$ 
### Margine di fase
Sia $\omega_c$ la frequenza di crossover per l'ampiezza, il margine di fase è la distanza tra la fase alla frequenza di crossover e -180.
$$\delta = \frac{PM}{100}$$



# Referenze