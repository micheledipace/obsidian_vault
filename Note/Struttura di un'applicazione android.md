14-07-2026 16:43
Tags:[[Sistemi Operativi]]

# Struttura di un'applicazione android
Ogni applicazione android ha 6 componenti. Ciascuno di questi rappesenta un **entry point** per il sistema
- Activity 
- Fragments
- Services
- Broadcast Receiver
- Content Provider
- Intent
### Activity 
Rappresenta una singola schermata di un'applicazione con cui l'utente può interagire.
- Un'applicazione può avere diverse activity. 
	Android gestisce l'ordine di activity di una stessa app in uno stack.
- Ogni activity è indipendente dalle altre
- L'applicazione viene avviata da un'activity principale
#### Stato di un'Activity
- Attiva o in esecuzione
	L'activity è in primo piano
- In pausa
	L'activity è oscurata parzialmente e non si può interagire con questa
- Terminata
	L'activity viene chiusa e un'altra passa in primo piano
#### Activity Lifecycle
Metodi di callback 
- onCreate()
	invocato quando	l'activity è creata per la prima volta
- onDestroy()
	invocato quando viene effettuata la deallocazione dell'activity dalla memoria. Stato in cui l'applicazione è killabile per mancanza di memoria
- onStart() (visibile lifetime)
	invocato prima che l'activity è visibile all'utente
- onResume() (foreground lifetime)
	invocato poco prima che l'utente possa interagire con l'activity (ma è gia visibile)
- onPause() (foreground lifetime)
	invocato quando un'altra activity passa in primo piano. Stato in cui l'applicazione è killabile per mancanza di memoria
- onStop() (visible lifetime)
	invocato quando l'activity non è più visibile all'utente. Stato in cui l'applicazione è killabile per mancanza di memoria
- onRestart()
	invocato quando l'utente torna all'activity
### Fragments
Componente che rende **modulare** l'interfaccia Android. Favorisce la riutilizzabilità dell'interfaccia utente anche su dispositivi di dimensione differente.
#### Fragment Lifecycle
- Ereditati da activity
- onAttach()
	Fragment associato ad un'activity
- onCreateView()
	chiamato tra onCreate() e onActivityCreated()
- onActivityCreated()
	chiamato dopo la creazione di una [[iOS#Componenti (Model-View-Controller design pattern)|view]] dell'Activity

### Services
Un service è una componente senza interfaccia utente che esegue operazioni in background.
- Un service può essere rappresentato dalla riproduzione della musica mentre un'altra Activity è in primo piano
#### Service Lifecycle
- onCreate()
- onDestroy()
- onStartCommand()
	callback chiamato quando una data operazione deve essere eseguita in background
- onBind()
	callback chiamato quando si verifica una connessione tra un'applicazione che richiede un *Service*
### Broadcast Receiver
Componente passivo di un'app attivo anche se l'app non è in esecuzione.
- Resta in ascolto di eventi segnalati dal sistema o da altre applicazioni.
- Ha solo il metodo di callback onReceive()
### Content Provider
Si occupa di gestire l'accesso ai dati di altre applicazioni. 
- Restituisce i dati come tabelle di un database relazionale (SQLite nelle [[Android#Librerie native|native libraries]]).
	interrogazioni, aggiornamenti, inserimenti e cancellazioni per agire sui dati
- Ogni dato è identificato da un *URI*, gestito dal *Content Resolver*
	`content(protocollo)://package/tabella/istanza`
#### Metodi di callback
- onCreate()
- update()
- remove()
- insert()
- query()
	restituisce un *cursore* che permette di scorrere righe e colonne
### Intent
Oggetto che rappresenta un'operazioni tra più componenti.
- Contiene il riferimento all'azione e ai dati da elaborare
Può essere
- Esplicito
	Individua univocamente il destinatario
- Implicito
	Dichiara un compito generico da eseguire. Le applicazioni dichiarano un *Intent Filter* nel loro manifest per filtrare gli intent impliciti
### Bundle
Contenitore per passare dati tra activity. Un Bundle è allegabile ad un Intent.
### Android Manifest
Documento in formato XML essenziale per ogni applicazione android. Descrivi informazioni necessarie:
- Intent Filter
- Permessi
- Package e ID dell'applicazione
- Icone e label
- Versione minima di Android richiesta
- Componenti dell'app

### Sicurezza 
- Ogni applicazione è confinata in una sandbox.
	Lo sviluppatore deve **richiedere esplicitamente** i permessi all'utente per accedere alla messaggistica, fotocamera, dati di altre app...
#### Permessi
Nell'AndroidManifest.xml lo sviluppatore può dichiarare i permessi (o un gruppo di questi) necessari per il funzionamento dell'app oppure crearne di custom per poter accedere ai propri dati riservati.
### Scrittura dei dati 
#### Preferenze di un app
Android salva le preferenza in una mappa (*array associativo*)
#### Storage Interno
Un app deve ricevere da parte dell'utente il permesso di poter leggere e scrivere in memoria
#### Scoped Internal Storage
Cartella visibile solo all'applicazione
#### Network Connection
API java.net e android.net forniscono i metodi di salvataggio dei dati in rete
### Risorse
Dati utili all'applicazione memorizzanti all'interno del pacchetto .apk
# Referenze