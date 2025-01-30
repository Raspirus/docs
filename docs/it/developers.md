# Sviluppatori

Benvenuto nella guida dello sviluppatore Raspirus! Questa pagina delinea tutto ciò di cui hai bisogno per contribuire in modo efficace, dalla creazione del tuo ambiente alla comprensione dell'architettura e all'aggiornamento delle regole YARA.

---

## Configurazione

Per iniziare lo sviluppo, seguire queste fasi:

1. Clona il repository:
   ```sh
   git clone https://github.com/Raspirus/raspirus.git
   cd raspirus
   ```
2. Installa [Rust](https://www.rust-lang.org/tools/install).
3. Installare il pacchetto Raspirus:
   ```sh
   cargo install .
   ```
4. Avvia lo sviluppo:
   ```sh
   corsa di carico
   ```
5. O costruire Raspirus:
   ```sh
   costruzione del carico
   ```

### Problemi Di Impostazione Risoluzione Problemi

Se si incontrano problemi durante la costruzione o l'esecuzione di Raspirus:

- Assicurati che Rust sia installato correttamente.
- Verificare che i log e i file di configurazione siano creati correttamente.
- Controlla i conflitti di dipendenza e i pacchetti mancanti.

---

## Documentazione

Dal momento che Raspirus è scritto in Rust, è possibile generare la documentazione dello sviluppatore con:

```sh
cargo doc --no-deps --open
```

Questo aprirà la documentazione generata nel tuo browser.

---

## Architettura

Raspirus segue un'architettura **frontend-backend** con entrambi i componenti scritti a Rust.

### Frontend

- Usa **iced-rs** per il rendering GUI.
- Prioritizza l'esperienza dell'utente, idealmente, gli utenti non dovrebbero mai avere bisogno di aprire la pagina delle impostazioni.
- Progettato per **supporto touch**, minimizzando l'input della tastiera.
- Plug-and-play: Può essere sostituito con un altro frontend se necessario.
- Struttura semplice, simile a un sito web con poche pagine.

### Backend

- **Multi-filettato** per una scansione efficiente.
- Gestisce la scansione, l'elaborazione delle regole e la gestione delle impostazioni.
- Implementa **regole YARA** per il rilevamento di malware.
- Funzioni ben documentate – in caso di dubbio controllare direttamente il codice.
- Nonostante la sua complessità, diventa più facile navigare una volta che si inizia a lavorare con esso.

---

## Configurazione

Il file di configurazione è memorizzato nella cartella di configurazione di sistema predefinita:

```json
{
  "config_version": "6",
  "rules_version": "v1.1. ",
  "min_matches": 0,
  "max_matches": 20,
  "max_threads": 12,
  "logging_is_active": true,
  "mirror": "https://api. ithub.com/repos/Raspirus/yara-rules/releases/latest",
  "language": "en",
  "dark_mode": true
}
```

### Campi Chiave

- `config_version`: Determina se una configurazione più vecchia deve essere sovrascritta.
- `rules_version`: Traccia l'ultima versione scaricata delle regole YARA.
- `min_matches`: Numero minimo di regole necessarie per contrassegnare un file.
- `max_matches`: Massima corrispondenza delle regole prima di interrompere ulteriori controlli.
- `max_threads`: Numero di thread della CPU utilizzati per la scansione.
- `logging_is_active`: Abilita/disabilita la registrazione (utile quando la memoria è limitata).
- `mirror`: endpoint API per recuperare gli aggiornamenti delle regole.
- `language`: Lingua corrente (supporta `fr`, `en`, `it`, `de`).
- `dark_mode`: Commuta la modalità scura dell'applicazione.

---

## Specchi

L'impostazione `mirror` nel file di configurazione dovrebbe puntare a una API Git. Gli specchi personalizzati devono fornire a JSON la seguente struttura:

```json
{
  "tag_name": "v1.1",
  "zipball_url": "http://example.com/download.zip"
}
```

- `tag_name`: Specifica la versione per i controlli di aggiornamento.
- `zipball_url`: Link diretto all'archivio `.zip` contenente le regole YARA.

---

## Aggiornatore

Raspirus ha un **built-from-scratch updater** che:

1. Controlla l'ultima versione disponibile utilizzando lo specchio configurato.
2. Scarica l'archivio `.zip` nella cache.
3. Compila tutti i file `.yar` in un `.yarac` (regole YARA compilate).
4. Salva le regole compilate in:
   - **Linux/macOS**: `~/.local/share/raspirus`
   - **Windows**: `%appdata%\Roaming\Raspirus\Data`
   - **macOS (App Bundle)**: `/Applications/Raspirus/data`

### Rilascia Struttura Archivio

L'aggiornamento `.zip` dovrebbe contenere **file YARA `.yar` non compilati**. La struttura delle cartelle all'interno dell'archivio non importa, poiché i file vengono aggiunti ricorsivamente.

📌 \*\*Utenti Windows: \*\* Se Windows Defender interferisce con le regole YARA compilate, uno script opzionale può disabilitare la scansione Defender. Vedi [questo script](https://github.com/Raspirus/yara-rules/blob/main/scripts/windows.ps1).
