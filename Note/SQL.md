01-06-2026 10:17
Tags: [[Basi di Dati]]

# SQL (Structured Query Language)
E' un linguaggio di *definizione* (DDL) e *modellazione* (DML) dei dati.
## DDL
#### Domini elementari 
Le variabili si dichiarano con il prefisso *var*
- Carattere
```
character[varying][(num_char)][character set nome_set]
```
- Numeri interi o a virgola fissa 
	- scale indica il numero di cifre dopo la virgola
	- precision indica il numero di cifre significative 
```
integer
smallint \\numeri interi
decimal[(precision,scale)]
numeric[(precision,scale)]
```
- Numero a virgola mobile
	Per **float** la precision è il numero di cifre della mantissa
```
float[(precision)]
real
double float
```
- Date e timestamp
```
Time [(precision)] [time_zone] \\UTC/GMT default
Timestamp [(precision)] [time_zone] \\6µs default
```
- Time interval
```
Interval FirstTimeUnit[(precision)] [to LastTimeUnit][(precision)]
```
- Valori booleani
```
bit[varying][(num_bit)]
```

#### Definizione di nuovi domini
A partire dai domini elementari è possibile creare nuovi domini più stringenti.
```
CREATE DOMAIN DomainName AS DataType [DefaultValue][Constraint]
```

#### Definizione di uno schema di basi di dati
```
CREATE SCHEMA [SchemaName] [[authorization] AuthorizedName] {DefiningElements}
```

#### Definizione di una tabella
Specificare una collezione ordinata di attributi e specificare i vincoli intrarelazionali e interrelazionali
```
CREATE TABLE RelationName(
AttributeName Domain [DefaultValue][Constraints]
{, FutherAttributeName...,}
FurtherConstraints) \\vincoli intra e inter-relazionali
```
#### Definizione dei vincoli 
1. Primary Key
	```
	PRIMARY KEY(AttributeName1, AttributeName2,...) \\ da inserire nella riga 
	"FurtherCconstraints"
	```
2. Not null
	L'attributo non può essere nullo. Va inserito nelle *constraints* dell'attributo
3. Unique 
	L'attributo è una chiave candidata. Va inserito nelle *constraints* dell'attributo
4. Foreign Key
	Specifica il vincolo inter-relazionale tra due tabelle. Bisogna specificare la chiave primaria alla quale la chiave secondaria si riferisce
	```
	FOREIGN KEY(AttributeName {,AttributeName}) REFERENCES 
	TableName(AttributeName{,AttributeName})
	```
5. Vincoli sull'aggiornamento e sull'eliminazione 
	Specifica il comportamento della tabella a seguito dell'eliminazione o dell'aggiornamento delle chiavi primarie a cui si riferiscono le chiavi secondarie.
	Fa parte della categoria *Further Constraints*
	```
	ON DELETE 
	ON UPDATE
	```
	Le possibili opzioni sono
	- Cascade 
		Tutte le tuple a cui si riferiscono i valori aggiornati si aggiornano (o eliminano)
	- Set null
	- Set default
	- No action 
		La cancellazione o l'aggiornamento viene inibito
6. Check su condizioni del dominio
	Equivalente ad una constraint sul dominio (**Vincoli di tupla**)

#### Modifica di una tabella o dominio
```
ALTER TABLE TableName <comando di alterazione>
ALTER DOMAIN DomaniName <comando di alterazione>
```
I possibili comandi sono
- alter column
- set default
- drop default
- add constraint
- drop constraint
- add column
- drop column
#### Eliminazione di una struttura
- Restrict implica che l'oggetto sia vuoto
- Cascade vengono eliminate tutte le referenze dell'oggetto in questione
```
DROP <schema|table|domain|view|assertion> ItemName [restrict|cascade] 
```

## DML
### Interrogazione
#### Struttura fondamentale
```
Select AttrExpr [[as] Alias]{, AttrExpr [[as] Alias]} \\ Target List
From TableName [[as] Alias]{, AttrExpr [[as] Alias]} \\ From clause
[Where condition] \\ Where clause
```
#### Alias
Sono utili per riferirsi ad attributi che non sono presenti nella tabella specificata dalla from clause
#### Operazioni Aritmetiche
E' possibile operare su
- campi di una tabella
- valori numerici 
- **funzioni aggregate**
#### All/Distinct
distinct preposto al nome dell'attributo formatta l'output in modo che un qualsiasi valore di quell'attributo compaia al più una volta
#### Condizioni logiche (where clause)
- Operatori di confronto
	Utilizzare **LIKE** per i caratteri
- Operatori logici (AND, OR)
- Operatori a valori multipli 
	IN e BETWEEN
#### Subquery nella where clause 
E' possibile effetturare una sottointerrogazione nella where clause.
Se la subquery **restituisce un insieme di valori** è possibile utilizzare le keyword
- ANY
	Almeno un elemento della target list deve rispettare la condizione
- ALL
	Tutti gli elementi della target list edvono rispettare la condizione
#### Prodotto cartesiano
Per effettuare il prodotto cartesiano tra due tabelle, inserire entrambe nella from clause.
#### Join
L'operazione di join è effettuata nella **from clause** 
```
Select ...
From TableName <tipo di join> TableName on <LogicalExp>
```
Tipi di join:
- Inner (default)
- Natural
- Outer
- Full (left outer + right outer)
- Self join
	E' necessario l'utilizzo degli alias nella from clause e nella join
#### Operatori insiemistici
Applicabili in una query o in una subquery sono:
- Union
- Except (differenza)
- Intesect
Eliminano di default i duplicati e le due target list devono avere lo stesso numero di elementi e gli elementi corrispondenti devono essere dello stesso tipo
#### Predicato EXISTS
Si applica a subquery a valori multipli.
Restituisce un valore booleano
### Interrogazioni con raggruppamento
- Le righe vengono raggruppate secondo gli attributi definiti dal `GROUP BY`
	La target list deve essere un sottoinsieme del group by, ma la condizione **non vale** per le funzioni aggregate
- La *having clause* esprime condizioni sui raggruppamenti.
#### Funzioni aggregate
E' possibile utilizzarle nella target list e nella having clause
- count
	Conta il numero di righe restituite
	`count (< * | [all|distinct] AttributeName {,AttributeName}`
 - Funzioni aritmetiche
	 avg, sum, max, min
### Insert
### Update
### Delete

## Asserzioni
Rappresenta un vincolo applicato all'intero schema di base di dati.
Il vincolo esprime ogni vincolo d'integrità valido per le tabelle.
```
create assertion AssertionName check(condizione)
```
Possono essere:
- immediati
	In caso di mancata soddisfazione della condizione in assertion viene effettuato un rollback
- Differiti (*deferred*)
	Il vincolo viene verificato al termine di una **transazione** (unità di lavoro indivisibile)
## Viste
Tabella virtuale il cui contenuto è definito a partire da altre tabelle o viste. Questa non contiene dati fisicamente conservati sul disco. 
Il database *rieseguirà* la query select della vista ogni volta che viene aperta.
```
create VIEW ViewName [(AttributeList)] as 
selectSQL [with [cascaded|local] check option]
```
Le **modifiche effettuate** sulla vista si propagano alla tabella base.
	Il flag *check option* annulla modifiche sulla vista che farebbero sparire quel dato dalla vista.
# Referenze