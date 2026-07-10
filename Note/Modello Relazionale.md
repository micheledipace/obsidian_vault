23-05-2026 11:21
Tags: [[Basi di Dati]]

# Modello Relazionale
Nel modello relazionale i dati sono organizzati in relazioni (diversa dalla definizione del modello E-R). 
In questo modello matematico una **relazione** è una collezione di tuple ordinate e distinte rappresentate in *forma tabellare*. 
Ogni **valore** di una tupla è collegato tra loro.
- Ogni tupla rappresenta una riga (occorrenza)
- Ogni colonna rappresenta un attributo. Tutti i valori di una colonna appartengono allo stesso dominio
- Il dominio di ciascun attributo deve consistere di valori atomici.
- Il valore di un attributo deve essere un singolo valore del proprio dominio
### Schema e istanza
- Lo schema di relazione è costituito da un nome e da un insieme di attributi. 
	Uno schema di basi di dati è un insieme di schemi di relazioni.
	Il **grado** di una relazione è il numero di attributi di uno schema
- Un'istanza di relazione è un insieme di tuple su un insieme di attributi individuato da uno schema di relazione. 
	Un'istanza di basi di dati è un insieme di relazioni.
	La **cardinalità** di una relazione è il numero di tuple presenti nell'istanza di relazione.
### Vincoli di integrità
Sono necessari per garantire la correttezza dei dati. Si distinguono in:
#### Intrarelazionali
 - Vincolo di chiave.
	 Per ogni relazione **deve** esistere un sottoinsieme di attributi **univoco**. Questo sottoinsieme è detto *superchiave*. Se la superchiave è l'insieme di cardinalità più piccolo che soddisfa il vincolo di chiave, il sottoinsieme è chiamato **chiave**.
	 La chiave *designata* è detta **primaria**
 - Vincolo di tupla
 - Vincolo di dominio
	 Restrizioni sui valori che un attributo può assumere.

#### Interrelazionali
- Vincolo di integrità referenziale: concetto di **chiave esterna**
	Se un sottoinsieme di attributi di una relazione è chiave primaria di un'altra relazione, le due relazioni devono rispettare il vincolo di **integrità referenziale**.
	Il vincolo è soddisfatto se i *tutti i valori referenziati* per **ciascuna** tupla della prima relazione sono presenti nella seconda relazione (sono istanze della seconda relazione).
	Il sottoinsieme di attributi è identificato come *chiave esterna*: assieme alla chiave parziale costituirà la chiave per entità deboli
	
### Dal modello E-R al modello relazionale
- Ogni entità è una nuova relazione costituita dai suoi *attributi atomici*
	Le entità deboli *devono* includere la chiave primaria dell'entità identificante
- Relazioni 1:1
	Includere in una delle due relazioni la chiave esterna
- Relazioni 1:N
	Includere nella relazione di cardinalità N la chiave esterna
- Relazioni N:M
	Creare una relazione aggiuntiva (*junction table*) che ha come chiavi esterne le chiavi primarie delle due relazioni con un legame N:M.
- Attributi multivalore
	Creare una nuova relazione relativa all'attributo. La chiave della nuova relazione è attributo + chiave primaria della relazione di cui l'attributo si riferisce
- Associazioni di grado > 2
	Creare una relazione *di associazione* che ha come chiave primaria tutte le chiavi esterne delle entità che partecipano alla relazione con gli eventuali attributi della nuova relazione.




# Referenze