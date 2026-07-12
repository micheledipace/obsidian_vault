12-07-2026 09:54
Tags: [[Sistemi Operativi]]

# File System
Il file system è il componente del sistema operativo che gestisce e organizza i file nella memoria secondaria. La memoria secondaria è suddivisa in **blocchi**. 
Un sistema operativo gestisce più file system attraverso un'interfaccia chiamata *Virtual File System*
### Struttura di un file
Dal punto di vista dell'utente, un file è l'unità logica di memoria. Tuttavia, un file può occupare più blocchi di memoria, oltre ad utilizzare un ulteriore blocco speciale (*blocco di controllo di file*) che contiene i metadati (nome, permessi, proprietario...).
### Directory
I file sono organizzati in directory. Una directory può essere implementata come:
- Una lista di nomi con puntatori ai blocchi di dati 
	Complessità computazionale $O(n)$ per la ricerca
- Una tabella di hash 
	Complessità computazionale $O(1)$ per la ricerca. Richiede la gestione delle collisioni e del linking dinamico man mano che il file system aumenta di grandezza.
### Metodi di allocazione
E' possibile utilizzare diverse strategie per collegare i blocchi di dati ai file
#### Allocazione contigua
Ogni file occupa blocchi di dati contigui tra loro. Un file è definito dal file system dall'indirizzo del blocco iniziale e dal numero di blocchi.
Vantaggi:
- Accesso sequenziale e diretto (senza tabella di allocazione)
Svantaggi:
- I file non possono essere ampliati. E' possibile allocare estensioni di blocchi contigui per aumentare la dimensione del file.
- Spreco di spazio (frammentazione e bit di validità)
#### Allocazione collegata
Ogni file è una lista di blocchi collegati tra loro. Il file system ha bisogno solo del blocco iniziale collegato al file.
 Vantaggi:
 - Eliminazione della frammentazione
Svantaggi:
- Nessuna possibilità di accesso casuale.

#### File Allocation Table (FAT)
Una tabella di linked list associano un file e i rispettivi metadati alla loro lista di blocchi di dati. Il formato FAT 32 ha un limite di dimensione per file di 4GB
#### Allocazione indicizzata
Ogni file punta al proprio blocco indice (*i-node*). Il blocco indice punta ai blocchi di dati.
- In Unix ogni blocco ha dimensione di 4KB.
- Si utilizza l'indicizzazione multilivello per aumentare la dimensione massima che un file può assumere.
### Gestione dello spazio libero 
Una mappa di bit che tiene traccia dei blocchi liberi e di quelli occupati è salvata in memoria centrale. Questo metodo richiede che la mappa sia sempre salvata in memoria. Sono possibili anche tecniche di raggruppamento e conteggio.
#### Dimensione della bitmap
Per un disco di $1 GB = 2^{30} B$ e blocchi di $4KB$ , il numero di blocchi presenti sul disco è$$
n = \frac{2^{30}B}{2^{12}B} = 2^{18}.
$$
Sono necessari $2^{18}$ bit per mappare l'intero disco.

### Prestazioni
Le prestazioni del file system possono migliorare implementando strategie di caching del disco, ottimizzazione dell'accesso sequenziale (*free-behind e read-ahead*) e [[Memoria Virtuale|mappando in memoria l'I/O]]. 

### Recupero dei file
- Copia effettuata su un supporto fisco esterno (*backup*)
- Logging delle [[Transazioni|transazioni]] (proprietà ACID) per file system orientati alle transazioni.
# Referenze