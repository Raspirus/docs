# Architecture

This page visualizes the general structure of the Raspirus project and its setup:

```mermaid
graph LR
     A[Start] --> B{Scan location specified?};
     B --> |Yes| C[Start scan];
     C --> |Start Loop| D[File found];
     D --> E[Compare with rules];
     E --> F{Rule detected malware?};
     F --> |Yes| G[Flag as Malware];
     F --> |No| H[Flag as Safe];
     G & H --> I[Continue iteration];
     I --> J{Last file?};
     J --> |Yes| K[Stop scanner];
     K --> L[Display Results];
     J --> |No| M[Start again];
     M --> D;
     B --> |No| N[Stop]
```

Generally, we use a frontend-backend architecture, with both components written in Rust. The frontend uses the iced-rs framework and communicates with the backend natively using Rust.

## Backend

```mermaid
classDiagram
     Main <|-- DBOps
     Main <|-- Configs
     Main <|-- FileLogs
     Main <|-- Scanner
     Main: +Config config_file

     class DBOps {
          +Connection db_conn
          +String db_file
          +TauriWindow t_win
          +new()
          +update_db()
          +hash_exists()
     }

     class Configs {
          +Data data
          +new()
          +save()
          +load()
     }

     class FileLogs {
          +File file
          +log()
          +create_file()
     }

     class Scanner {
          +String scan_loc
          +Vec malware_list
          +search_files()
          +create_hash()
          +get_folder_size()
     }
```

## Frontend

### Home

![Screenshot of Home page](../img/screenshots/home.png)

### Scansione

![Screenshot del processo di scansione](../img/screenshots/scanning.png)

### Risultato

![Screenshot del risultato positivo](../img/screenshots/result.png)

### Configurazione Raspberry Pi

![Screenshot della Home page su Raspberry Pi](../img/screenshots/Rpihomesetup.jpg)

![Screenshot of Raspberry Pi setup](../img/screenshots/Rpisetup.jpg)

The visualization has evolved over the course of the project, but the page structure remains consistent.
