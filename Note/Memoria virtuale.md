10-07-2026 18:09
Tags: [[Sistemi Operativi]]

# Memoria virtuale
E' uno spazio di memoria centrale simulata dal sistema operativo. Questa tecnica ha numerosi vantaggi:
- Isolamento della memoria fisica
- Maggiore facilità della gestione della condivisione delle risorse
- Caricamento dinamico 
	La pagina viene introdotta nella memoria fisica (frame) solo se è necessaria. Un bit di validità indica se la pagina è caricata in memoria.
- Copy on write
	Quando un processo padre condivide le sue risorse con i processi figli, gli indirizzi logici dei processi figli puntano agli indirizzi fisici del padre. Una copia viene creata quando uno di questi effettua una modifica sui dati.
- Mappatura in memoria (*Memory Mapped I/O*)
	Il sistema operativo mappa un blocco del disco ad una pagina in memoria centrale. Così facendo si può accedere al file attraverso una richiesta di paginazione: il file è ora una sequenza di indirizzi virtuali ai quali la CPU può avere accesso come se fosse una porzione di memoria secondaria. Questa tecnica velocizza le operazioni di I/O.
- Swapping
### Page fault
Interrupt (trap) che segnala una *mancanza di pagina*. Se l'indirizzo è valido, il sistema procede a caricare la pagina cercando un frame libero.  Degli algoritmi di schedulazione delle pagine sono impiegati in caso di mancanza di frame liberi.
### Algoritmi di sostituzione della pagina
Scelgono il frame vittima da liberare.
#### Algoritmo FIFO
Le pagine vengono caricate nei frame fisici secondo il paradigma FIFO. 
Esistono sequenze per cui aumentare il numero di frame fisici **fa aumentare** il numero di page fault (**Anomalia di Belady**)
#### Algoritmo Ottimale
Sostituire la pagina che non sarà usata per il più lungo periodo di tempo
#### Algoritmo Least Recently Used (LRU)
Si sostituisce la pagina caricata da più tempo. 
##### Implementazione con stack 
La pagina da caricare viene messo in cima alla pila. La pagina in fondo alla pila viene sostituita.
#### Algoritmo Most Frequently Used e Least Frequently Used
- MFU sostituisce la pagina più usata
- LFU sostituisce la pagina meno usata

### Allocazione dei frame
Il sistema operativo può allocare un numero di frame ad un processo in base a:
- livello di priorità
- specifica fissa
Inoltre un processo può:
- Caricare una pagina in un frame anche se è allocato da un altro processo
- Caricare una pagina solamente nei suoi frame allocati.
### Thrashing
E' il fenomeno per cui il numero delle page fault è così elevato da compromettere le perfomance del sistema. Un processo è in thrashing quando spende più tempo in richiesta di paginazione che in esecuzione.
Il fenomeno del thrashing avviene quando il *working set*, ossia l'insieme dei dati e delle istruzioni usate più di recente, del processo è maggiore alla porzione di memoria fisica libera.

# Referenze