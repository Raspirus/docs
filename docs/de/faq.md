---
comments: true
---

# FAQ

??? question "App crashes when updating"
On Windows, it has been observed that the app crashes when attempting to update the database. Wir sind uns dieser Frage bewusst und arbeiten aktiv daran, sie zu lösen. Das Problem tritt auf, weil die Update-Funktion Administratorrechte benötigt, die Windows nicht automatisch zur Verfügung stellt. Um dieses Problem vorübergehend zu beheben, können Sie die App mit Administratorrechten ausführen. Klicken Sie mit der rechten Maustaste auf die App und wählen Sie "Als Administrator ausführen", um sie mit den nötigen Rechten zu starten.

??? question "Where does the Raspirus logo come from?"
Das Logo der Raspirus App enthält ein rotes Monster namens Stuart, das eine virusfressende Kreatur darstellen soll. Das Logo wurde mit [DALL-E](https://openai.com/product/dall-e-2) zusammen mit kreativer Bildbearbeitung und Zusammenführung generiert. Stuart ist ein freundliches Monster, außer wenn er hungrig nach Viren ist. Du kannst zusätzliche Medien und Dokumente im [dedizierten Projektarchiv](https://github.com/Raspirus/media) finden. Du kannst diese Bilder verwenden, um dein eigenes Kunstwerk zu erstellen und sie in den [Diskussionsforen“ zu teilen](https://github.com/orgs/Raspirus/discussions).

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
Das Rust Analyzer Plugin in Visual Studio Code sucht nach einer `Cargo.toml` Datei im aktuellen Verzeichnis oder seinem übergeordneten Verzeichnis. Um dieses Problem zu beheben, können Sie eine Option zu den Plugin-Einstellungen hinzufügen und den Standort Ihrer `Cargo` angeben. oml` Datei.

Wie in [diesem Kommentar](https://github. om/rust-lang/rust-analyzer/issues/2649#issuecomment-691582605), können Sie die folgenden Zeilen am Ende Ihrer Plugin-Einstellungen JSON hinzufügen. Anschließend starten Sie den Rust Analyzer neu, damit die Änderungen wirksam werden.

```json
{
    "rust-analyzer. inkedProjects": [
        "/home/stuart/raspirus/raspirus/Cargo.toml"
    ]
}
```
````

??? question "Can't select directories/files"
Unfortunately, as of [this issue](https://github.com/tauri-apps/tauri/issues/5405) with Tauri, we currently can't allow users to select both files and folders. Um zwischen der Auswahl einer einzelnen Datei oder eines einzelnen Ordners zu wechseln, müssen Sie diese in den Raspirus Einstellungen ändern. Dort finden Sie einen Schalter dafür.

??? question "What is obfuscated mode?"
Raspirus war ursprünglich für den Unternehmenseinsatz gedacht und musste daher privatfreundlich sein. Um dies zu gewährleisten, fügte es den "Obfuscation Mode" hinzu, der alles versteckt, Malware schneller erkennt und nur anzeigt: "Malware gefunden" oder "Keine Malware gefunden". Sie ist standardmäßig eingeschaltet, wenn Sie also etwas mehr über Ihren Scan wissen möchten, sollten Sie ihn wahrscheinlich deaktivieren. Sie können dies in den Einstellungen tun.

??? question "error: found a virtual manifest instead of a package manifest"
If you get this error when performing `cargo install` or using the Makefile, please note that it's a [know issue](https://github.com/rust-lang/cargo/issues/7599). The solution is simple, as explained on [this](https://stackoverflow.com/a/76271890) Stackoverflow answer, simply change the command to include the workspace, like this: `cargo install --path src-tauri/`

??? question "How do I add my own signatures to the main repository?"
Raspirus fetches signatures from the [signatures repository](https://github.com/Raspirus/signatures) and creates the database locally. You can add signatures to the repository by creating an issue or PR request on that repository. Or if you want to experiment with it locally, you can use the [signatures-builder](https://github.com/Raspirus/signature-builder) that we use to update the signatures in the signatures repository
