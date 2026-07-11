09-07-2026 10:28
Tags:[[Sistemi Operativi]]

# Architettura del calcolatore
![[Screenshot 2026-07-09 at 10.50.16.png]]

### Avvio 
Viene caricato un programma di bootstrap (BIOS) letto da una EEPROM. 
Inizializza i controller delle diverse perifiche e si occupa di **caricare il kernel**
### Gestione interrupt driven degli eventi
Il kernel è in ascolto di eventi segnalati da interrupt hardware. L'*interrupt handler* del kernel trasferisce il controllo della CPU alla routine di gestione interrupt caricata dal **vettore degli interrupt**. 
- Gli interrupt non causati da eccezioni possono essere mascherati.
- Il sistema operativo deve salvare l'indirizzo dell'istruzione interrotta e lo stato della CPU al momento dell'interruzione.
- Attraverso una **system call** un processo utente può richiedere al kernel l'accesso a periferiche di I/O
### Direct Memory Access (DMA)
E' una tecnica che permette l'accesso a dati della memoria secondaria attraverso *bus dati* non controllati dalla CPU, che non riuscirebbe a restare al passo della velocità di trasferimento di queste periferiche.
- La CPU si occupa solo di iniziare il trasferimento e di eseguite la routine per l'interrupt di completamento.
### Protezione hardware
La non corretta gestione della multiprogrammazione potrebbe portare un processo a interferire con il corretto funzionamento del kernel. 
Le risorse sono protette dal sistema operativo in questo modo.
#### Modalità differenziate
- User mode
- Kernel mode
	La CPU commuta in questa modalità al verificarsi di un interrupt.
	Un processo user può richiedere l'uso di servizi e periferiche effettuando una system call. 
#### Protezione dell'I/O
E' fondamentale che un processo utente non venga mai eseguito in kernel mode.
Un programma malevolo eseguito in kernel mode potrebbe alterare il vettore degli interrupt per ottenere il controllo del calcolatore.
#### Protezione della memoria
Un processo deve poter accedere esclusivamente alla porzione di memoria a sè riservata. 
Un registro base/limite modificabile solo dal SO confronta ogni indirizzo generato in modalità utente.
#### Protezione della CPU
Un temporizzatore evita che un processo blocchi la CPU in ciclo infinito. Alla fine del timer il sistema operativo riprende il controllo della CPU.
# Referenze