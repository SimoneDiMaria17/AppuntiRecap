## Teoria
### Tabella
Una tabella è una struttura di un database che organizza i dati in righe e colonne.
Ogni colonna rappresenta un attributo (con un tipo di dato), mentre ogni riga rappresenta un record, cioè un’istanza dei dati memorizzati.

```sql
Create Table nome_Tabella (
	 nome_campo attributi
)
```
###  Vincoli
I vincoli sono delle regole che vengono applicate ai campi della tabella, i principali sono:
- Primary Key: Vincolo di chiave primaria 
- Foreign Key : Vincolo di chiave esterna
- Unique: impedisce valori duplicati e può essere null
- Not null: impedisce che un valore sia null
- Check: impone una condizione
- Default