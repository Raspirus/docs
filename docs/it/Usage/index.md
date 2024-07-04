# Usage

Using Raspirus is fairly simple. It has been designed to be used without a keyboard or mouse and completely with touchscreen.
Generally speaking you shouldn't have any issues trying to ue Raspirus, as the UI is made very simple.
In this section we further explain the available settings andscanning functionality.

## Navigazione di registri e configurazioni

In caso di eventi inaspettati o di crash improvvisi delle app, l'esame di registri e configurazioni può fornire approfondimenti. Individuare questi file nelle seguenti cartelle, in base al sistema operativo. Il [ProjectDirs crate](https://docs.rs/directories-next/latest/directories_next/struct.ProjectDirs.html) li memorizza nella posizione seguente:

**Log file location:**

| Piattaforma | Valore                                                                                    | Esempio                                                                                       |
| ----------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Linux       | `$XDG_DATA_HOME`/`_project_path_` o `$HOME`/.local/share/`_project_path_` | /home/alice/.local/share/barapp                                               |
| macOS       | `$HOME`/Library/Application Support/`_project_path_`                                      | /Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App |
| Finestre    | `{FOLDERID_LocalAppData}`\\`_project_path_`\data                                        | C:\Users\Alice\AppData\Local\Foo Corp\Bar App\data                            |

Assicurarsi di includere questi file durante la segnalazione di bug, in quanto aiutano notevolmente nella risoluzione dei problemi.
