09-07-2026 19:09
Tags: [[Sistemi Operativi]]

# Thread
![[Concepts-_Program_vs._Process_vs._Thread.jpg|697]]

![[Multithreaded_process.svg.webp|365]]
Un **thread** è l’unità più piccola di elaborazione che può essere gestita in modo indipendente da un sistema operativo. Rappresenta il flusso di controllo dentro quel processo.
Creare nuovi thread è **meno costoso** rispetto a creare un nuovo processo.
### Vantaggi 
- Condividono risorse perchè appartengono allo stesso processo 
- E' più veloce creare nuovi thread 
- Utilizzano le capacità multithread delle moderne CPU (esecuzione parallela).
- Il context-swtiching può applicare strategie aggressive di caching
### Modello di programmazione dei thread livello kernel e utente
Alcuni thread possono essere gestiti esclusivamente nello userspace. Questi devono essere collegati ad almeno un thread kernel
- Modello uno ad uno
	Livello di multithreading elevato ma può generare overhead dovuto alla continua creazione di thread kernel.
- Modello molti ad uno
	Solo un thread utente per volta può effettuare una syscall ad un thread kernel. Semplice da implementare.
- Modello molti a molti 
	Aggrega più thread utente ad un numero minore o uguale di thread kernel 
- Modello a due livelli 
	Variante ibrida che permette anche la mappatura uno ad uno oltre che molti a molti
### System call `fork()` a livello thread
Si può decidere di:
- Duplicare tutti i thread se non vi è nessuna `exec()` successiva
- Copiare solo il thread che invoca la `fork()` se una chiamata `exec()` rimpiazza il programma nello spazio di memoria del processo. 
### Terminazione di un thread
Avviene in 
- Modalità asincrona
	Il thread termina immediatamente. Causa problemi se il thread sta modificando dati condivisi con altri thread.
- Modalità differita
	Il thread target controlla periodicamente se può terminare in modo ordinato.
### Segnali (sistemi UNIX)
Nei sistemi UNIX i segnali **notificano un evento** ad un processo. 
Possono essere:
- Sincroni 
	Nascono a causa del thread che lo riceve (seg fault)
- Asincroni 
	Inviati da un processo esterno 
Il gestore dei segnali si occupa di consegnare i messaggi secondo diverse modalità:
- Ad ogni processo
- Al singolo processo (segnali sincroni)
- Ad alcuni processi 
- Ad un thread che ha il compito di ricevere i segnali
### Pool di thread
La creazione di un gruppo di thread che rimangono inattivi fin quando non ce n'è bisogno
- Pongono un limite alla concorrenza tra thread
- Garantiscono un esecuzione più veloce piuttosto della creazione e terminazione di nuovi thread.
# Referenze