1. Decidere se il Progetto è DbFirst o CodeFirst

## DbFirst
1. Creare il Database seguendo le regole di [[Sql]]
2. Crea il progetto su visual studio usando il template Applicazione Web Asp.net                    (.Net Framework)
3. Importare il db
	1. 
## Code First
Creo il Progetto seguendo questo modello **api web asp.net core**.
### Progetto Vs 
come prima cosa dopo aver Creato il progetto Abilito il CORS che permette l'accesso alle chiamate del nostro backend, nel Program cs Scriviamo 
```c#
builder.Services.AddCors(options => {
	options.AddPolicy("CorsPolicy", builder => { 
		builder.AllowAnyOrigin();  //abilito tutti ad accedere
		builder.AllowAnyMethod(); //abilito chi può usare i metodi
		builder.AllowAnyHeader(); //abilito chi può usare gli header
	}); 
} );
```
dopo aver creato con il builder le politiche di cors, bisogna applicarle:
```c#
//dopo lo Use.Authorization
Use.Cors()
```

Dopo aver applicato il cors posso iniziare a creare le prime tabelle instanziando una cartella models, nella quale verranno create le classi che sono le future tabelle del Database, oltre alle tabelle si posso inserire anche i DTO (data transfer object) che sono dei "cloni" delle classi principali utili per operazioni specifiche come per esempio le set.
```
//Codice
```

Dopo aver Creato il Model di una tabella Bisogna Creare il Controller che è dove verranno create le vere proprie Api che poi richiamerà il FrontEnd
```
//Codice
```
Il Controller dentro alle chiamate userà dei metodi del service nel quale ci sono le principali operazioni logiche 
#### DbContext
Dentro la Cartella Model creo il DBContext che è quello che consente di collegare il progetto al db
```c#
using CompanyEmployees.Models;
using Microsoft.EntityFrameworkCore;
namespace CompanyEmployees.Repository
{
    public class RepositoryContext : DbContext
    {
        public RepositoryContext(DbContextOptions options): base(options)
        {
        }
        //col db set dico quali classi corrispondono alle tabelle
        public DbSet<Company>? Companies { get; set; }

        public DbSet<Employee>? Employees { get; set; }
    }
}
```
ovviamente serve anche la stringa di connessione che va inserita nell'Appsetting.jSon
```c#
"ConnectionStrings": {
    "sqlConnection": "connessione"
  },
```

!implementazione dbContext!

### Migration e creazione Db
migration è il metodo con il quale nel CodeFirst le Classi c# diventano tabelle nel db
per la prima migration bisogna avere almeno una entity e il dbContext configurato.
Dopo Avere quello menzionato prima impostato correttamente, si usa il comando 
```c#
Add-Migration NomeMigration
```
dopo aver creato la migration bisogna applicarla con il comando:
```c#
Update-Database
```
(come funziona il tutto, con il primo comando crei nella cartella migration le modifiche da fare al db e con il secondo le applichi, non è mai consigliato cancellare una migration o modificare a mano il db, piuttosto si crea una nuova migration che modifica come vogliamo).

### Model
### Controller


## Front-end
