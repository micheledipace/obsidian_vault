10-07-2026 15:41
Tags: [[Sistemi Operativi]]

# Memoria Centrale
La memoria centrale è un vettore di word, l'unità fondamentale di informazione gestibile dal processore.
Un [[I Processi|processo]] per essere eseguito deve essere caricato in memoria centrale.
Il programma deve essere collegato ad un indirizzo di memoria valido.
Il collegamento avviene in tre fasi
- Fase di compilazione
	Il compilatore può generare indirizzi di memoria assoluti se si conosce a priori la posizione del processo in memoria.
- Fase di caricamento
	Altrimenti il compilatore deve generare del codice *rilocabile*. L'indirizzo di memoria del processo viene calcolato appena prima che il programma venga eseguito, a partire dalla prima zona contigua di RAM.
- Fase di esecuzione
	La Memory Management Unit (MMU) si occupa di tradurre gli indirizzi e della rilocazione (*caricamento dinamico*).
### Linking Dinamico 
Tecnica per cui non è necessario che ogni processo disponga di una copia delle librerie di sistema.
- Una piccola porzione di codice (*immagine*) è predisposta ad individuare la libreria desiderata e caricare le procedure della libreria rimpiazzando se stessa.
- Il sistema operativo controlla se la procedura richiesta è in uso da un altro processo e ne abilita l'accesso mantenendo i meccanismi di protezione della memoria
### Swapping
Tecnica che sposta un processo in stato di riposo nella memoria secondaria per essere poi ricaricato in memoria successivamente. E' praticabile grazie al linking dinamico.
- Un processo in attesa di I/O, anche se asincrono **non** può essere spostato nella memoria secondaria.
- Il tempo richiesto per lo swap è proporzionale alla quantità di memoria occupata dal processo. E' necessario assicurarsi che il tempo di esecuzione sia maggiore del tempo necessario per lo swap.
I moderni S.O utilizzando questa tecnica non appena viene superata una soglia di occupazione della memoria centrale.
### Metodi di allocazione
#### Allocazione contigua 
- A partizione singola
	Ogni indirizzo logico non deve superare il valore del registro limite. Il registro di rilocazione si occupa di non far interferire gli indirizzi di memoria dei vari processi.
- A partizione multipla
	Il sistema operativo cerca un blocco di memoria libero (*hole*) in cui caricare tutto il processo
#### Allocazione dinamica
Ci sono diverse tecniche per assegnare blocchi liberi a processi che devono essere caricati in memoria
- First-fit
	Primo blocco sufficientemente grande
- Best-fit
	Cercare lungo tutta la memoria il più piccolo blocco sufficientemente grande
- Worst-fit
	Cercare lungo tutta la memoria il più grande blocco libero.
#### Problema della frammentazione
- Frammentazione esterna
	La memoria disponibile è sufficiente per caricare il processo, ma	i blocchi liberi di memoria non sono contigui.
	Mitigabile con paginazione e segmentazione
- Frammentazione interna
	Il blocco è troppo grande rispetto al processo e la differenza non viene sfruttata.
### Paginazione
Attraverso questa tecnica lo spazio degli indirizzi fisici può non essere contiguo.
- Viene suddivisa la memoria fisica in **frame** di dimensione fissa.
- Viene suddivisa la memoria logica in **pagine** di dimensione uguali a quelle di un frame.
La dimensione di un indirizzo logico è definita dall'hardware ed è diviso in due parti:
- Numero di pagina (p)
	E' l'indice della tabella delle pagine
- Spiazzamento nella pagina (displacement - d)
	Viene utilizzato per calcolare l'indirizzo di memoria fisico
Se la dimensione di un indirizzo logico è $2^n$ e abbiamo a disposizione $m$ bit di indirizzamento (hardware), il numero di pagina occupa $m-n$ bit, mentre il displacement ne occupa $n$ 

#### Protezione della memoria
- Ogni entry ha un bit di protezione che stabilisce se la pagina è read only o rw.
- Un registro della lunghezza delle pagine verifica che ogni processo sta accedendo ad uno spazio di memoria a sè riservato. (*Page-Table Length Register*)

#### Translation Look-aside table (TLB)
Cache che contiene gli indirizzi di memoria usati più frequentemente
#### Tempo di accesso effettivo (EAT)
Il tempo di accesso ad un indirizzo può variare se questo è presente nella TLB.
Per calcolare il tempo effettivo si ricorre alla media pesata
$EAT = (\beta + \epsilon) \alpha + (2\beta + \epsilon)(1-\alpha)$
- $\beta$ è il tempo di accesso alla memoria
- $\alpha$ è l'hit ratio della TLB
- $\epsilon$ è il tempo di accesso alla TLB
#### Paginazione gerarchica (64 bit)
La page map table (PMT) è paginata. Una tabella esterna contiene i riferimenti delle pagine.
#### Paginazione a due livelli
Utilizzata per evitare che le page table occupino troppa memoria.
I bit allocati al numero di pagina si dimezzano (caso di due page table).
Per sistemi a 64 bit si utilizzano tre livelli.
#### Paginazione con funzione di hash (64 bit)
Il numero di pagina è messo nella funzione di hash che ha come risultato l'indice del frame fisico corrispondente.
#### Paginazione invertita (64 bit)
Ciascuna entry della tabella delle pagine invertita è un **frame fisico** associato ad un solo processo.
- Ogni riga è composta da PID del processo, numero di pagina logica e displacement. L'indice di tabella è un riferimento al frame fisico.
- Questa tecnica evita che le page table occupino troppa memoria.
	Esiste solo una page table inversa per l'intero sistema.
- Una singola tabella di hash permette di trovare subito il frame fisico desiderato.
- Rende difficile l'implementazione della multiprogrammazione.
	La condivisione delle pagine permette di associare più indirizzi virtuali ad un solo indirizzo fisico.
### Segmentazione 
Suddivisione della memoria logica in unità logiche (*segmenti*). Non risolve del tutto il problema della frammentazione esterna.
- L'indirizzo segmentato è composta da <numero del segmento, spiazzamento>
- La tabella dei segmenti è divisa in base e limite
- La base è l'indirizzo fisico di partenza (contenuto nel *registro base del segmento dalla pagina*)
- Il limite è la lunghezza del segmento (contenuto nel *registro della lunghezza del segmento della pagina*)
#### Protezione della memoria
Vengono associati bit di validità ad ogni segmento.
E' possibile associare una tabella dei segmenti per ogni processo
- E' possibile che processi condividano informazioni a livello di segmento
### Segmentazione paginata
La tabella dei segmenti ha l'indirizzo per la tabella delle pagine relativa a quel segmento.
Inoltre lo spazio logico è diviso in due tabelle dei segmenti:
- Local Descriptor Table per i segmenti privati
- Global Descriptor Table per i segmenti condivisi.
Le entry di queste due tabelle comprendono informazioni sul segmento, compresa base e limite
L'indirizzo logico è dato dalla coppia <selettore, spiazzamento>
- Selettore <s,g,p> (s = numero segmento, g=bit LDT o GDT, p= bit protezione)
- spiazzamento 
Questa tecnica richiede tre accessi alla memoria.
![[segmentazione_paginata.png]]
# Referenze