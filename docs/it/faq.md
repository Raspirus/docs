---
comments: true
---

# FAQ
In this page we will answer your most asked questions. As more questions arise, we will expand this page to include more answers. This page is very useful if you encounter any errors during developemnt or usage. Maybe your error can be easily fixed and doesn't require a bug report.

## Come posso generare la documentazione per questo repository?
You can find the generated documentation in the [rust folder](/rust/) and in case you want to generate your own, you can do so by using the `cargo doc` command. Ecco alcuni parametri che potresti voler utilizzare con esso:
- `--no-deps`: Ignora le dipendenze, documenta solo il codice stesso
- `--release`: Generalmente è meglio di un debug
- `--target-dir`: Where to output the docs All together, the command might look something like this: \
  `cargo doc --no-deps --release --target-dir=/docs/generated/`

## In VSCode, come posso impostare l'analizzatore di Rust per lavorare nella struttura di directory non standard?
Il plugin dell'analizzatore Rust in Visual Studio Code cerca di cercare un file Cargo.toml nella directory corrente o nella directory principale. But since we packed the entire application in the `app` directory, it's unable to find the file and therefore might not work. This is a big lost, as it doesn't tell you if your Rust files have correct syntax or not. Per risolvere questo problema, è possibile aggiungere un'opzione al plugin e specificare la posizione del file Cargo.toml. As stated [in this comment](https://github.com/rust-lang/rust-analyzer/issues/2649#issuecomment-691582605), you need to add the following lines to the end of your plugin settings' JSON. In seguito, dovrai anche riavviare l'analizzatore per rendere effettiva la modifica.

```json
{
    "rust-analyzer.linkedProjects": [
        "/home/matklad/tmp/hello/Cargo.toml"
    ]
}
```

## Updating database crashes app
On Windows it seems like the app crashes when the user tries to update the database. We are aware of this issue and working to fix it. The issue arises because the function needs administrative privileges, which Windows isn't providing. To fix this issue for now, simply execute the app in administration mode, aka. with admin privileges. You can do so by right-clicking the app and clicking `Run as administrator`.
