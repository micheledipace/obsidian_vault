01-06-2026 16:52
Tags: [[Basi di Dati]] [[SQL]]
# Base di dati attiva
Una base di dati attiva **reagisce automaticamente** al verificarsi di determinati eventi. 
I DBMS in commercio utilizzano i **Trigger** per seguire il *paradigma ECA*(Evento-Condizione-Azione)
- Evento 
	Qualsiasi operazione di manipolazione dei dati (insert, update, delete)
- Condizione
	Predicato booleano
- Azione 
	Sequenza di statement SQL anche procedurali (PL/SQL)
### Sintassi
```
CREATE TRIGGER TriggerName
event mode {, event} 
on TargetTable
[referncing reference]\\ alias per il vecchio valore e il nuovo valore
[granularity]\\ livello di dettaglio
[when (condition)]
StatementSQL
```
#### Modalità
- Immediata 
	1. After
		E' la modalità da utilizzare quando si vuole effettuare un'operazione su una tabella (**tabella target**) A dopo un'operazione effettuata su una tabella B
	2. Before
		Viene utilizzata quando c'è bisogno di intercettare una modifica *prima che questa venga scritta* sul disco. E' utilizzata quando bisogna confrontare i dati nuovi (*che stanno per essere inseriti*) e quelli vecchi.
- Differita
#### Granularità 
Definisce *quante volte* il trigger viene eseguito
- row-level 
	L'operazione viene ripetuta per tutte le righe
- statement-level (valore di default)
	L'operazione viene eseguita una volta per tutte le righe
#### Esecuzione
Statement SQL (**no DDL**)
# Referenze