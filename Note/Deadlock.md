10-07-2026 11:56
Tags: [[Sistemi Operativi]]

# Deadlock
Stato di attesa indefinito. Accade quando una processo è in attesa di risorse da processi che sono anch'essi in attesa.
Le situazioni di deadlock possono essere descritte da grafi.
### Condizioni per la verifica del deadlock 
Le condizioni devono verificarsi simultaneamente
- Mutua esclusione
	Un processo per volta può accedere alla risorsa.
	Alcune risorse non sono condivisibile per loro natura.
- Assenza di preemption
	L'esecuzione di un processo non può essere terminata esternamente per poter liberare la risorsa
- Possesso e attesa
	Il processo deve necessariamente attendere tutte le risorse anche se ne dispone già di alcune.
	L'assenza di questa condizione comporta starvation. (un processo possiede tutte le risorse necessarie o non ne possiede nessuna)
- Attesa circolare
	Per evitare questa condizione i thread non devono richiedere risorse di thread con un indice più basso del loro.
Per prevenire situazioni di deadlock è necessario assicurarsi che una di queste quattro condizioni non si verifichi mai.
### Stati sicuri
Il sistema è in uno stato sicuro se esiste almeno una sequenza precisa di esecuzione che eviti un deadlock.

### Algoritmo del banchiere
Algoritmo per la determinazione di stati sicuri. Si basa su vettori e matrici.
- Vettore Available 
	Vettore delle risorse disponibili
- Matrice Max
	Matrice che indica per ogni processo il massimo numero di risorse di cui il processo ha bisogno, suddivise per tipo
- Matrice Allocation
	Matrice delle risorse già assegnate ad ogni processo, suddivise per tipio
- Matrice Need
	Matrice delle risorse i cui processi necessitano per poter completare la loro esecuzione.
- Vettore Work
	Vettore delle risorse disponibili + quelle deallocate

### Ripristino dal deadlock 
- Abort di processi
	Abortire tutti i processi o uno per volta in base a priorità, numero di risorse adoperate, age del processo (notevole overhead causato dall'algoritmo di rilevazione)
- Preemption
	Selezionare il processo vittima in base al numero di risorse occupate e tempo di esecuzione. Occorre evitare la starvation.	
- Rollback
	Riportare un processo ad uno stato sicuro dopo aver sottratto una risorsa da questo




# Referenze