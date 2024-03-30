# GUIDES

## Lokale Dokumentation einrichten

Richten Sie einfach die Dokumentation auf Ihrem Rechner mit diesen einfachen Schritten ein:

1. Clone this repository by following the instructions on [GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository).

   ```bash
   git clone https://github.com/Raspirus/docs.git
   ```

2. Navigate to the cloned directory and install the required dependencies.

   ```bash
   You can install the dependencies by running the following command: `pip install -r requirements.txt`.
   ```

3. Starte das Projekt lokal:
   Beginne dein lokales Projekt, indem du diesen Befehl ausführst:

   ```bash
   mkdocs dienen
   ```

   Dies wird einen Entwicklungsserver initiieren, der dir erlaubt, die Dokumentation über [http://localhost:8000](http://localhost:8000) in deinem bevorzugten Webbrowser zuzugreifen.

## Export to PDF

If you would like to have an offline version of this documentation in PDF format, you can follow these step-by-step instructions:

1. Folgen Sie den oben beschriebenen Installationsprozess.

2. Install [mkdocs](https://www.mkdocs.org/user-guide/installation/) and execute the build command: `mkdocs build`.

3. If everything goes smoothly, the resulting PDF file should be located in the `site/pdf` directory with the name `document.pdf`.

Please be aware that the exported PDF may have some issues with images and iFrames, but the text should be readable and suitable for sharing offline. Dennoch bleibt der Text lesbar und für die Offline-Freigabe geeignet.

## Übersetzungen

Für Übersetzungen dieser Dokumentation besuchen Sie bitte [Crowdin](https://crowdin.com/project/raspirus), eine gemeinschaftliche Plattform. Übersetzungen für UI-Zeichenketten werden über JSON-Dateien verwaltet. Erstelle deine Übersetzungen im [locales Ordner](https://github.com/Raspirus/Raspirus/tree/main/public%2Flocales). Behalte die Einzigartigkeit der Schlüssel bei der Übersetzung aus der `en.json` Datei.

## Scanner-Einblicke

### Scanne komprimierte Dateien

!!! notiz

```
Diese Option ist für die Raspberry Pi noch nicht verfügbar. Schau, warum in der [FAQ Sektion](https://raspirus.github.io/docs/faq)
```

Während Raspirus standardmäßig Ordner scannt, können Sie dieses Verhalten über die Einstellungsseite ändern. Durch Umschalten können Sie einzelne Dateien, einschließlich komprimierter Dateien, scannen. Es ist wichtig zu beachten, dass nur eine Datei gleichzeitig gescannt werden kann.

### Protokolle und Konfigurationen navigieren

Bei unerwarteten Vorfällen oder plötzlichen Abstürzen der App kann die Prüfung von Logs und Konfigurationen Einblicke bieten. Suchen Sie diese Dateien in den folgenden Ordnern, basierend auf Ihrem Betriebssystem. Das [ProjectDirs crate](https://docs.rs/directories-next/latest/directories_next/struct.ProjectDirs.html) speichert diese an der folgenden Stelle:

**Konfigurationsdatei:**

| Plattform | Wert                                                                         | Beispiel                                                         |
| --------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Linux     | `$XDG_DATA_HOME`/`_project_path_` oder `$HOME`/.local/share/`_project_path_` | /home/alice/.local/share/barapp                                  |
| macOS     | `$HOME`/Library/Application Support/`_project_path_`                         | /Benutzer/Alice/Library/Application Support/com.Foo-Corp.Bar-App |
| Fenster   | `{FOLDERID_RoamingAppData}`\\`_project_path_`\data                           | C:\Benutzer\Alice\AppData\Roaming\Foo Corp\Bar App\data          |

**Logdateien:**

| Plattform | Wert                                                                         | Beispiel                                                         |
| --------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Linux     | `$XDG_DATA_HOME`/`_project_path_` oder `$HOME`/.local/share/`_project_path_` | /home/alice/.local/share/barapp                                  |
| macOS     | `$HOME`/Library/Application Support/`_project_path_`                         | /Benutzer/Alice/Library/Application Support/com.Foo-Corp.Bar-App |
| Fenster   | `{FOLDERID_LocalAppData}`\\`_project_path_`\data                             | C:\Benutzer\Alice\AppData\Local\Foo Corp\Bar App\data            |

Stellen Sie sicher, dass Sie diese Dateien beim Melden von Fehlern einfügen, da sie bei der Fehlerbehebung sehr hilfreich sind.

## Die Anreicherung der Signaturdatenbank

Raspirus has its own [signatures repository](https://github.com/Raspirus/signatures) which are collected from various sources and updated approximately once or twice every month. You can check out all the signatures there and report false positives or missing signatures directly there by opening an issue or Pull request.
If you want to build your own signatures database, you can use the [signature-builder](https://github.com/Raspirus/signature-builder).

## Raspberry Pi Einsatz

Ursprünglich für den eigenständigen Einsatz von Raspberry Pi mit Touchscreen-Funktionalität (ähnlich dem Kiosk Modus) konzipiert, war dieses Projekt in erster Linie das Scannen angehängter USB-Laufwerke. Während der Umfang des Projekts erweitert wurde, bleibt diese Funktion intakt. Folge der [Anleitung auf Tauri](https://tauri.app/v1/guides/building/linux#manual-compilation) und wenn du Probleme damit hast, lass es uns wissen.
We also provide pre-built executables on [our website](https://raspirus.deno.dev/)!

Vielen Dank, dass Sie Raspirus als Ihre Malware-Schutzlösung gewählt haben. Diese umfassenden Führer sorgen dafür, dass Ihre Erfahrung nahtlos und effizient ist.
