15-07-2026 09:35
Tags:[[Sistemi Operativi]]

# ROS (Robot Operating System)
E' un framework software open-source per lo sviluppo di software per dispositivi robotici.
E' un *meta-sistema operativo* perchè offre alcuni dei servizi e delle funzionalità offerti da un sistema operativo in senso stretto
- Astrazione hardware
	ROS offre un'interfaccia per accedere ai driver di basso livello per l'hardware del robot. Questo rende il codice notevolmente riusabile nonostante l'eterogeneità dei sistemi robotici
- Comunicazione tra processi
	Tra cui un meccanismo di comunicazione asincrono (*Topic*) secondo il paradigma publish/subscribe e uno sincrono (*services*)
- Gestore dei pacchetti (*rosrun*)
- Semplificare il lavoro del ricercatore
	ROS scompone i diversi processi del sistema robotico in nodi.
### ROS core
E' una collezione dei nodi essenziali per il funzionamento di ROS. Comprende:
- ROS master
	Nodo che permette la comunicazione P2P tra nodi fornendo un algoritmo di lookup per questi.
- ROS Parameter Server
	Permette di conservare e recuperare dati in coppie chiave valore.
- ROS logging node
	Offre funzioni di logging ridirezionate sullo stdout e stderr in formato human readable
Il comando `roscore` è un'estensione del comando `roslaunch` che permette di avviare contemporaneamente i nodi e le librerie essenziali.
### Nodi
Ogni eseguibiile in ROS è un nodo.
I nodi possono comunicare tra loro 
- "Partecipando" ad un Topic 
- Offrendo o richiedendo un servizio
### Topic 
Uno o più nodi possono partecipare ad un topic. La comunicazione inizia quando un topic ha almeno un publisher ed un subscriber.
- I nodi non hanno conoscenza dei nodi con cui stanno comunicando
	Slega la produzione dell'informazione dal consumatore.
- Ogni topic è fortemente tipizzato.
	Il messaggio è una struttura dati costituita da campi tipizzati.
### Servizi
Offrono un modo ai nodi per mandare richieste e ricevere risposte da altri nodi, in maniera sincrona (protocollo RPC).
- Un'interazione richiesta/risposta è scarsamente praticabile nella comunicazione unidirezionale tra topic. I servizi sono definiti da una coppia di messaggi (request; reply)
- Un nodo offre un servizio sotto uno *String Name* (turtlesim/Spawn)
### Parameters
I dati sono conservati nel ROS Parameter Server. Solitamente sono utilizzati per la configurazione dei nodi a runtime e accettano diversi tipi di dati.
I parametri sono organizzati gerarchicamente secondo la naming convention di ROS.
- Evita che parametri diversi collidano tra loro 
- Organizza i parametri in una struttura ad albero

### ROS Launch Files (`roslaunch`)
File XML .launch dichiarati gerarchicamente sotto un package che permettono di lanciare diversi nodi, anche in maniera remota, contemporaneamente. 
Offre la possibilità di specificare parametri di configurazione di avvio per i nodi in questione.


# Referenze