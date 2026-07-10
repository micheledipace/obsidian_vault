26-05-2026 10:45
Tags: [[Basi di Dati]] [[Modello Relazionale]]

# Normalizzazione
- Fornisce linee guida formali che garantiscono la realizzazione di buone basi di dati.
- Evita che un'unica relazione contenga **informazioni eterogenee** che producono **ridondanza** e **anomalie da aggiornamento**. 
### Linee guida informali
- Prestare attenzione alla semantica degli attributi
- Evitare i valori null
	Possono essere variamente interpretati.
- Ridurre la ridondanza
- Evitare le tuple con informazioni non corrette (*spurie*)
	Queste possono essere generate tramite natural join effettuato su attributi che *non sono* chiavi primarie o esterne
#### Anomalie da aggiornamento
![[Screenshot 2026-05-26 at 11.02.52.png]]
In questa relazione si elencano le possibili anomalie a cui si potrebbe andare incontro.
- Anomalie da inserimento
	1. Un nuovo dipendente richiede l'inserimento delle informazioni del dipartimento. Tuttavia il dipendente potrebbe non essere stato assegnato ad alcun dipartimento
	2. L'inserimento di un nuovo dipartimento deve avere per forza un impiegato
- Anomalie da cancellazione
	1. Eliminando l'ultimo dipendente di un dipartimento si perderebbero le informazioni su quest'ultimo
- Anomalie da modifica
	1. La nomina di un nuovo direttore del dipartimento comporta la modifica di tutte le tuple della relazione.

### Dipendenze funzionali
Sono un **vincolo** tra due insieme di attributi appartenenti alla stessa relazione.
Un insieme di dipendenze funzionali **minimo** genera relazioni prive di ridondanze.
#### Definizione
Siano $X$ e $Y$ due sottoinsieme di $R$ non vuoti, si dice che $R$ **soddisfa la dipendenza funzionale** $$X \rightarrow Y$$ se ogni valore del sottoinsieme $X$ è associato ad un **unico valore** del sottoinsieme $Y$ 
Se $X$ è chiave candidata di $R$ allora $X \rightarrow Y$ vale per ogni attributo $Y$ di $R$. 
#### Conservazione delle dipendenze
Se ciascuna delle dipendenze funzionali dello schema originario coinvolge attributi che compaiono tutti insieme in uno delle relazioni decomposte.
#### Assiomi di Armstrong
1. Riflessività: se $Y$ è un sottoinsieme di $X$ allora $X \rightarrow Y$
2. Incremento: se $X \rightarrow Y$ allora $XZ \rightarrow YZ$ 
3. Transitività: se $X \rightarrow Y$ e $Y \rightarrow Z$ allora $X \rightarrow Z$
4. Unione: se $X \rightarrow Y$ e $X \rightarrow Z$ allora $X \rightarrow YZ$
5. Decomposizione: $X \rightarrow YZ$ allora $X \rightarrow Y$ e $X \rightarrow Z$
### Forme Normali
Compongono un metodo formale per analizzare le relazioni
1. Prima forma normale
	Coincide con la definizione di relazione del [[Modello Relazionale]]
2. Seconda forma normale
	Ogni attributo non chiave della relazione ha una dipendenza funzionale con l'intera chiave della relazione. La relazione deve essere gia in 1FN
3. Terza forma normale
	La relazione deve essere già in 2FN. Inoltre per ogni dipendenza funzionale:
	- $X$ è **superchiave** di $R$
	oppure 
	- $Y$ fa parte di una **chiave** di $R$
	 Ossia nessun attributo non chiave dipende transitivamente da un'altra FD
4. Forma normale di Boyce-Codd
	Vale solo la prima condizione per la 3FN.
	Uno schema in questa FN **non ha ridondanze**.
### Decomposizione senza perdite (lossless join)
Data una relazione $R(X)$ con $X = X_1 U X_2$, la relazione $R$ si decompone senza perdite se il natural join delle proiezioni di R su x1 e x2 (*relazioni decomposte*) sono uguali ad R.
#### Condizione sufficiente
Affinchè una relazione si decomponga senza perdite gli attributi in comune di ($X_1$ e $X_2$)  devono essere chiave per una delle due relazioni (le proiezioni su $X_1$ e $X_2$).

# Referenze