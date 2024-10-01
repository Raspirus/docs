## Config

The config file stores your settings when you close the app and includes some important variables. Avoid changing these values unless you know what you're doing, as a malformed file structure will prevent the app from starting.

### Location

| Piattaforma | Valore                                                                                    | Esempio                                                                                       |
| ----------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Linux       | `$XDG_DATA_HOME`/`_project_path_` o `$HOME`/.local/share/`_project_path_` | /home/alice/.local/share/barapp                                               |
| macOS       | `$HOME`/Library/Application Support/`_project_path_`                                      | /Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App |
| Finestre    | `{FOLDERID_RoamingAppData}`\\`_project_path_`\data                                      | C:\Users\Alice\AppData\Roaming\Foo Corp\Bar App\data                          |

### Structure

```json
{
  "config_version": "5",
  "rules_version": "None",
  "min_matches": 0,
  "max_matches": 20,
  "max_threads": 8,
  "logging_is_active": true,
  "mirror": "https://api.github.com/repos/Raspirus/yara-rules/releases/latest",
  "language": "en"
}
```

You can set a custom `mirror` to another URL. The mirror points to the location where all the rules are stored and uses them to build the database. This allows you to create your own database with custom YARA rules.

### Usage

You might want to manually change the config file if you have special requirements. For instance, you could distribute a central config to all users by replacing the config file on each startup. Another use case could be troubleshooting or setting custom settings, like the path to the yara rules.
