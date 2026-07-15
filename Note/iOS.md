13-07-2026 09:42
Tags: [[Sistemi Operativi]]

# iOS
E' un sistema operativo *closed source* sviluppato da Apple. E' utilizzato sulla maggioranza dei dispositivi Apple con le sue varianti *watchOS* e *tvOS*. E' strettamente legato a macOS
### Principi cardine
- Ha componenti open source
	Il sistema operativo che fa da nucleo **Darwin**, diversi framework come *WebKit* e i linguaggi **Swift** e **Objective-C** oltre ai compilatori come *Clang*
- App-centrico
	Anche l'UI (*Springboard*)
- Interazione diretta con tocco e gesti
- Design consistente
- Privacy e sicurezza
### Architettura di un'App
Il software è installabile quasi esclusivamente dall'App Store per le politiche di privacy e sicurezza di Apple.
#### Componenti  (Model-View-Controller design pattern)
- Model
	Comprende le strutture dati e la logica dell'applicazione
- Controller
	Intermediario tra model e view. Aggiorna i contenuti delle view e segnala al model cambiamenti dovuti all'input dell'utente.
- View
	Componenti relativi all'interfaccia utente. Mostra informazioni all'utente e riceve input da questo. Ogni view è un *rettangolo* sullo schermo e può essere organizzato in modo gerarchico
#### Ciclo di vita
- Not running
- Inactive (foreground)
	L'app è in foreground, ma non riceve eventi
- Active (foreground)
- Background
	L'app esegue operazioni in background
- Suspended
	L'app non esegue operazioni in background

### Architettura del sistema
iOS ha una struttura stratificata. 
#### Cocoa Touch
E' il framework per lo sviluppo di applicazioni per iOS. E' basato su Cocoa per macOS e modificato per l'interazione touch.
Comprende sub-framework come:
- UI Kit
	Interfaccia per gestire tutti gli elementi visivi (finestre e view) e come interagiscono con l'utente e con altre app. Inoltre gestisce l'accesso alla sensoristica, il ciclo di vita, animazioni, schedulazione e ricezione notifiche, TUTTO
- ContactsUI
	Interfaccia per l'accesso ai contatti
- MapKit
	Mappe e geolocalizzazione
- Message UI
	Interfaccia per la composizione di email
#### Media Layer
- Core Image
	Framework di manipolazione delle immagini e riconoscimento di volti e oggetti.
- AVFoundation
	Framework multimediale di alto livello per la riproduzione, cattura e processing di video e audio.
- CoreAudio/CoreVideo
	Framework multimediale di basso livello
- CoreGraphics
	Rendering 2D. 
- CoreAnimation
	Utilizzata per il rendering delle view.
- OpenGL/Metal
	API di rendering 3D. Metal è l'API grafica proprietaria di Apple.
#### Core Services
- Foundation
	Comprende le strutture dati base del sistema.
- CoreData
	framework per la gestione e la persistenza dei dati. I dati sono in relazione tra loro come nodi di un grafo.
- CoreLocation
	Servizio per ricavare la posizione del dispositivo attingendo dai dati forniti dai sensori integrati (barometro, GPS, altimetro).
- CoreMotion
	Framework che consente l'accesso ai dati di movimento rilevati dai sensori integrati (giroscopio, accelerometro).
- WebKit
	Motore per il rendering di pagine web.
#### CoreOS
Il livello più basso dell'ambiente user
- libSystem
	librerie base per il funzionamento del sistema come la libreria C e chiamate di sistema POSIX.
- Accelerate
	Librerie per il calcolo vettoriale e matriciale.
- SystemConfiguration
	Framework per l'accesso alla configurazione di rete del dispositivo.

#### Kernel e Driver
- Darwin 
	E' il nucleo di iOS. E' basato su Kernel XNU e userspace BSD.
- I/O Kit
	Framework che fornisce astrazione hardware per i layer a più alto livello.
- Filesystem APFS
- Secure Boot Chain
##### Kernel XNU
Kernel Ibrido formato dal microkernel Mach e dal kernel monolitico BSD.
Il microkernel Mach si occupa di:
- IPC
- CPU scheduling
- RPC
- supporto soft real-time
- Thread lato kernel
- Memoria virtuale e paginazione
Il kernel BSD fornisce:
- **protezione della memoria**
- funzioni di networking
- modello e controllo dei processi
- API posix
- modello di sicurezza UNIX
- thread lato utente
- interazione con i file system
##### Architettura dell' I/O Kit
- Family
	Collezione di astrazioni comuni per categorie di hardware
- Driver
	Oggetti che gestiscono direttamente uno specifico hardware. Hanno bisogno delle astrazioni fornite dalla *Family*
- Nub
	Canale di comunicazione per un dispositivo. Può rappresentare una tastiera, un mouse, un disco. Agisce come ponte tra due driver e per estensione per due famiglie.
##### Apple FileSystem
File system proprietario e moderno (2016). Ha diverse features:
- Copy on Write
	Il dato copiato viene effettivamente scritto su disco solo se questo viene modificato.
- inode a 64 bit
- Possibilità di effettuare snapshots
- Ridimensionamento dinamico delle partizioni
- Crittografia a **chiave singola o multipla**
##### Secure Boot Chain
Sequenza di avvio del dispositivo. E' composta da tre stadi. Ogni stadio verifica l'integrità e in caso di successo decritta la fase successiva.
- BootROM
	firmware salvato su una ROM dedicata. Contiene le prime istruzioni e la *root CA key* della chain of trust. Se questo stadio fallisce il dispositivo entra in modalità DFU (*Device Firmware Upgrade*)
- Low level Bootloader (opzionale)
	effettua routine per verificare l'integrità dello stadio successivo e operazioni di setup.
 - iBoot (Stadio di BOOT)
	 Verifica l'integrità del kernel XNU e ne lancia l'esecuzione (Stadio FSYS).
	 Se questo stadio fallisce il dispositivo entra in modalità di recovery
### Feature di sicurezza
- secure boot chain
- Secure Enclave Processor
	Hardware che si occupa di mantenere sicuri i dati sensibili dell'utente anche in caso di sistema compromesso.
- Motore per la crittografia AES-256
- Write XOR Execute (W^X)o
	Una pagina di memoria non può essere eseguita e modificata contemporaneamente.
- Kernel Address Space Layout Randomization (KASLR)
	kernel caricato ad indirizzi di memoria casuali
- Kernel Integrity Protection (KIP)
	Impossibilità di scrivere sul kernel una volta terminata la fase di boot
- Pointer Authentication Codes (PAC)
	I puntatori ad indirizzi di memoria critici sono crittografati.
- Sandboxing delle app basata sulle autorizzazioni
- Firma delle app da parte di apple (*code signing*)
- Entitlement
	Le autorizzazioni per le app possono essere fornite esclusivamente dall'utente.
# Referenze
