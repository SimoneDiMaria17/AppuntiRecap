## Teoria
### Tabella
Una tabella è una struttura di un database che organizza i dati in righe e colonne.
Ogni colonna rappresenta un attributo (con un tipo di dato), mentre ogni riga rappresenta un record, cioè un’istanza dei dati memorizzati.


```sql
Create Table nome_Tabella (
	 nome_campo attributi
)
```

### Tipologia di dato
Ogni campo della tabella è tipizzato, i principali di tipi sono:
#### Numeri
- Tinyint -> intero molto piccolo equivalente a 8 bit, valore fino a 255
- Smallint -> intero equivalente a 16 bit, valore fino a 
- Int -> intero standard equivalente a 32 bit
- Bigint
- decimal(p,s)->numero decimale, la 'p' equivale al numero cifre totali e la 's' al numero di cifre decimali  
- float -> simile al decimal ma più approssimato
#### Testo
- Char(n) -> stringa a lunghezza fissa
- Varchar(n) -> stringa a lunghezza variabile 
- Nvarchar(n) -> come il varchar ma supporta tutti i caratteri unicode
#### Altre tipologie
- Boolean -> non esiste un vero e proprio tipo bolleano, infatti di deve usare il tipo bit
- Data -> per inserire un data si usa il tipo DATETIME
-

###  Vincoli
I vincoli sono delle regole che vengono applicate ai campi della tabella, i principali sono:
- Primary Key: Vincolo di chiave primaria 
	```sql
		nome tipo primary key
	```
- Foreign Key : Vincolo di chiave esterna
	```sql
		nome tipo FOREIGN KEY REFERENCES tabella(id_Tabella)
	```
- Unique: impedisce valori duplicati e può essere null
	```sql
		nome tipo Unique
	```
- Not Null: impedisce che un valore sia null
	```sql
		nome tipo not null
	```
- Check: impone una condizione
```sql
	nome tipo check(condizione)
```
- Default: imposta un valore di default
```sql
	nome tipo DEFAULT valore_di_default
```

## Operazioni con Tabelle
### Select
La Select permette di selezionare un determinato set di dati tramite delle condizioni
```sql
Select colonne
From Tabella
```
se si vogliono selezionare tutte le tabelle si può usare l'asterisco.
I dati si possono ordinare con una ``ORDER BY campo``, o raggruppare con una ``GROUP BY campi da raggruppare``
#### Funzioni nella Select
- Count(campo) -> Conta il numero di righe
- AVG(campo) -> restituisce il valore medio
- Max(campo) -> Restituisce il valore massimo
- Min(campo) ->  Restituisce il valore minimo
### Join
La funzionalità di Join Permette di unire due o più tabelle, ci sono 3 tipi principali di Join:
- Inner Join -> prende solo gli elementi in comune delle 2 tabelle
- Left Join -> prende tutti glie elementi della prima tabella più gli  elementi in comune delle 2 tabelle
- Right Join -> prende tutti glie elementi della seconda tabella più gli  elementi in comune delle 2 tabelle
- 
```sql
--Inner Join
	SELECT u.nome, o.importo
	FROM utenti u
	INNER JOIN ordini o ON u.id = o.id_utente;
--Left Join
	SELECT u.nome, o.importo
	FROM utenti u
	LEFT JOIN ordini o ON u.id = o.id_utente;
--Right Join
	SELECT u.nome, o.importo
	FROM utenti u
	RIGHT JOIN ordini o ON u.id = o.id_utente;
```
### Sub_Query
Una sub Query è una query dentro un'altra Query.
Di solito le sub-query possono essere usate generalmente nelle Where e nelle From
```sql
SELECT col1, col2
FROM tabella
WHERE col3 = (
    SELECT col3
    FROM altra_tabella
    WHERE condizione
);
```
#### Scalar Sub-query
in questo caso la sub-query restituisce un solo valore
``` sql
	SELECT nome
	FROM utenti
	WHERE eta = (
	    SELECT MAX(eta)
	    FROM utenti
	);
```
#### Sub-Query multi-valore
In questo caso restituiscono più valori
``` sql
	SELECT nome
FROM utenti
WHERE id IN (
    SELECT id_utente
    FROM ordini
    WHERE importo > 100
);

```
 