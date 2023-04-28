---
comments: vero
---

# Backend

## Planing

![Raspirus Activity Diagram](../../img/RaspActDark.png#only-dark) ![Raspirus Activity Diagram](../../img/RaspActLight.png#only-light) This diagram describes how the logical flow of the app work. The exact flow can change in the future, but this was the initial planing of the app. As you can see, it is rather simple with just a couple if statements and a for-each loop. The backend is actually not that hard to understand, the complicated part is the more in-depth part of how to manage the database, scan files, create the hash and most importantly, communicate the result to the frontend by emitting signals.

## Database

The Database consists of a single big file with mainly two columns. This file is generated at runtime and can be updated with a button on the GUI. At the time of writing, this file is approximately 4 GB in size and can take up to an hour to generate. The database contains in one column all signatures as a primary key, and in the second column the name of the file they got extracted from, based on the [Virusshare database](https://virusshare.com/) file names.

### Structure

Here is how the database may look like:

| MD5 Hash                         | FileNr |
| -------------------------------- | ------ |
| ....                             | ....   |
| 40610db6af6eaf2391b7a169e2540de9 | 00219  |
| 64a613db4aa368108e6d4c15ef7f6454 | 00219  |
| ....                             | ....   |

### Initialisation

Here is the Rust code in the main.rs file that creates the Database:

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

If the specified `signatures.db` file doesn't exist, it will automatically attempt to create on and even create the necessary table. You can technically also provide your own file, just put it in the same folder as the executable. Also make sure that the table is the same.

## Scanner

The scanner class is the main function of the entire app. It takes a directory as parameter and starts scanning it. It will scan all folders and files recursively by hashing it and checking the hash in the database.

### Ignoring hashes (false positives)

In the `file_scanner.rs` file, where the scanner is declared, we also have an Array that contains signatures that should be ignored. Virusshare is a databse where Hashes are mostly added, not removed, and therefore we need to do our filtering on the client-side. For example there was a hash for empty files, but in our opinion empty file should not be flagged as dangerous, so we added an excemption:

```rust
let false_pos: Vec<String> = vec!["7dea362b3fac8e00956a4952a3d4f474".to_owned()];
```

### Obfuscated mode

Sometimes, for privacy reasons, you might not want to display the path and names of the found files, therefore the scanner provides a so-called 'Obfuscated mode'. Setting this to true will make the app fail immediately as soon as it finds a vairus, without scanning the entire folder, and output red or green depending on the security of the scan.

## Logging

The app also has a logger that keeps track of issues or warnings during the execution of the app. Sadly this only works in `dev` or `debug` mode. When packing ito an executable the logger is lost as it gets stripped away for better performance. We are nonetheless working on bringing it back to life in the future.
