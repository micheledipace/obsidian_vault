13-07-2026 12:08
Tags: [[Sistemi Operativi]]

# NuttX
E' un sistema operativo hard real-time open-source. NuttX è alla base di sistemi operativi realtime come TizenRT e Motorola MotoMod
### Peculiarità
- Compilato anche per microcontrollori
- API Posix
- API Unix (Nuttshell e VFS)
- Kernel modulare
- Ampia gamma di architetture supportate
### Architettura di NuttX
Ha struttura stratificata
- User Layer
	Layer di comunicazione con l'utente e librerie POSIX. 
- OS Layer
	Funzionalità base del sistema operativo (IPC, scheduling e driver). I driver sono organizzati in 
	1. Upper half driver: offre metodi indipendenti dall'hardware
	2. Lower half driver: comunicano con gli upper half driver attraverso interfacce comuni, specifiche per la categoria di hardware con cui comunicano.
	
### Task in NuttX
Sono simili ai processi di un S.O general purpose. Ogni task ha un proprio ID e una tabella che contiene i suoi metadati (*Task Control Block*).
Sono organizzati tramite relazioni *parent-child*
- child ereditano i file di stream (stdin/stdout)
- i parent **attendono** la terminazione dei processi figli per completare la loro esecuzione.
### IPC 
I segnali (segnali POSIX) vengono assegnati in una coda (*POSIX Message Queue*) associata ad ogni thread.
Inoltre semafori di tipo *signaling* mandano un segnale di wait se la risorsa è occupata oppure segnalano che la risorse è libera.

### Scheduling e stato di un processo
- inactive_tasks
	task inizializzati ma non ancora attivati
- readytorun
	lista dei task pronti a partire. In testa c'è il task correntemente in esecuzione, in coda i task in idle
- pendingtasks
	- task pronti per l'esecuzione, ma non selezionati dallo [[Schedulazione della CPU|scheduler a frequenza monotona]].
- blocked
	task che aspettano di ricevere un segnale o di ottenere l'accesso a risorse condivise.
- running
	il processo è in esecuzione

### File System
E' uno pseudo file-system generato al volo su richiesta dell'utente (*on-the-fly*) e caricato in RAM. Ha una struttura ad albero ed è stato implementato per utilizzare le interfacce POSIX
- E' estensibile
	L'eventuale storage esterno è montato nella cartella /mnt
- I dispositivi sono file a blocchi presenti nella cartella /dev
- I driver sono registrati come nodi nel file system
### Sottosistema grafico NX
Utilizza un *modello client/server* simile ad X-Window chiamato NX.
- I client sono i thread associati ad ogni finestra dell'interfaccia grafica
- Il server è il backend che fornisce le primitive per le operazioni grafiche e di rendering oltre che a provvedere ai servizi I/O per tastiere e mouse.
- NxWidgets è una libreria per l'integrazione di oggetti grafici all'interno di NX
### Interprete dei comandi NuttShell (NSH)
E' basata sulla shell BASH. Eredita i comandi principali da Linux. E' possibile configurarla modificando il file *defconfig*
Di default all'avvio:
1. NSH crea un file-system minimale con il solo file /init.d/rcS. Questo file system viene caricato in RAM
2. NSH monta il file-system appena creato nella cartella /etc
3. NSH esegue lo script in /etc/init.d/rcS non appena prima di ricevere il primo prompt.
4. lo script monta un file-system temporaneo nella cartella /tmp
# Referenze