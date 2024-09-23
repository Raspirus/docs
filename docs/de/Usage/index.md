# Usage

Using Raspirus is fairly simple. It has been designed to be used without a keyboard or mouse and completely with touchscreen.
Generally speaking you shouldn't have any issues trying to ue Raspirus, as the UI is made very simple.
In this section we further explain the available settings and scanning functionality.

## Protokolle und Konfigurationen navigieren

Bei unerwarteten Vorfällen oder plötzlichen Abstürzen der App kann die Prüfung von Logs und Konfigurationen Einblicke bieten. Suchen Sie diese Dateien in den folgenden Ordnern, basierend auf Ihrem Betriebssystem. Das [ProjectDirs crate](https://docs.rs/directories-next/latest/directories_next/struct.ProjectDirs.html) speichert diese an der folgenden Stelle:

**Log file location:**

| Plattform | Wert                                                                                         | Beispiel                                                                                         |
| --------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Linux     | `$XDG_DATA_HOME`/`_project_path_` oder `$HOME`/.local/share/`_project_path_` | /home/alice/.local/share/barapp                                                  |
| macOS     | `$HOME`/Library/Application Support/`_project_path_`                                         | /Benutzer/Alice/Library/Application Support/com.Foo-Corp.Bar-App |
| Fenster   | `{FOLDERID_LocalAppData}`\\`_project_path_`\data                                           | C:\Benutzer\Alice\AppData\Local\Foo Corp\Bar App\data                            |

Stellen Sie sicher, dass Sie diese Dateien beim Melden von Fehlern einfügen, da sie bei der Fehlerbehebung sehr hilfreich sind.
