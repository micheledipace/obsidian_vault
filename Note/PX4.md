13-07-2026 11:47
Tags:[[Sistemi Operativi]]

# PX4
Software di controllo *open-source* per sistemi UAV (*Unmanned Aerial Veichle*) (droni).
Per poter funzionare un UAV ha bisogno di:
- Autopilota
	Dispositivo che regola attuatori e motori ricevendo direttive dalla Ground Control Station o da una traiettoria di volo preimpostata.
- Ground Control Station
	Sistema di terra che ha controllo dei parametri di volo forniti dai sensori del mezzo e invia segnali all'autopilota.
### Architettura di PX4
E' composta da due layer principali
- flight stack
- middleware
#### Flight Stack
- Estimator
	riceve dati dai sensori e fissa un setpoint.
- Controller
	Prende in ingresso il setpoint per modificare assetto e controllare la spinta sugli attuatori (movimento verso la posizione desiderata).
- Mixer
	Traduce i dati dei controllori in comandi a basso livello per i motori, garantendo l'integrità strutturale del veivolo.
#### Middleware
- driver per i sensori
- uORB
	API per lo scambio di messaggi tra processi secondo il paradigma *publish/subscribe* **asincrono**
- MAVLink
	protocollo per la comunicazione tra veivolo e Ground Control Station (QGroundControl) e scambio di messaggi tra PX4 e componenti esterni.
- Layer di simulazione
	Gazebo e jMAVSim
### QGroundControl
Applicazione per configurare e guidare un veivolo con autopilota PX4
- mission planning
- supporto a Google Earth
- gestisce i dati ricevuti dai sensori
- supporto al controllo tramite joystick

### Caricamento del firmware
E' necessario scaricare il codice sorgente e utilizzare il tool di cross-compilazione `make`. 
Modificando il *makefile* è possibile definire moduli aggiuntivi da includere nella compilazione oltre che cambiare la configurazione del sistema.
### Software di Simulazione
- Gazebo
	Software di simulazione 3D per qualsiasi robot
- jMAVSim
	Software di simulazione 3D specifico per UAV. Supporta la comunicazione con QGroundControl mediante protocollo MAVLink.
	

# Referenze