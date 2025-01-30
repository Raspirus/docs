# Gebrauchsanleitung

Raspirus ist ein unkompliziertes und benutzerfreundliches Erlebnis. Es entfällt auf Tastatur oder Maus durch eine vollständig Touchscreen-basierte Schnittstelle. Die Anwendung wurde im Hinblick auf Einfachheit entwickelt, um sicherzustellen, dass das Navigieren und Benutzen von Raspirus intuitiv ist. In diesem Abschnitt werden wir die verfügbaren Einstellungen und Funktionalitäten detaillierter erläutern.

## Protokolle und Konfigurationen navigieren

Bei unerwarteten Fehlern oder einem Absturz der Anwendung kann die Überprüfung von Logs und Konfigurationsdateien wertvolle Einblicke bieten. Diese Dateien werden in plattformspezifischen Verzeichnissen gespeichert, die von der [ProjectDirs crate](https://docs.rs/directories-next/latest/directories_next/struct.ProjectDirs.html).

### Speicherort der Protokolldatei

Die Logdateien werden je nach Betriebssystem an verschiedenen Stellen gespeichert. Unten ist eine Tabelle mit den Standardpfaden:

| Plattform | Pfad                                                                                         | Beispiel                                                        |
| --------- | -------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Linux     | `$XDG_DATA_HOME`/`_project_path_` oder `$HOME`/.local/share/`_project_path_` | `/home/alice/.local/share/barapp`                               |
| macOS     | `$HOME`/Library/Application Support/`_project_path_`                                         | `/Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App` |
| Fenster   | `{FOLDERID_LocalAppData}`\\`_project_path_`\data                                           | `C:\Users\Alice\AppData\Local\Foo Corp\Bar App\data`     |

Wenn Sie Fehler oder Probleme melden, stellen Sie sicher, dass Sie diese Logdateien einfügen, da sie bei der Fehlerbehebung erheblich helfen.

## Konfigurationsdatei

Die Konfigurationsdatei enthält wichtige Einstellungen, die auch nach dem Schließen der Anwendung beibehalten werden. Es ist wichtig, diese Einstellungen nicht zu ändern, es sei denn, Sie kennen ihre Funktion, da unsachgemäße Änderungen verhindern könnten, dass die Anwendung startet.

### Speicherort der Konfigurationsdatei

Die Konfigurationsdatei befindet sich in plattformspezifischen Verzeichnissen, wie unten gezeigt:

| Plattform | Pfad                                                                                         | Beispiel                                                        |
| --------- | -------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Linux     | `$XDG_DATA_HOME`/`_project_path_` oder `$HOME`/.local/share/`_project_path_` | `/home/alice/.local/share/barapp`                               |
| macOS     | `$HOME`/Library/Application Support/`_project_path_`                                         | `/Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App` |
| Fenster   | `{FOLDERID_RoamingAppData}`\\`_project_path_`\data                                         | `C:\Users\Alice\AppData\Roaming\Foo Corp\Bar App\data`   |

### Konfiguration

Wenn Sie Raspirus weiter anpassen müssen, können Sie die Konfigurationsdatei manuell bearbeiten. Zum Beispiel:

- **Zentralisierte Config Distribution**: Ersetzen Sie die Konfigurationsdatei auf dem System eines jeden Benutzers beim Start, um eine gemeinsame Konfiguration zu erzwingen.
- **Benutzerdefinierte Einstellungen**: Setze bestimmte Werte, wie den Pfad zu benutzerdefinierten YARA-Regeln oder Einstellungen für Scan-Verhalten.

Weitere Details zur Verwendung und Änderung der Konfigurationsdatei finden Sie auf der [Entwicklerseite](developers.md#configuration).

## Scannen

Mit Raspirus können Sie bestimmte Dateien, Ordner und externe Laufwerke auf potenzielle Bedrohungen von Malware scannen. Der Scanning-Prozess überprüft Dateien mit einer Datenbank von YARA-Regeln, die darauf ausgelegt sind, bekannte bösartige Muster zu erkennen.

### Unterstützte Scanziele

Raspirus kann scannen:

- Ein Ordner und alle Unterordner.
- Eine einzelne Datei, inklusive komprimierter Dateien (z.B. ZIP, TAR).
- Ein abnehmbares Laufwerk (z.B. USB-Stick).

### Berechtigungen und Einschränkungen

Um Dateien zu scannen, benötigt Raspirus Lesezugriff auf die betreffenden Dateien oder Verzeichnisse. Es kann nicht auf passwortgeschützte komprimierte Dateien oder Ordner zugreifen, die von Ihrem Betriebssystem eingeschränkt sind.

!!! warning "wichtig!"
Versuchen Sie nicht, Ihr gesamtes Betriebssystem oder Ihren Computer zu scannen. Für vollständige Systemsuche empfiehlt es sich, eine spezielle Antiviren-Lösung zu verwenden.

### Scanvorgang

Der Scanvorgang beinhaltet die Analyse von Dateien und deren Inhalten, die mit der YARA-Regeldatenbank übereinstimmen. Für komprimierte Dateien wird Raspirus den Inhalt extrahieren und scannen. Wenn eine Datei mit einem bekannten Malware-Muster übereinstimmt, wird sie als potenziell bösartig markiert.

### Post-Scan Aktionen

Nach Abschluss eines Scans:

- Wenn keine Bedrohungen erkannt werden, können Sie Ihre Aufgaben ohne Sorge fortsetzen.
- Wenn Malware gefunden wird, zeigt Raspirus eine Liste der markierten Dateien und der entdeckten Bedrohungen an.

!!! note "Übersprungene Dateien"
Wenn Raspirus nicht in der Lage ist, eine Datei zu scannen, überspringt sie, um den Scanvorgang nicht zu unterbrechen.
Übersprungene Dateien können normalerweise ignoriert werden, da sie normalerweise nur ein Berechtigungsproblem darstellen.

Raspirus bietet **nicht** Dateilöschungs- oder Quarantäneoptionen an, da die Erkennungsdatenbank gelegentlich falsche Positive generieren kann. We recommend reviewing flagged files carefully and making decisions based on your own judgment or submitting suspicious files to services like [VirusTotal](https://www.virustotal.com) for further analysis.
