09-07-2026 11:15
Tags:[[Sistemi Operativi]]

# Struttura di un sistema operativo
### Componenti
- Gestione dei processi
	deadlock, scheduling, sincronizzazione tra thread
- Gestione della memoria centrale
	paging, swapping, segmentation
- Gestione dei file
	supporto di file system
- Gestione dell' I/O
	gestione dei controller, interfaccia driver
- Protezione dell'hardware
	kernel-user mode, syscall
- Gestione della memoria secondaria
	gestire e allocare lo spazio libero, scheduling tra dischi
- Gestione delle reti 
- Interprete dei comandi (GUI o a caratteri)
	Riceve ed interpreta:
	- Istruzioni di controllo
	- Esecuzione di programmi richiesta dall'utente (script, built-in, esterni)
- Interfaccia grafica (opzionale)
### Servizi del sistema operativo 
- Caricamento in memoria ed esecuzione di un programma 
- Operazioni di I/O interrupt driven
- Manipolazione del file system 
- Comunicazione tra processi 
- Rilevamenti di interrupt non mascherabili
- Allocazione delle risorse 
- Logging e statistiche d'uso
- Protezione delle risorse
- Recuperare le informazioni riguardanti la configurazione hardware (SYSGEN)
### Chiamate di sistema
Sono un'interfaccia tra hardware e processi utente. Il kernel verifica se la richiesta è legittima e concede in *modo sicuro* (programmi di sistema) la risorsa al processo.
I parametri del processo richiedente sono passati in una tabella di memoria (LINUX) o in una pila.
### Architettura di un Sistema Operativo 

#### Organizzazione gerarchica 
Semplice organizzazione (MS-DOS)
#### Microkernel
Spazio kernel ridotto all'osso (scheduling, IPC, paging) lasciando la maggior parte delle funzionalità e servizi nel lato utente. Garantisce sicurezza e affidabilità al costo di un maggior context-switching
#### Kernel monolitico
Tutti i componenti del kernel sono caricati in un singolo livello. Può essere anche modulare come il kernel linux
#### Kernel ibrido
Composto da più architetture (Darwin, Windows NT)
#### Stratificato
Ciascun layer ha accesso ad operazioni sempre più a basso livello.
- Il livello 0 è l'hardware mentre il livello N è l'interfaccia utente. 
- Ciascuno strato è inacessibile dagli strati superiori
- Un maggior numero di strati comporta un maggior numeri di interfaccie per l'interazione tra strati.
### Macchine virtuali 
Ambiente che emula il comportamento di una macchina fisica attraverso la tecnica della virtualizzazione. 
- La macchina fisica ripartisce le proprie risorse verso una o più macchine virtuali (risorse virtuali)
- L'ambiente virtuale deve virtualizzare anche la modalità kernel della macchina fisica (l'ambiente è ovviamente eseguito in modalità utente)
- La richiesta di istruzione privilegiata sulla VM viene passata alla modalità kernel virtualizzata.
- Questo processo garantisce l'isolamento di una macchina virtuale all'hardware delle macchina fisica e ad altre istanze di macchine virtuali.
###  Obiettivi
- Obiettivi utente: facilità di utilizzo, sicurezza, affidabilità
- Obiettivi sistema: facilità di manutenzione e di progettazione, efficienza
# Referenze