09-07-2026 09:49
Tags: [[Sistemi Operativi]]

# Tipologie di sistemi di calcolo
Un **sistema operativo** è un insieme di programmi che agisce da intermediario tra utente e hardware. Di quest'ultimo ne *controlla* e *coordina* l'uso semplificando l'interazione tra utente e macchina
Ogni sistema di calcolo è formato da:
- Hardware
- Programmi applicativi
- Utenti
- Sistema operativo
#### Sistemi mainframe
- Di grandi dimensioni
	Offrivano elevate prestazioni (per l'epoca) e affidabilità. Servivano centinaia di utenti
- Nessuna interazione diretta con l'utente.
	Un operatore inseriva il *job* (programma + dati) da eseguire su schede perforate o nastri.

#### Sistemi mainframe batch
- Il monitor residente (precursore del kernel) gestiva l'esecuzione di job simili tra loro.
- L'intero sistema rimaneva in attesa durante le operazione di I/O
	L'hardware restava inutilizzato per la maggior parte del tempo

#### Sistemi multiprogrammati
- La CPU rivolge l'attenzione ad un processo alla volta tra quelli presenti in memoria
	I sistemi operativi moderni applicano tecniche di multi tasking e scheduling decisamente più avanzate di quelle dei primi sistemi multiprogrammati.
	- Gestione della concorrenza tra job
	- gestione della cooperazione tra job
	- CPU scheduling
	- Job scheduling
	- Gestione della memoria disponibile (es. swapping)
#### Sistemi desktop
Sistemi rivolti a singoli utenti (Personal computer)
#### Sistemi paralleli
Sistemi che hanno più CPU in comunicazione tra loro
- AMP (Asymmetric multiprocessing)
	Una CPU master organizza il lavoro per le CPU slave
- SMP (Symmetric multiprocessing)
	Le CPU condividono le risorse e l'SO si occupa della gestione della concorrenza tra processi.
#### Sistemi distribuiti
Sistemi in cui l'elaborazione è divisa tra diversi processori fisicamente distanti tra loro.
- La comunicazione avviene attraverso la connessione attraverso una rete.
	Le risorse possono essere condivise su macchine virtuali.
- Architettura client-server o P2P
#### Sistemi cluster
Sistemi che si avvalgono della tecnica della condivisione di una o più periferiche (*clustering*).
Ogni nodo del cluster esegue la stessa task (cluster simmetrico)
#### Sistemi real-time
Utilizzati in scenari in cui il completamento dell'operazione in un certo vincolo di tempo è safety-critical (*hard real-time*).
Sistemi *soft real-time* danno priorità a task avanzati per aumentare la quality of service (campo multimediale)
#### Sistemi mobile
Tengono conto delle capacità computazionali limitate e delle dimensioni ridotte dei dispotivi mobile





# Referenze