23-05-2026 10:16
Tags: [[Basi di Dati]]

# Modello Entità Relazioni
Definisce lo **schema concettuale**, una rappresentazione ad alto livello dei dati e delle relazioni raccolte in analisi
### Costrutti del modello entità relazioni
- Entità
	Una classe di oggetti distinguibili da altri.
	Possono essere *deboli*
	- Gli attributi di un'entità debole non identificano univocamente una chiave per quella entità. L'insieme di attributi che rispetta il vincolo di chiave è identificato da un o più attributi dell'entità identificante che partecipa alla relazione che la lega con l'entità debole.
	Le **generalizzazioni** permettono di esprimere un rapporto genitore-figlio tra entità. Esistono strategie per rappresentare questo tipo di legame logico.
- Relazione
	Legame logico tra entità.
	Ogni relazione ha:
	- grado
		Numero di entità che partecipano alla relazione. E' preferibile avere relazioni il cui **grado massimo** è pari a 2.
	- cardinalità
		Numero di occorrenze coinvolte per ciascuna entità partecipante (1:1, 1:N, N:M)
	- partecipazione
		Numero minimo di occorrenze che *partecipano* alla relazione.
	Possono essere **ricorsive**
- Attributo
	Peculiarità e proprietà di una entità. Deve essere specificato il **dominio** di ogni attributo (può essere null).
	Può essere:
	- Atomico
	- Composto
	- Multivalore (aumenta la complessità della query)
	- Derivato
	Se una combinazione di valori di uno o più attributi è **distinta** per ogni occorrenza, l'insieme di attributi è chiamata **chiave**. Più di un insieme di attributi può soddisfare il *vincolo di chiave*.
	Il vincolo di chiave deve avere carattere generale: non dipende dalle singole occorrenze che sono presenti in un determinato momento.
- Occorrenza
	Singolo esemplare di un'entità, caratterizzata da singoli valori dei propri attributi. E' identificata univocamente dalla chiave.



# Referenze