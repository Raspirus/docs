---
comments: wahr
---

# FAQ
In this page, we will answer your most asked questions. As more questions arise, we will expand this page to include more answers. This page is very useful if you encounter any errors during development or usage. Maybe your error can be easily fixed and doesn't require a bug report.

## What is the Icon of the project?
![Transparent logo](../img/transparent-logo.png) In case you didn't notice yet, this is the logo of the Raspirus app. It was generated with [DALL-E](https://openai.com/product/dall-e-2) and some creative image editing and merging. It should represent a red monster that eats viruses. His name is Stuart by the way, and don't worry, he is a very kind monster, except for when he is hungry, then you better feed him viruses. You can find more media and documents in the [dedicated repository](https://github.com/Raspirus/media). You are free to use these images to create your own art and showcase them in the [discussion boards](https://github.com/orgs/Raspirus/discussions)

## Wie generiere ich die Dokumentation für dieses Projektarchiv?
You can find the generated documentation in the [rust folder](/rust/) and in case you want to generate your own, you can do so by using the `cargo doc` command. Hier sind einige Parameter, die Sie mit ihm verwenden können:
- `--no-deps`: Ignoriert Abhängigkeiten, dokumentiert nur den Code selbst
- `--release`: Es ist im Allgemeinen besser als ein Debug
- `--target-dir`: Where to output the docs All together, the command might look something like this: \
  `cargo doc --no-deps --release --target-dir=/docs/generated/`

## In VS Code, how do I set up Rust analyzer to work in non-standard directory structure?
Das Rust Analyzer Plugin in Visual Studio Code versucht nach einer Cargo.toml Datei im aktuellen Verzeichnis oder übergeordnetem Verzeichnis zu suchen. But since we packed the entire application in the `app` directory, it's unable to find the file and therefore might not work. This is a big lost, as it doesn't tell you if your Rust files have correct syntax or not. Um dieses Problem zu lösen, können Sie dem Plugin eine Option hinzufügen und den Speicherort Ihrer Cargo.toml Datei angeben. As stated [in this comment](https://github.com/rust-lang/rust-analyzer/issues/2649#issuecomment-691582605), you need to add the following lines to the end of your plugin settings' JSON. Danach müssen Sie auch den Analyzer neu starten, damit die Änderung wirksam wird.

```json
{
    "rust-analyzer.linkedProjects": [
        "/home/matklad/tmp/hello/Cargo.toml"
    ]
}
```

## Updating database crashes app
On Windows, it seems like the app crashes when the user tries to update the database. We are aware of this issue and working to fix it. The issue arises because the function needs administrative privileges, which Windows isn't providing. To fix this issue for now, simply execute the app in administration mode, aka. With admin privileges. You can do so by right-clicking the app and clicking `Run as administrator`.