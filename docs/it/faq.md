---
comments: true
---

# FAQ

??? question "App crashes when updating"
On Windows, it has been observed that the app crashes when attempting to update the database. Siamo consapevoli di questo problema e ci stiamo adoperando attivamente per risolverlo. Il problema sorge perché la funzione di aggiornamento richiede privilegi amministrativi, che Windows non fornisce automaticamente. Per risolvere temporaneamente questo problema, è possibile eseguire l'applicazione con privilegi amministrativi. Fare clic con il tasto destro sull'app e selezionare "Esegui come amministratore" per avviarla con i privilegi necessari.

??? question "Where does the Raspirus logo come from?"
Il logo dell'app Raspirus presenta un mostro rosso di nome Stuart, che è progettato per rappresentare una creatura che mangia virus. Il logo è stato generato utilizzando [DALL-E](https://openai.com/product/dall-e-2), insieme all'editing e alla fusione di immagini creative. Stuart è un mostro amichevole, tranne quando ha fame di virus. Puoi trovare ulteriori supporti e documenti nel [repository dedicato](https://github.com/Raspirus/media). Sentitevi liberi di utilizzare queste immagini per creare la vostra grafica e condividerle nelle [schede di discussione](https://github.com/orgs/Raspirus/discussioni).

??? question "Can I use Raspirus offline?"
Yes, except for the update, everything on Raspirus works offline. The database is built locally, you only need to be connected to the internet during the database update, as we fetch the signatures from our GitHub repository.

??? question "What are the minimum requirements for the app to work?"
Raspirus is built to work and almost any system. It even works well on a RPi 3B+. Nonetheless, we recommend having:

```
- 1 GB of RAM
- minimum of 10 GB of space (the database is sadly quite big)
- Dual core CPU (The better, the faster Raspirus will be)
- A display for the GUI, else you can only use it in CLI mode
- Any graphics card
```

??? question "My VScode setup is giving me issues"

````
Il plugin Rust Analyzer in Visual Studio Code cerca un file `Cargo.toml` nella directory corrente o nella directory principale. Per risolvere questo problema, puoi aggiungere un'opzione alle impostazioni del plugin e specificare la posizione del tuo `Cargo. oml` file.

Come menzionato nel [questo commento](https://github. om/rust-lang/rust-analyzer/issues/2649#issuecomment-691582605), è possibile aggiungere le seguenti righe alla fine delle impostazioni del plugin JSON. Successivamente, riavviare l'Analizzatore Rust affinché le modifiche abbiano effetto.

```json
{
    "rust-analyzer. inkedProjects": [
        "/home/stuart/raspirus/raspirus/Cargo.toml"
    ]
}
```
````

??? question "Can't select directories/files"
Unfortunately, as of [this issue](https://github.com/tauri-apps/tauri/issues/5405) with Tauri, we currently can't allow users to select both files and folders. Per passare dalla selezione di un singolo file o cartella, è necessario modificarlo nelle impostazioni di Raspirus. Qui troverete un interruttore per esso.

??? question "What is obfuscated mode?"
Raspirus era originariamente destinato all'uso aziendale e quindi doveva essere rispettoso della privacy. Per garantire che, ha aggiunto la "modalità obfuscation", che nasconderà tutto, rilevare il malware più velocemente e solo visualizzare: "Malware trovato" o "Nessun malware trovato". È attivata per impostazione predefinita, quindi se vuoi saperne di più sulla tua scansione, probabilmente dovresti disattivarla. Puoi farlo nelle impostazioni.

??? question "error: found a virtual manifest instead of a package manifest"
If you get this error when performing `cargo install` or using the Makefile, please note that it's a [know issue](https://github.com/rust-lang/cargo/issues/7599). The solution is simple, as explained on [this](https://stackoverflow.com/a/76271890) Stackoverflow answer, simply change the command to include the workspace, like this: `cargo install --path src-tauri/`

??? question "How do I add my own signatures to the main repository?"
Raspirus fetches signatures from the [signatures repository](https://github.com/Raspirus/signatures) and creates the database locally. You can add signatures to the repository by creating an issue or PR request on that repository. Or if you want to experiment with it locally, you can use the [signatures-builder](https://github.com/Raspirus/signature-builder) that we use to update the signatures in the signatures repository
