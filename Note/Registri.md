03-04-2026 17:00
Tags: [[Elettronica]] [[Progettazione Logica]] [[Flip-flop]]

# Registri
Gruppi di *n* D flip-flop che memorizzano n bit di informazione. Hanno clock comune.
#### Utilizzi
-  Adder parallelo con memoria (registro accumulatore)
- Shifting dell'informazione 
#### Registri a scorrimento
- SISO (Serial-Input, Serial-Output). 
	- Solo l'informazione nell'ultimo flip-flop puó essere letta. 
	- Puó essere circolare
- SIPO (**74HC595**)
	- Usano tri-state buffer per shiftare il dato nel registro di output
- PIPO
	- Ha due variabili di controllo, Load e Shift che controllano l'uscita di un multiplexer associato alla variabile D di ogni flip-flop



# Referenze