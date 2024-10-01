## Mirror
The mirror flag in the config file should ideally point to a git API. Custom Mirrors need to have the following structure in JSON
```json
{
	"tag_name": "String", // eg. v1.1
	"zipball_url": "String" // http://example/download.zip
}
```
- The `tag_name` supplies the version against which the local config gets checked
- The `zipball_url` should point to the `.zip` archive which contains the rules
## Updater
The new and written-from-scratch Updater looks up the newest version indicated by your mirror online, and downloads the release .zip file to cache. Once that succeeds, it starts compiling all the `.yar` files into a compiled `.yarac`. This gets saved to the data directory (`~/.local/share/raspirus`, `%appdata%\Roaming\Raspirus\Data`, `/Applications/Raspirus/data`)
## Release archive
The zip should contain `.yar` files, which are uncompiled, raw YARA rules. The structure of the archive does not matter, as the files get added recursively. On Microsoft Windows, an optional script can be supplied to disable Windows Defender, from scanning the created compiled rules on disk, as that might result in them getting deleted. An example can be found [here](https://github.com/Raspirus/yara-rules/blob/main/scripts/windows.ps1) . The script is run with the Data Folder as argument.
