---
comments: wahr
---

# Backend

In the backend of the Raspirus app, several components work together to provide the desired functionality. This section outlines the planning, database structure, scanner, and logging aspects of the backend.

## Planning

The activity diagrams below illustrate the logical flow of the app. While the exact flow may evolve over time, these diagrams represent the initial planning of the app. The backend follows a relatively straightforward design, utilizing if statements and a for-each loop. The complexity lies in managing the database, scanning files, creating hashes, and communicating the results to the frontend through signal emissions.

Activity Diagram: ![Raspirus Activity Diagram - Dark Mode](../../img/RaspActDark.png#only-dark) ![Raspirus Activity Diagram - Light Mode](../../img/RaspActLight.png#only-light)

## Database

The database consists of a single large file with two main columns. This file is generated at runtime and can be updated through a button on the GUI. At the time of writing, the database file is approximately 4 GB in size and can take up to an hour to generate. The first column contains all signatures as primary keys, while the second column contains the corresponding file names extracted from the [Virusshare database](https://virusshare.com/) file names.

### Structure

The database structure is as follows:

| MD5 Hash                         | FileNr |
| -------------------------------- | ------ |
| ....                             | ....   |
| 40610db6af6eaf2391b7a169e2540de9 | 00219  |
| 64a613db4aa368108e6d4c15ef7f6454 | 00219  |
| ....                             | ....   |

### Initialization

The following Rust code in the `main.rs` file creates the database:

```rust
let mut use_db = "signatures.db".to_owned();
match dbfile {
    Some(fpath) => {
        if Path::new(&fpath).to_owned().exists() && Path::new(&fpath).to_owned().is_file() {
            info!("Using specific DB path {}", fpath);
            use_db = fpath.to_owned();
        } else {
            info!("Falling back to default DB file (signatures.db)");
        }
    }
    None => {
        info!("Path is None; Falling back to default DB file (signatures.db)");
    }
};
```

If the specified `signatures.db` file doesn't exist, the code will attempt to create it and the necessary table. You can also provide your own file by placing it in the same folder as the executable. Just ensure that the table structure is the same.

## Scanner

The scanner class is the core function of the app. It takes a directory as a parameter and starts scanning it. It recursively scans all folders and files by hashing them and checking the hash in the database for matches.

### Ignoring Hashes (False Positives)

In the `file_scanner.rs` file, where the scanner is defined, there is an array that contains signatures to be ignored. Since Virusshare primarily adds hashes and rarely removes them, we need to handle filtering on the client-side. For example, if there is a hash for empty files, we added an exemption to prevent them from being flagged as dangerous:

```rust
let false_pos: Vec<String> = vec!["7dea362b3fac8e00956a4952a3d4f474".to_owned()];
```

### Obfuscated Mode

To address privacy concerns, the scanner offers an "Obfuscated mode." When enabled, the app immediately fails upon finding a virus without scanning the entire folder

. It outputs red or green depending on the security of the scan, without revealing the path and names of the detected files.

## Logging

The app incorporates a logger that tracks issues or warnings during execution. However, the logger only functions in `dev` or `debug` mode. When packing the app into an executable, the logger is stripped away for improved performance. Efforts are underway to reintroduce logging functionality in the future.