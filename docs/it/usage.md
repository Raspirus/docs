# Guida All'Uso

Raspirus è progettato per offrire un'esperienza semplice e user-friendly. Elimina la necessità di una tastiera o del mouse fornendo un'interfaccia completamente touchscreen. L'applicazione è stata sviluppata con semplicità in mente, garantendo che la navigazione e l'utilizzo di Raspirus sia intuitiva. In questa sezione, spiegheremo le impostazioni disponibili e le funzionalità di scansione in modo più dettagliato.

## Navigazione di registri e configurazioni

In caso di errori inattesi o crash delle applicazioni, la revisione dei registri e dei file di configurazione può fornire preziose informazioni. Questi file sono memorizzati in directory specifiche per le piattaforme, gestite dal [ProjectDirs crate](https://docs.rs/directories-next/latest/directories_next/struct.ProjectDirs.html).

### Posizione File Di Log

I file di registro sono memorizzati in posizioni diverse a seconda del sistema operativo. Di seguito è riportata una tabella dei percorsi predefiniti:

| Piattaforma | Percorso                                                                                  | Esempio                                                         |
| ----------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Linux       | `$XDG_DATA_HOME`/`_project_path_` o `$HOME`/.local/share/`_project_path_` | `/home/alice/.local/share/barapp`                               |
| macOS       | `$HOME`/Library/Application Support/`_project_path_`                                      | `/Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App` |
| Finestre    | `{FOLDERID_LocalAppData}`\\`_project_path_`\data                                        | `C:\Users\Alice\AppData\Local\Foo Corp\Bar App\data`     |

Quando si segnalano bug o problemi, assicurarsi di includere questi file di registro, in quanto aiutano in modo significativo nella risoluzione dei problemi.

## File Di Configurazione

Il file di configurazione contiene impostazioni importanti che persistono anche dopo la chiusura dell'applicazione. È essenziale non modificare queste impostazioni a meno che non si ha familiarità con la loro funzione, in quanto modifiche improprie potrebbero impedire l'applicazione di lanciare.

### Posizione File Di Configurazione

Il file di configurazione si trova in directory specifiche per la piattaforma, come mostrato di seguito:

| Piattaforma | Percorso                                                                                  | Esempio                                                         |
| ----------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Linux       | `$XDG_DATA_HOME`/`_project_path_` o `$HOME`/.local/share/`_project_path_` | `/home/alice/.local/share/barapp`                               |
| macOS       | `$HOME`/Library/Application Support/`_project_path_`                                      | `/Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App` |
| Finestre    | `{FOLDERID_RoamingAppData}`\\`_project_path_`\data                                      | `C:\Users\Alice\AppData\Roaming\Foo Corp\Bar App\data`   |

### Configurazione

Se hai bisogno di personalizzare ulteriormente Raspirus, puoi modificare manualmente il file di configurazione. Per esempio:

- **Distribuzione di configurazione centralizzata**: Sostituire il file di configurazione sul sistema di ogni utente all'avvio per imporre una configurazione comune.
- **Impostazioni personalizzate**: Imposta valori specifici, come il percorso delle regole YARA personalizzate o le preferenze del comportamento di scansione.

Per maggiori dettagli su come utilizzare e modificare il file di configurazione, fare riferimento alla [pagina sviluppatori](developers.md#configuration).

## Scansione

Raspirus consente di eseguire la scansione di file, cartelle e unità esterne specifiche per potenziali minacce di malware. Il processo di scansione controlla i file contro un database di regole YARA progettato per rilevare modelli dannosi noti.

### Bersagli Di Scansione Supportati

Raspirus può scansionare:

- Una cartella e tutte le sue sottocartelle.
- Un singolo file, compresi i file compressi (ad esempio, ZIP, TAR).
- Un disco staccabile (ad es. chiavetta USB).

### Permessi e limitazioni

Per eseguire la scansione dei file, Raspirus richiede l'accesso in lettura ai file o alle directory in questione. Non può accedere a file o cartelle compressi protetti da password che sono limitati dal sistema operativo.

!!! warning "Importante!"
Non tentare di scansionare l'intero sistema operativo o computer. Per la scansione completa del sistema, si consiglia di utilizzare una soluzione antivirus dedicata.

### Processo Di Scansione

Il processo di scansione comporta l'analisi dei file e del loro contenuto per abbinare i modelli rispetto al database delle regole YARA. Per i file compressi, Raspirus estrarrà e scansionerà i contenuti. Se un file corrisponde a un modello noto di malware, verrà contrassegnato come potenzialmente dannoso.

### Azioni Post-Scansione

Dopo aver completato una scansione:

- Se non vengono rilevate minacce, è possibile continuare le attività senza preoccupazione.
- Se viene trovato un malware, Raspirus visualizzerà un elenco di file contrassegnati e le minacce rilevate.

!!! note "File saltati"
Se Raspirus non è in grado di scansionare un file, salterà per evitare di dover interrompere il processo di scansione.
I file saltati possono normalmente essere ignorati, come di solito solo un problema di autorizzazione.

Raspirus **non** offre opzioni di cancellazione di file o quarantena perché il database di rilevamento può occasionalmente generare falsi positivi. Raccomandiamo di rivedere attentamente i file contrassegnati e di prendere decisioni in base al tuo giudizio o di inviare file sospetti a servizi come [VirusTotal](https://www.virustotal.com) per ulteriori analisi.
