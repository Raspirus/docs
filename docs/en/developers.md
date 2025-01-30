# Developers  

Welcome to the Raspirus developer guide! This page outlines everything you need to contribute effectively, from setting up your environment to understanding the architecture and updating YARA rules.  

---

## Setup  

To begin development, follow these steps:  

1. Clone the repository:  
    ```sh
    git clone https://github.com/Raspirus/raspirus.git
    cd raspirus
    ```  
2. Install [Rust](https://www.rust-lang.org/tools/install).  
3. Install the Raspirus package:  
    ```sh
    cargo install .
    ```  
4. Start development:  
    ```sh
    cargo run
    ```  
5. Or build Raspirus:  
    ```sh
    cargo build
    ```  

### Troubleshooting Setup Issues  
If you encounter issues while building or running Raspirus:  

- Ensure Rust is installed correctly.  
- Verify that logs and config files are created properly.  
- Check for dependency conflicts and missing packages.  

---

## Documentation  

Since Raspirus is written in Rust, you can generate developer documentation with:  
```sh
cargo doc --no-deps --open
```  
This will open the generated documentation in your browser.  

---

## Architecture  

Raspirus follows a **frontend-backend** architecture, with both components written in Rust.  

### Frontend  

- Uses **iced-rs** for GUI rendering.  
- Prioritizes user experience—ideally, users should never need to open the settings page.  
- Designed for **touch support**, minimizing keyboard input.  
- Plug-and-play: Can be replaced with another frontend if needed.  
- Simple structure, similar to a website with just a few pages.  

### Backend  

- **Multi-threaded** for efficient scanning.  
- Handles scanning, rule processing, and settings management.  
- Implements **YARA rules** for malware detection.  
- Well-documented functions—if in doubt, check the code directly.  
- Despite its complexity, it becomes easier to navigate once you start working with it.  

---

## Configuration  

The configuration file is stored in the default system configuration folder:  

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

### Key Fields  

- `config_version`: Determines if an older config needs to be overwritten.  
- `rules_version`: Tracks the last downloaded YARA rules version.  
- `min_matches`: Minimum number of rule matches required to flag a file.  
- `max_matches`: Maximum rule matches before stopping further checks.  
- `max_threads`: Number of CPU threads used for scanning.  
- `logging_is_active`: Enables/disables logging (useful when storage is limited).  
- `mirror`: API endpoint for fetching rule updates.  
- `language`: Current language (supports `fr`, `en`, `it`, `de`).  
- `dark_mode`: Toggles the application’s dark mode.  

---

## Mirrors  

The `mirror` setting in the config file should point to a Git API. Custom mirrors must provide JSON with the following structure:  

```json
{
  "tag_name": "v1.1",
  "zipball_url": "http://example.com/download.zip"
}
```  

- `tag_name`: Specifies the version for update checks.  
- `zipball_url`: Direct link to the `.zip` archive containing YARA rules.  

---

## Updater  

Raspirus has a **built-from-scratch updater** that:  

1. Checks the latest available version using the configured mirror.  
2. Downloads the `.zip` archive to cache.  
3. Compiles all `.yar` files into a `.yarac` (compiled YARA rules).  
4. Saves the compiled rules in:  
   - **Linux/macOS**: `~/.local/share/raspirus`  
   - **Windows**: `%appdata%\Roaming\Raspirus\Data`  
   - **macOS (App Bundle)**: `/Applications/Raspirus/data`  

### Release Archive Structure  

The update `.zip` should contain **uncompiled YARA `.yar` files**. The folder structure inside the archive does not matter, as files are added recursively.  

📌 **Windows Users:** If Windows Defender interferes with compiled YARA rules, an optional script can disable Defender scanning. See [this script](https://github.com/Raspirus/yara-rules/blob/main/scripts/windows.ps1).  
