# Architecture

This page visualizes the general structure of the Raspirus project and its setup:

``` mermaid
graph LR
     A[Start] --> B{Scan location specified?};
     B --> |Yes| C[Start scan];
     C --> |Start Loop| D[File found];
     D --> E[Create Hash];
     E --> F[Compare Hash];
     F --> G{Hash found in DB?};
     G --> |Yes| H[Flag as Malware];
     G --> |No| I[Flag as Safe];
     H & I --> J[Continue iteration];
     J --> K{Last file?};
     K --> |Yes| L[Stop scanner];
     L --> M[Display Results];
     K --> |No| N[Start again];
     N --> D;
     B --> |No| O[Stop]
```

Generally, we use a frontend-backend architecture, with both components written in Rust. The frontend uses the Leptos framework and communicates with the backend via Tauri through WebAssembly

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
          +DbOps db_ops
          +Vec malware_list
          +search_files()
          +create_hash()
          +get_folder_size()
     }
```

## Frontend
<iframe title="The original Raspirus project on Figma" style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FpkgpwieNbhYiOi4Gz6Uyt6%2FRaspirus%3Fnode-id%3D0%253A1%26t%3DGr4YG3Ynv24YVlz2-1" allowfullscreen></iframe> 

The visualization has evolved over the course of the project, but the page structure remains consistent.