# Architecture

This page visualizes the general structure of the Raspirus project and its setup:

```mermaid
grafico LR
     A[Start] --> B{Posizione di scansione specificata? ;
     B --> Sì<unk> C[Start scan];
     C --> <unk> Start Loop<unk> D[File trovato];
     D --> E[Crea Hash];
     E --> F[Confronta Hash];
     F --> G{Hash trovato in DB? ;
     G --> <unk> Sì<unk> H[Contrassegna come malware];
     G --> <unk> No<unk> I[Contrassegna come sicuro];
     H & I --> J[Continue iteration];
     J --> K{Ultimo file? ;
     K --> <unk> Sì<unk> L[Stop scanner];
     L --> M[Display Results];
     K --> <unk> No<unk> N[Start again];
     N --> D;
     B --> <unk> No<unk> O[Stop]
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
