## Config
The config file gets saved in the default System Configuration Folder. The structure should be the following:
```json
{
  "config_version": "6",
  "rules_version": "v1.1.2",
  "min_matches": 0,
  "max_matches": 20,
  "max_threads": 12,
  "logging_is_active": true,
  "mirror": "https://api.github.com/repos/Raspirus/yara-rules/releases/latest",
  "language": "en",
  "dark_mode": true
}
```
This is an example from a running system with the latest release at the time of writing this.
- `config_version`: This field contains the current config version. Older configs get overwritten if the new program version ships with a higher config version.
- `rules_version`: The version of the rules that have been built last. This gets pulled from the `tag_name` field on the `mirror` JSON.
- `min_matches`: The minimum amount of rules that need to match on a file for it to be reported
- `max_matches`: The maximum amount of rules that match on a file, before no more matches get produced
- `max_threads`: The amount of parallel threads for scanning. This should ideally be the amount of CPU threads. Systems which need performance for other tasks or that might experience thermal issues at full CPU usage, can set this lower.
- `logging_is_active`:  If set to false, terminal and file logging get disabled. For diagnostics purposes this should usually be enabled. However if storage is limited, it can be disabled in order to avoid filling up the disk with logging. 
- `mirror`: This field points to the API endpoint described in the Updater.
- `language`: Contains the current language. At the time of writing this, supported languages are fr, en, it and de.
- `dark_mode`: Toggles the dark mode of the application interface