09-07-2026 16:59
Tags:[[Sistemi Operativi]]

# I Processi
###  Concetto di Processo
Un processo è un **programma in esecuzione**. Comprende
- Codice 
- dati (temporanei e variabili globali)
- memoria allocata
- registri CPU 
Due processi associati al medesimo programma sono considerate due istanze di esso (thread)

### Process Control Block
E' una struttura dati del kernel che contiene le informazioni relative ad un processo. Viene creata quando il processo passa dalla coda di hold alla coda di ready (prima richiesta di esecuzione).
Comprende:
- Stato del processo
- Registri CPU 
- Informazioni per la schedulazione (priorità, time slice)
- Valore del registro base/limite del processo
- CPU%, MEM%
- **Program Counter**
	Indirizzo di memoria della prossima istruzione da eseguire
- Informazioni sullo stato dell I/O
### Stato di un processo
- new 
	Le richieste per la creazione di nuovi processi vengono inserite nella **coda di submit**. Il macroscheduler riorganizza le richieste in base alle priorità del sistema nella **coda di hold**
- running 
   processo attualmente in esecuzione
- waiting (coda di wait)
	processo in attesa di I/O, interrupt, della terminazione di un suo child
- ready (coda di ready)
	in attesa di essere assegnato alla CPU. Il microscheduler si occupa dell'ordine dei processi nella coda di ready ed effettua il cambio di contesto necessario affinchè la CPU si occupi di un altro processo. **La CPU è ferma** durante il cambio di contesto (*context switching*) effettuato dal dispatcher.
- terminated
### Dispatcher
Modulo del S.O che effettua il cambio di contesto per la CPU.
La *dispatch latency* è il tempo necessario a gestire il cambio di contesto.
- Se il cambio di contesto deve avvenire durante l'esecuzione di una chiamata di sistema, il kernel deve garantire la consistenza dei dati.
	Nelle routine di sistema vengono inseriti dei *preemption point*, porzioni in cui il sistema è in uno stato sicuro per effettuare il context-switching verso un processo a più alta priorità.
### Schedulazione 
Ogni S.O ha tre diversi schedulatori
#### Schedulatore a lungo termine
- Bilanciare i processi I/O bound (short burst) e CPU bound
- Controllare il livello di multiprogrammazione (*numero di processi in memoria*)
- Eseguito con una frequenza nell'ordine dei minuti
#### Schedulatore a medio termine
- Riduce temporaneamente il grado di multiprogrammazione attraverso la tecnica dello swapping su disco
#### Schedulatore a breve termine
- Si occupa di selezionare l'ordine dei processi nella coda di ready.
- Eseguito ogni 100ms
### Creazione e terminazione
Un processo *padre* può creare processi *figli*. In un sistema operativo ogni processo è figlio del processo `init` (PID=1)
- Padre e figli condividono le risorse, un sottoinsieme di queste o non condividono le risorse
- Il padre può concorrere con i suoi figli o aspettarne la terminazione
- Il figlio può essere un duplicato del padre o avere un nuovo programma caricato nel suo spazio di memoria (*spazio di indirizzamento*)
#### System call `fork()` 
   La primitiva `fork()` crea una copia del processo padre con alcune differenze
- Il processo figlio ha un PID unico
- Il PID del processo padre è diverso da quello di quest'ultimo
- Se il nuovo processo è creato correttamente, ritorna un valore di 0 al processo figlio e il PID del processo figlio al processo padre 
#### System call `exec()` 
Si occupa di caricare un nuovo programma nello spazio di memoria di un processo.
#### System call `exit()`
Richiesta al sistema operativo di rimuovere il processo dal sistema e la deallocazione delle sue risorse.
- Ritorna un valore di stato al processo padre che potrebbe star aspettando la sua terminazione con la system call `wait()`.
Il processo padre può terminare l'esecuzione dei suoi processi figli per varie ragioni:
- Processo figlio non più necessario
- Processo figlio ha ecceduto nell'utilizzo delle risorse

### Cooperazione tra processi 
La cooperazione tra processi ha numerosi vantaggi se gestito da opportune strategie di sincronizzazione:
- Condivisione delle informazioni
- Esecuzione in parallelo
- Modularità
- Convenienza
#### Paradigma produttore consumatore
- Un processo produce informazioni che un altro processo elaborerà. 
- Per gestire la concorrenza tra processi, le informazioni prodotte sono salvate in buffer di dimensione fissa o illimitata.
### Comunicazione tra processi  (IPC)
E' la condivisione di informazioni tra processi. Fornisce due operazioni:
- `send(msg, P)` 
- `receive(msg, Q)` 
#### Comunicazione diretta
- Fra ogni coppia di processi esiste una sola connessione
- I processi devono conoscere destinatario e del mittente
- L'indirizzamento può essere asimmetrico se il messaggio non è ricevuto dal mittente
#### Comunicazione indiretta (mailbox)
- Ogni mailbox ha un identificatore univoco. 
- Una mailbox può appartenere ad un singolo processo o al sistema operativo
- Una connessione può essere associata a due o più processi ->  concorrenza gestita dal SO
#### Sincronizzazione
- Invio bloccante (sincrono)
	Il processo si blocca fino alla ricezione del messaggio da parte del destinatario
- Ricezione bloccante (sincrono)
	Il ricevente è in attesa di un messaggio
- Invio non bloccante (asincrono)
	Il processo riprende l'attività dopo l'invio
- Ricezione non bloccante (asincrona)
Invio bloccante + Ricezione bloccante = *rendezvous*
#### Coda dei messaggi 
I messaggi in attesa sono inseriti in una coda, le cui dimensioni possono variare.
- Capacità zero 
	Nessun messaggio può rimanere in attesa (rendezvous)
- Capacità limitata
	L'invio è bloccante solo se la coda è piena
- Capacità illimitata
	L'invio è sempre non bloccante
#### Comunicazione su un'interfaccia di rete
Un **socket** è l'endpoint per ricevere e manadare messaggi lungo un'interfaccia di rete.
E' univocamente individuato da protocollo, indirizzo IP, e numero di porta
#### RPC (Remote Procedure Call)
Esecuzione di una procedura su uno spazio di indirizzamento diverso a quello del processo che chiama la **RPC**. 
Se la procedure risiede su un computer remoto, gli *stub* si occupano della traduzione dei parametri (marshalling) e di invocare la procedura lato server (client-side = proxy/server-side = skeleton).
Le RMI Java rappresentano le RPC su procedure che risiedono su differenti Java Virtual Machine.


# Referenze