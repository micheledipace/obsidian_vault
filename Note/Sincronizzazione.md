10-07-2026 10:28
Tags: [[Sistemi Operativi]]

# Sincronizzazione
La sincronizzazione tra thread è necessaria quando questi tentano di accedere a dati condivisi.
In thread che cooperano secondo il paradigma [[I Processi#Paradigma produttore consumatore|produttore consumatore]], la sequenza con cui i thread hanno accesso ai dati determina il risultato finale dell'operazione (**corse critiche**)
### Sezione critica
Occore dichiarare come sezione critica la porzione di codice ad accesso condiviso
- Ogni thread può avere una sua sezione critica
#### Requisiti per la sincronizzazione tra processi
- Mutua esclusione
	Se un thread sta eseguendo la sua sezione critica, nessun altro thread può entrare nella sua sezione critica
- Progresso
	I thread che **non** stanno eseguendo la loro sezione **non** critica possono decidere quale thread deve entrare nella sua sezione critica. **Nessun processo esterno** può bloccare l'accesso di un altro thread alla sua sezione critica. Previene situazioni di stallo (deadlock).
- Attesa limitata
	Esiste un limite di quante volte gli altri thread possono entrare nella loro sezione critica dopo che un thread ha fatto richiesta di entrare nella sua. Previene la starvation. 
#### Algoritmo di Bakery (del fornaio)
Fornisce una soluzione software al problema. Ogni thread riceve un token di priorità. Il thread con il token dal valore più basso possono accedere alla loro sezione critica.
- Se ci sono più thread con un token dello stesso valore, vale l'ordinamento FCFS.

#### Soluzioni hardware
- Per sistemi a singolo processore si possono disabilitare gli interrupt durante l'accesso alle sezioni critiche
	Inefficiente per sistemi multiprocessore perchè l'istruzione che gestisce la disattivazione degli interrupt deve essere eseguita per ogni processore
- Implementazione di istruzioni speciali atomiche (non interrompibili)
	Includono il controllare e modificare il contenuto di una word di memoria e lo scambiare il contenuto di due word di memoria
#### Spin lock
Tecnica software che consiste nel verificare periodicamente l'ottenimento del lock, *sprecando* cicli di CPU. Il periodo in cui il processo aspetta è detto attesa attiva (*busy waiting*). 
- Non obbligano a context-switching e possono essere più efficienti se si prevede che l'attesa duri brevi periodi.
#### Semafori
Sono una variabile intera (integer), protetta dal sistema operativo.
E' possibile accedere al semaforo attraverso le operazioni indivisibili
- `acquire()` 
- `release()`
Queste operazioni non possono essere eseguire da più thread contemporaneamente.
Il *semaforo binario* implementa il requisito mutex.
- Un semaforo con attesa attiva cicla il processo quando il suo valore è $\le$  0
##### Semafori senza busy waiting
Occorre modificare le operazioni di `acquire()` e `release()` implementando la preemption con le operazioni `block` e `wakeup(P)`

Un non corretto ordine delle istruzioni `acquire()` e `release()` comportano stalli.
#### Monitor 
Costrutto (ADT) che raggruppa in un'unica struttura:
- Le variabili condivise (variabili della sezione critica)
- Le funzioni/procedure che operano sulle variabili condivise
- Variabili per le regole di sincronizzazione (*variabili di tipo condition*)
Garantiscono 
- Mutua esclusione
	Solo un thread per volta può accedere al monitor
- Superamento del busy waiting
	Implementano regole di sincronizzazione che permettono la sospensione di un thread (portato nello stato di wait) che aspetta risorse all'interno del monitor.
# Referenze