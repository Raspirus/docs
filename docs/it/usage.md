# Usage Guide

Raspirus is designed to offer a straightforward and user-friendly experience. It eliminates the need for a keyboard or mouse by providing a fully touchscreen-based interface. The application has been developed with simplicity in mind, ensuring that navigating and using Raspirus is intuitive. In this section, we will explain the available settings and scanning functionalities in more detail.

## Navigazione di registri e configurazioni

In cases of unexpected errors or application crashes, reviewing logs and configuration files can provide valuable insights. These files are stored in platform-specific directories, managed by the [ProjectDirs crate](https://docs.rs/directories-next/latest/directories_next/struct.ProjectDirs.html).

### Log File Location

The log files are stored in different locations depending on the operating system. Below is a table of default paths:

| Piattaforma | Path                                                                                      | Esempio                                                         |
| ----------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Linux       | `$XDG_DATA_HOME`/`_project_path_` o `$HOME`/.local/share/`_project_path_` | `/home/alice/.local/share/barapp`                               |
| macOS       | `$HOME`/Library/Application Support/`_project_path_`                                      | `/Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App` |
| Finestre    | `{FOLDERID_LocalAppData}`\\`_project_path_`\data                                        | `C:\Users\Alice\AppData\Local\Foo Corp\Bar App\data`     |

When reporting bugs or issues, make sure to include these log files, as they help significantly in troubleshooting.

## Configuration File

The configuration file holds important settings that persist even after you close the application. It is essential not to alter these settings unless you are familiar with their function, as improper modifications could prevent the application from launching.

### Configuration File Location

The config file is located in platform-specific directories, as shown below:

| Piattaforma | Path                                                                                      | Esempio                                                         |
| ----------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Linux       | `$XDG_DATA_HOME`/`_project_path_` o `$HOME`/.local/share/`_project_path_` | `/home/alice/.local/share/barapp`                               |
| macOS       | `$HOME`/Library/Application Support/`_project_path_`                                      | `/Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App` |
| Finestre    | `{FOLDERID_RoamingAppData}`\\`_project_path_`\data                                      | `C:\Users\Alice\AppData\Roaming\Foo Corp\Bar App\data`   |

### Configuration

If you need to customize Raspirus further, you can manually edit the configuration file. For example:

- **Centralized Config Distribution**: Replace the config file on each user's system upon startup to enforce a common configuration.
- **Custom Settings**: Set specific values, such as the path to custom YARA rules or scan behavior preferences.

For more details on how to use and modify the configuration file, refer to the [developers page](developers.md#configuration).

## Scansione

Raspirus allows you to scan specific files, folders, and external drives for potential malware threats. The scanning process checks files against a database of YARA rules designed to detect known malicious patterns.

### Supported Scanning Targets

Raspirus can scan:

- A folder and all of its subfolders.
- A single file, including compressed files (e.g., ZIP, TAR).
- A detachable drive (e.g., USB stick).

### Permissions and Limitations

To scan files, Raspirus requires read access to the files or directories in question. It cannot access password-protected compressed files or folders that are restricted by your operating system.

!!! warning "Important!"
Do not attempt to scan your entire operating system or computer. For full system scans, it’s recommended to use a dedicated antivirus solution.

### Scanning Process

The scanning process involves analyzing files and their contents to match patterns against the YARA rule database. For compressed files, Raspirus will extract and scan the contents. If a file matches a known malware pattern, it will be flagged as potentially malicious.

### Post-Scan Actions

After completing a scan:

- If no threats are detected, you may continue your tasks without concern.
- If malware is found, Raspirus will display a list of flagged files and the detected threats.

!!! note "Skipped files"
If Raspirus is not able to scan a file, it will skip it to avoid having to interrupt the scanning process.
Skipped files can normally be ignored, as its usually just a permission problem.

Raspirus does **not** offer file deletion or quarantine options because the detection database may occasionally generate false positives. We recommend reviewing flagged files carefully and making decisions based on your own judgment or submitting suspicious files to services like [VirusTotal](https://www.virustotal.com) for further analysis.
