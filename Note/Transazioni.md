01-06-2026 17:43
Tags: [[Basi di Dati]]

# Transazioni
Una transazione è *un'unità elementare* di lavoro. Una transazione deve garantire le proprietà **ACID** 
- Atomicità
	Ogni transazione è incapsulata tra i due comandi `bot` ed `eot` e non può lasciare la base di dati in uno stato indeterminato.
	I comandi `commit` e `abort` definiscono le operazioni da riprovare o da annullare in caso di errore.
- Consistenza
	Le operazione di una transazione non devono intaccare la consistenza della base di dati. Il compilatore della DDL si occupa dei vincoli di tupla.
- Isolamento
	Ogni transazione è indipendente dalle altre. Transazioni concorrenti hanno lo stesso risultato di una serie di transazioni in sequenza.
- Durabilità
	Gli effetti di una transazione devono permanere nel tempo.
	I cambiamenti di un `commit` *non devono essere persi* 
#### Elementi del DBMS per garantire l'atomicità
- Gestore della memoria secondaria
	Garantisce affidabilità e l'isolamento delle transazioni (gestore della concorrenza)
	1. Si occupa della durabilità e dell'atomicità
	2. Si occupa dei ripristini
	3. Si occupa del logging
- Gestore del buffer
- Gestore dei metodi di accesso
- Gestore delle interrogazioni
### Logging e ripristino della base di dati
I file di log contengono informazioni per il ripristino dei dati a seguito di guasti. La perdita di questi file è considerato un *evento catastrofico*
- Log di transazione 
	registrano le operazioni effettuate durante una transazione
- Log di sistema 
	Registrano le operazioni effettuate regolarmente dal *controllore dell'affidabilità* 
	I **CHECKPOINT** registrano lo stato attuale del DB. Nessuna operazione deve essere in corso durante questa operazione.
	Il **DUMP** è una copia dell'intera base di dati su supporti fisici considerati sicuri 
#### Gestione dei guasti
- Soft failure
	I dati del DB sono intatti, ma può verificarsi la perdita di dati di cache e di buffer.
- Hard failure
	I dati del DB sono intaccati. E' necessario analizzare i file di log per ripristinare lo stato dei dati.
Applicando il metodo *Fail-Stop* il DB viene fermata non appena il DBMS rileva un fail.
#### Metodi di ripristino
- Ripresa a caldo per guasti di sistema
	1. Si parte dall'ultimo checkpoint se l'ultima transazione attiva non è più vecchia del checkpoint
	2. Si formano due insieme per le operazione da rieseguire e quelle da annullare
- Ripresa a freddo per guasti del dispositivo
	1. Si accede al dump
	2. Si applicano le operazioni al dump per tornare allo stato dei dati appena precedente al fail.
### Gestione della concorrenza
Deve gestire i possibili conflitti durante l'esecuzione concorrente di più transazioni.
- Perdita di aggiornamento
	Una transazione scrive dopo una lettura di un'altra transazione mentre quel dato è ancor in uso
- Lettura sporca
	Una transazione legge un dato che poi viene rollbackato da un'altra transazione
- Lettura inconsistente
	Una transazione deve sempre poter leggere lo stesso valore di uno stesso dato
- Aggiornamento fantasma
	Il database può ancora essere in uno stato consistente ma non per tutte le transazioni.
- Inserimento fantasma
	Una transazione inserisce un dato mentre è in esecuzione una funzione aggregata
### Gestione dei conflitti
Un conflitto nasce quando due o più transazioni cercano di accedere allo stesso dato.
Le *primitive di lock* effettuano un blocco per quel dato. Ogni blocco è registrato nella tabella dei conflitti
- r_lock 
	blocco in lettura. Il blocco non è esclusivo. 
- w_lock 
	blocco in scrittura. Il blocco è esclusivo
- unlock 
	rilascio della risorsa.
#### Tabella dei conflitti

| richiesta | libero   | r_locked                | w_locked              |
| --------- | -------- | ----------------------- | --------------------- |
| r_lock    | r_locked | aumenta il contatore    | rifiuta il lock.      |
| w_lock    | w_locked | transazione in attesa   | transazione in attesa |
| unlock    | errore   | diminuisce il contatore | libera la risorsa     |
#### Schedule serializzabili
Se una sequenza di operazioni è equivalente ad una sequenza seriale di transizioni questa è detta **serializzabile** 
Lo stesso vale per un conflitto.
#### Two phase locking 
E' utilizzato per garantire diversi livelli di isolamento
1. La prima fase innesca i lock
2. La seconda fase (*calante*) li rilascia solo al termine della transazione, avendo verificato la corretta esecuzione di tutte le operazioni di `commit` e `abort`.
Dopo la seconda fase **non possono essere acquisiti altri lock** da parte della stessa transazione.
Possono verificarsi deadlock.
Lock 2 fasi + transazione ben definita = schedule confilct serializzabile
#### Livelli di isolamento
- read uncommitted
	Nessun 2PL applicato
- read committed
	r_lock richiesto ma subito rilasciato
- repeatable read
	Applica il 2PL solo al livello di tupla
- serializable
	Applica il 2PL al livello di predicato (tabella)
#### Controllo a livello di timestamp
- se la lettura ha timestamp maggiore dell'ultima scrittura effettuata, l'operazione viene accettata. Altrimenti l'operazione viene uccisa
- se la scrittura ha timestamp maggiore dell'ultima scrittura effettuata, l'operazione viene accettata. Altrimenti l'operazione viene uccisa
# Referenze