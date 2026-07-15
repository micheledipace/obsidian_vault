14-07-2026 09:43
Tags: [[Sistemi Operativi]]

# Android
Sistema operativo per dispositivi mobile.
- E' un progetto open source capitanato da Google (*Open Handset Alliance*)
- deve supportare migliaia di dispositivi con hardware diverso 
	smartphone, tablet, televisioni, wearables
- Basato su kernel linux customizzato
	ne condivide driver e moduli kernel
- E' uno stack software a 5 livelli 
	1. Applicazioni di sistema
	2. Application Framework
	3. Librerie native e runtime (*Dalvik* e *Android Runtime*)
	4. Hardware Abstraction Layer
	5. Kernel e Driver
### Modifiche al Kernel Linux
- Low memory killer personalizzato e adattato alle capacità di memoria limitate dei dispositivi mobile
- Gestione dell'energia basata sui **wakelocks**
- Comunicazione tra processi gestita da **Binder IPC**
	metodo di comunicazione tra due processi completamente trasparente.
- servizio di logging *logcat*
#### Gestione della memoria
il demone *lmkd* si occupa di liberare spazio in memoria centrale sfruttando il concetto di *pressione* della memoria. lmkd legge il parametro *vmpressure* e verifica che il kernel stia effettivamente riscontrando rallentamenti dovuti alla mancanza di memoria.
Il demone terminerà tutti i processi non essenziali per le funzionalità base del sistema al fine di alleviare pressione.
#### Gestione dell'energia
Si basa sul meccanismo dei wakelock, che impedisce al dispositivo di entrare in modalità di sospensione.
In assenza di wakelock, android disattiva le risorse per risparmiare energia (sospensione dello schermo, riduzione della luminosità,...).
Android integra anche moduli di gestione dell'energia del kernel linux
#### Comunicazione tra processi
Il Binder (*OpenBinder*) è il sistema di IPC sincrona di Android. 
- Fornisce un canale di comunicazione di oggetti tra processi
- Ogni processo ha un pool di thread che si occupano della comunicazione
- Tiene traccia dei puntatori ad un oggetto attraverso il *reference counting*
#### File System
Opportunamente scelti per rendere più efficienti e affidabili le memorie flash.
##### Caratteristiche di una memoria flash
- No seek time (nessuna testina da muovere)
- Block erasing
	Un blocco di dati deve essere esplicitamente cancellato per poter essere riutilizzato per la scrittura di nuovi dati
- Wear leveling
	Il numero di scritture su una cella di memoria è limitato.
### Hardware Abstraction Layer
Metodo di astrazione dell'hardware per i layer superiori. Fornisce un'interfaccia standardizzata per accedere ai metodi dei driver a basso livello.
- Ogni vendor deve definire un'interfaccia HAL scritta nel linguaggio HAL Interface Definition Language
### Librerie native
Comprende le funzionalità essenziali del sistema. L'accesso ad esse non è diretto, ma avviene tramite framework.
- BioniC
	Libreria standard C più leggera e veloce di glibc
- SQLite
- Media frameworks
- WebKit/Blink
- FreeType
- Surface Manager
### Android Runtime
Un sistema runtime è un sotto sistema che fornisce un ambiente in cui eseguire un programma. Ogni applicazione android viene eseguita in un Android Runtime che mantiene la compatibilità con il suo predecessore Dalvik. Le VM di ART sono register-based per rendere più efficiente l'utilizzo della CPU.
ART può eseguire 
- bytecode .dex compilato Just-In-Time (Hot-Code) o interpretata (Cold-Code)
- codice binario .oat compilato *Ahead of Time*
	generato dal compilatore *dex2oat* mentre il dispositivo è idle o in ricarica
Il processo **Zygote** è il processo padre di tutte le istanze di ART
### Application Framework
Insieme di librerie e software che forniscono l'ambiente e i servizi necessari per l'esecuzione delle app. Le API fornite dai *Manager* dell'Application Framework permettono l'accesso alle funzioni native.
- Resource Manager
- Notification Manager
- Telephony Manager
- Location Manager
- Window Manager
- Package Manager
- Content Provider
	consente alle applicazioni di accedere a dati di altre applicazioni
- View System
	gestisce l'insieme degli elementi che costituiscono l'UI
### Applicazioni di sistema 
- Sono scritte in Kotlin o Java e sono impacchettate in un file .apk che contiene il .dex e risorse utili all'applicazione.
- Ogni applicazione è eseguita in un'istanza di ART. Ogni istanza di ART ha un univoco linux UID
- Hanno diversi entry point 
### Meccanismo di start-up del sistema
Il processo init:
- inizializza i demoni di sistema 
- inizializza il processo Zygote
- inizializza il processo Runtime che avvia il manager dei servizi
#### Il processo Zygote
- è in ascolto sul proprio socket di richieste di istanza di ART. Ogni istanza di ART è un *fork* del processo Zygote al fine di ottimizzare le risorse.
	le risorse sono duplicate solo in fase di scrittura
- Avvia il processo Service Manager che gestisce i Manager presenti nell'Application Framework
# Referenze