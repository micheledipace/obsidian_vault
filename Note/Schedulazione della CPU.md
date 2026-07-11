10-07-2026 09:09
Tags: [[Sistemi Operativi]]

# Schedulazione della CPU
Il sistema operativo deve scegliere fra processi in memoria che sono pronti per l'esecuzione ed assegnare la CPU ad uno di essi.
Le decisioni avvengono quando:
- Un processo passa dallo stato di running allo stato di wait (*preemptive*)
- Un processo passa dallo stato di running allo stato di ready
- Un processo passa dallo stato di wait allo stato di ready
- Un processo termina la sua esecuzione (*preemptive*)
Le soluzioni preemptive comportano la sospensione dell'esecuzione. Devono implementare dei meccanismi di **sincronizzazione** per garantire la consistenza dei dati.
### Obiettivi e criteri
L'obiettivo della multiprogrammazione è massimizzare l'utilizzo della CPU, minimizzando gli istanti in cui è in attesa.
#### Criteri di comparazione per algoritmi di schedulazione
- Utilizzo della CPU
- Numero di processi completati per unita di tempo (*throughput*)
- Tempo di completamento (*turnaround time*)
	tempo che va dal caricamento del processo in memoria fino alla terminazione
- Tempo di attesa
	Tempo che il processo spende nella coda di ready
- Tempo di risposta
	Tempo necessario al processo per cominiciare a rispondere
### Algoritmi di schedulazione (microscheduler)
#### First Come First Served (FCFS)
E' un algoritmo non preemptive. Può capitare che un processo I/O bound debba aspettare processi CPU bound.
#### Shortest Job First (SJF) non-preemptive
E' un algoritmo ottimale (minore tempo di attesa), tuttavia occorre effettuare stime di quanto durerà un processo.
$$\tau_{n+1} = \alpha t_n + (1-\alpha) \tau_n$$
$\tau_{n+1}$ è la stima del prossimo CPU burst
$t_n$ è la durata del n-esimo CPU burst
$\alpha$ è un paramentro di peso
#### SJF preemptive
Variante con sospensione dell'esecuzione dell'algoritmo SJF

#### Schedulazione a priorità
Si associa una priorità numerica ad ogni processo (minore è il numero, maggiore è la priorità).
Si eseguono per i primi i processi a priorità maggiore, come i processi real-time (processi multimediali, realtà virtuale).
- Le priorità possono essere definite internamente o esternamente al S.O
Potrebbe capitare che i processi a bassa priorità non vengano mai eseguiti (**starvation**)
- Una delle possibili soluzioni è quella di far aumentare la priorità in base alla age del processo (**aging**)
#### RR
Ad ogni processo è assegnato un time slice di CPU. Per il resto l'algorimo si comporta come FCFS. Da utilizzare se si vuole minimizzare il tempo di risposta.
- Il time slice deve essere *sufficientemente maggiore* del tempo necessario al cambio di contesto effettuato dal **dispatcher** del S.O.
- Il turnaround time aumenta al diminuire della durata dei quanti, considerando il tempo per il context-swtiching
#### Coda multilivello
La coda di ready è ripartita in più code. Ad esempio:
- Coda processi in foreground (RR per il tempo di risposta)
- Coda processi in background (FCFS  perchè i processi sono CPU bound)
Ogni coda può avere un algoritmo di schedulazione differente.
Il sistema operativo può assegnare a ciascuna coda
- Un numero di priorità
- Un time slice
Si possono prevedere metodi per far muovere i processi tra code per prevenire la starvation

### Schedulazione nei [[Tipologie di sistemi di calcolo#Sistemi paralleli|sistemi multiprocessore]]
Si può suddividere il carico nei seguenti modi:
- Assegnare una coda di ready ad ogni proecssore
- Condivisione dei processi nella coda di ready
### Schedulazione nei sistemi hard real-time
I sistemi hard real-time devono garantire l'esecuzione di un processo in un determinato intervallo di tempo
#### Schedulazione Earliest Deadline First (EDF)
La CPU esegue i processi che hanno la scadenza più vicina
#### Schedulazione a frequenza monotona
Viene assegnata una priorità maggiore ai processi che vengono eseguiti con maggiore frequenza.
SI può optare anche per algoritmi preemptive come
-  round robin
- schedulazione a priorità fissa

### Schedulazione a livello thread
Avviene su due livelli
- Schedulazione locale (*Process Contention Scope*)
	La libreria dei thread decide quali thread a livello utente inserire in un thread livello kernel (mappatura molti a molti)
- Schedulazione globale  (*System Contention Scope*)
	Decide quali thread kernel mandare in esecuzione per prima (mappatura uno ad uno)

# Referenze