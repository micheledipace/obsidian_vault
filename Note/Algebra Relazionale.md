24-05-2026 11:25
Tags: [[Basi di Dati]] [[Modello Relazionale]]

# Algebra Relazionale
E' un'algebra chiusa: è definita su relazioni che producono altre relazioni

### Operatori unari
- Operatore di selezione $\sigma$
	Seleziona le tuple che rispettano una serie di condizioni legate mediante gli operatori logici.
	Il grado della relazione prodotta è **minore o uguale** a quello della relazione di partenza.
    Il grado **rimane invariato**
	L'operazione di selezione è commutativa
- Operatore di proiezione $\pi$ 
	Seleziona una lista di attributi da una relazione
	**Modifica** il grado
	**Può modificare** la cardinalità perchè un attributo può avere lo stesso valore per più tuple.
- Operatore di ridenominazione $\rho$
	Cambia il **nome** di uno o più attributi$$\rho_{<lista\_attributi\_rinominati> \leftarrow <lista\_attributi>} (<relazione>)$$
### Operatori binari
- Operatori insiemistici (unione, intersezione, differenza e prodotto cartesiano)
	Deve esistere una corrispondenza 1:1 fra gli attributi delle due relazioni.
- Operatore join
	Unisce due tuple di relazioni diverse che soddisfano una proposizione logica in una singola tupla. Solitamente i valori null **NON** contribuiscono al risultato della join.
	- Equi join
		E' un'operazione join che ha una condizione di uguaglianza su due attributi. I due attributi compariranno due volte nella relazione prodotto.
	- Natural join
		E' una equi join applicata su due relazioni che hanno lo stesso attributo (**STESSO NOME**)
	- Outer join
		Viene effettuata quando una delle due relazioni ha valori nulli per l'attributo su cui viene verificata la condizione del join.



# Referenze