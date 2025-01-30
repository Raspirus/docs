# FAQ

Qui di seguito sono alcune domande frequenti su Raspirus. Fare clic su qualsiasi domanda per espandere la risposta.

## Generale

??? question "Da dove viene il logo Raspirus?"\
Il logo Raspirus presenta un mostro rosso chiamato **Stuart**, progettato per rappresentare una creatura che mangia virus. Il logo è stato generato usando [DALL-E](https://openai.com/product/dall-e-2), con l'editing e la fusione di immagini aggiuntive.

```
Stuart è un mostro amichevole, tranne quando ha fame di virus. Puoi trovare altri supporti e risorse nel [repository dedicato](https://github.com/Raspirus/media). Sentiti libero di usare queste immagini per la tua grafica e condividerle nelle [schede di discussione](https://github.com/orgs/Raspirus/discussions).  
```

??? question "Posso usare Raspirus offline?"\
Sì! Raspirus funziona offline ad eccezione degli aggiornamenti. Il database delle regole YARA è costruito localmente, e una connessione internet è necessaria solo quando si recuperano le ultime regole dal nostro repository GitHub.

## Installazione & Compatibilità

??? question "Quali sono i requisiti minimi di sistema?"\
Raspirus è leggero e funziona sulla maggior parte dei sistemi, tra cui dispositivi a bassa potenza come il Raspberry Pi 3B+. Tuttavia, per la migliore esperienza, raccomandiamo:

```
- **RAM:** ~1 GB  
- **Storage:** ~200 MB  
- **CPU:** Processore Dual-core (prestazioni superiori si traduce in scansioni più veloci)  
- **Display:** Richiesto per la GUI (nessuna dimensione minima rigorosa, ma schermi più piccoli possono avere un impatto sull'usabilità)  
```

??? question "Problema durante l'installazione di Raspirus su Linux"\
\*\*Non installare o eseguire azioni come utente `sudo`. \* Esegui sempre i comandi come utente principale e usa `sudo` solo quando necessario.

```
Passando all'utente `sudo` e eseguendo l'installazione si **romperà** la configurazione.  
```

??? question "Perché non posso selezionare directory o file?"\
Per modificare il tipo di asset che vuoi scansionare, fai clic sulla **icona arancione** vicino al menu a discesa della selezione. Puoi scegliere tra:

```
- **Unità USB**  
- **Cartelle**  
- **File individuali**  
```

??? question "Quali sistemi operativi e architetture sono supportati?"\
Raspirus supporta più sistemi operativi e architetture della CPU:

```
- **Windows:** Windows 10 & 11 (x86_64)  
- **Linux:** Distribuzioni basate su Debian (Debian, Ubuntu, PopOS, Mint, etc. (x86_64, ARM64)  
- **macOS:** Silicio Intel & Apple (x86_64, aarch64)  

Inoltre, Raspirus è **ufficialmente supportato** su:  

- OpenSUSE (x86_64, ARM64)  
- Distribuzioni Linux basate su Arch(x86_64, ARM64)  

**Supporto sperimentale:** RISC-V 64 su Linux.  
```

## Personalizzazione

??? question "Come aggiungo le mie regole YARA?"\
Raspirus recupera le regole dal [yara-rules repository](https://github.com/Raspirus/yara-rules) e costruisce il database localmente.

```
Se vuoi contribuire con nuove regole:  
- Apri un **problema** o invia una **pull request (PR)** sul [yara-rules repository](https://github.com/Raspirus/yara-rules).  

Se preferisci usare le tue regole:  
- Modifica il file di configurazione per recuperare le regole dal tuo repository invece.  
```

---

## Problemi Conosciuti

??? warning "Errore di installazione remota: App non rilevamento schermo"\
Se si installa Raspirus tramite accesso remoto, potresti vedere un errore che indica che l'app **non sta rilevando uno schermo**.

```
Questo accade perché il sistema non registra uno schermo quando si esegue l'app dalla CLI, anche se si è fisicamente connessi.  
```

??? warning "Problemi di dipendenza durante l'installazione di Raspirus"\
Se riscontri problemi di dipendenza:* Prova a usare la versione **AppImage**.
* Se i problemi persistono, considera **il downgrading o l'aggiornamento del tuo sistema operativo**.

```
Segnala sempre questi problemi su [Discord](https://discord.gg/raspirus) o [GitHub](https://github.com/Raspirus/raspirus/issues) in modo da poter indagare ulteriormente.  
```

---

## Problemi importanti di GitHub da controllare

Prima di segnalare un problema, si prega di controllare i seguenti problemi comunemente riferiti:

??? note "Problemi segnalati comunemente"* **[#852 - Nessun supporto armv7 (32-bit)](https://github.com/Raspirus/raspirus/issues/852)**
* **[#891 - Caratteri mancanti](https://github.com/Raspirus/raspirus/issues/891)**
* **[#902 - Errore "Impossibile aprire il file yar"](https://github.com/Raspirus/raspirus/issues/902)**
* **[#937 - ARM64 deb non installa su RaspiOS (Debian 12 Bookworm)](https://github.com/Raspirus/raspirus/issues/937)**

Questo non è un elenco completo, ma solo una selezione di problemi segnalati di frequente. Se riscontri un errore, controlla prima di tutto [GitHub issues](https://github.com/Raspirus/raspirus/issues) per vedere se esiste già una soluzione prima di richiedere supporto.

## Contribuire A Correzioni

Siamo lieti di assistere, quando possibile, ma il nostro tempo è limitato. Se trovi una soluzione a un problema, considera di condividerlo:

- Se un **problema esistente** copre il tuo problema, aggiungi un commento con la tua correzione.
- Se si scopre un **nuovo problema** e un workaround, aprire un problema e documentare la soluzione per gli altri.

I tuoi contributi aiutano a migliorare Raspirus per tutti! 🚀
