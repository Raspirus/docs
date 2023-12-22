# Guide

## Impostazione Della Documentazione Locale

Impostare facilmente la documentazione sulla vostra macchina con questi semplici passi:

1. Clone this repository by following the instructions on [GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository).

   ```bash
   git clone https://github.com/Raspirus/docs.git
   ```

2. Navigate to the cloned directory and install the required dependencies.

   ```bash
   You can install the dependencies by running the following command: `pip install -r requirements.txt`.
   ```

3. Avvia il progetto localmente:
   Inizia il tuo progetto locale eseguendo questo comando:

   ```bash
   servizio mkdocs
   ```

   Questo avvierà un server di sviluppo, che ti permetterà di accedere alla documentazione tramite [http://localhost:8000](http://localhost:8000) nel tuo browser web preferito.

## Export to PDF

If you would like to have an offline version of this documentation in PDF format, you can follow these step-by-step instructions:

1. Segui il processo di configurazione descritto sopra.

2. Install [mkdocs](https://www.mkdocs.org/user-guide/installation/) and execute the build command: `mkdocs build`.

3. If everything goes smoothly, the resulting PDF file should be located in the `site/pdf` directory with the name `document.pdf`.

Please be aware that the exported PDF may have some issues with images and iFrames, but the text should be readable and suitable for sharing offline. Tuttavia, il testo rimane leggibile e adatto per la condivisione offline.

## Traduzioni

Per le traduzioni di questa documentazione, visita [Crowdin](https://crowdin.com/project/raspirus), una piattaforma di collaborazione. Le traduzioni per le stringhe dell'interfaccia utente sono gestite attraverso i file JSON. Per contribuire, crea le tue traduzioni all'interno della [cartella locales](https://github.com/Raspirus/Raspirus/tree/main/public%2Flocales). Mantenere l'unicità delle chiavi quando si traduce dal file `en.json`.

## Scanner Insights

### Scansione Dei File Compressi

!!! nota

```
Questa opzione non è ancora disponibile per il Raspberry Pi. Scopri perché nella [sezione FAQ](https://raspirus.github.io/docs/faq)
```

Mentre Raspirus predefinito per la scansione delle cartelle, è possibile modificare questo comportamento tramite la pagina delle impostazioni. Attivando un interruttore, è possibile eseguire la scansione di singoli file, inclusi quelli compressi. È importante notare che un solo file può essere scansionato alla volta.

### Navigazione di registri e configurazioni

In caso di eventi inaspettati o di crash improvvisi delle app, l'esame di registri e configurazioni può fornire approfondimenti. Individuare questi file nelle seguenti cartelle, in base al sistema operativo. Il [ProjectDirs crate](https://docs.rs/directories-next/latest/directories_next/struct.ProjectDirs.html) li memorizza nella posizione seguente:

**File di configurazione**

| Piattaforma | Valore                                                                    | Esempio                                                       |
| ----------- | ------------------------------------------------------------------------- | ------------------------------------------------------------- |
| Linux       | `$XDG_DATA_HOME`/`_project_path_` o `$HOME`/.local/share/`_project_path_` | /home/alice/.local/share/barapp                               |
| macOS       | `$HOME`/Library/Application Support/`_project_path_`                      | /Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App |
| Finestre    | `{FOLDERID_RoamingAppData}`\\`_project_path_`\data                        | C:\Users\Alice\AppData\Roaming\Foo Corp\Bar App\data          |

**File di registro:**

| Piattaforma | Valore                                                                    | Esempio                                                       |
| ----------- | ------------------------------------------------------------------------- | ------------------------------------------------------------- |
| Linux       | `$XDG_DATA_HOME`/`_project_path_` o `$HOME`/.local/share/`_project_path_` | /home/alice/.local/share/barapp                               |
| macOS       | `$HOME`/Library/Application Support/`_project_path_`                      | /Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App |
| Finestre    | `{FOLDERID_LocalAppData}`\\`_project_path_`\data                          | C:\Users\Alice\AppData\Local\Foo Corp\Bar App\data            |

Assicurarsi di includere questi file durante la segnalazione di bug, in quanto aiutano notevolmente nella risoluzione dei problemi.

## GitHub Integration

### Arricchire il database delle firme

COMANDO SUONO

## Distribuzione Raspberry Pi

Originariamente su misura per distribuzione Raspberry Pi standalone con funzionalità touchscreen (simile alla modalità chiosco), lo scopo primario di questo progetto era la scansione delle unità USB collegate. Mentre il campo di applicazione del progetto si è ampliato, questa caratteristica rimane intatta. Segui la [guida su Tauri](https://tauri.app/v1/guides/building/linux#manual-compilation) e, se riscontri qualche problema, assicurati di farci sapere.

Grazie per aver scelto Raspirus come soluzione di protezione da malware. Queste guide complete garantiranno la vostra esperienza senza soluzione di continuità ed efficiente.
