12-07-2026 11:46
Tags:[[Sistemi Operativi]]

# Struttura delle memoria di massa
Un disco è indirizzato come un array di blocchi logici.
Ogni blocco logico è traducibile con un indirizzo fisico del disco:
- Numero di cilindro.
- Numero di settore all'interno di quel cilindro.
- Numero di traccia all'interno della traccia.
traccia $\subset$ settore $\subset$ cilindro
### Algoritmi di schedulazione del disco
L'obiettivo del sistema operativo è utilizzare efficientemente la memoria secondaria, garantendo una larghezza di banda sufficiente e un tempo d'accesso ai dati ridotto.
In particolare nei dischi magnetici: 
- Seek time è il tempo che impiega la testina per spostarsi sulla traccia desiderata
- La latenza rotazionale è il delay aggiunto dalla rotazione del disco.
- La larghezza di banda è il flusso di dati trasmessi per unità di tempo
#### FCFS
Classico algortimo first come first served

#### SSTF
Algoritmo shortest seek time first. Il seek time è appossimabile alla distanza fisica dei cilindri. Molto simile a SJF.

#### SCAN (Algoritmo dell'ascensore)
Il braccio si muove da un estremo all'altro del disco servendo le richieste di accesso man mano che si muove verso le estremità.

#### C-SCAN
Il braccio si muove verso l'estremità finale del disco servendo le richieste. Una volta toccato il cilindro finale si sposta al cilindro iniziale per servire le richieste rimanenti.

#### C-LOOK
Variante dell'algoritmo C-SCAN per cui la testina non tocca le estremità del disco.

### Formattazione del disco
Il sistema operativo suddivide il disco in due o più partizioni del disco.
- Una partizione è formata da un gruppo di cilindri.
- Ogni partizione ha una formattazione logica che corrisponde al [[File System|file system]] da utilizzare in quella partizione
- La partizione di boot è una partizione speciale che comprende i file necessari all'avvio del sistema (escluso il BIOS).

# Referenze