---
comments: true
---

# FAQ
In this page we will answer your most asked questions. As more questions arise, we will expand this page to include more answers. This page is very useful if you encounter any errors during developemnt or usage. Maybe your error can be easily fixed and doesn't require a bug report.

## How do I generate the documentation for this repository?
You can find the generated documentation in the [rust folder](/rust/) and in case you want to generate your own, you can do so by using the `cargo doc` command. Here are some parameters you might want to use with it:
- `--no-deps`: Ignores dependencies, only documents the code itself
- `--release`: It is generally better than a debug
- `--target-dir`: Where to output the docs All together, the command might look something like this: \
  `cargo doc --no-deps --release --target-dir=/docs/generated/`

## In VSCode, how do I set up Rust analyzer to work in non-standard directory structure?
The Rust analyzer plugin in Visual Studio Code tries to search for a Cargo.toml file in the current directory, or parent directory. But since we packed the entire application in the `app` directory, it's unable to find the file and therefore might not work. This is a big lost, as it doesn't tell you if your Rust files have correct syntax or not. To solve this issue, you can add an option to the plugin and specify the location of your Cargo.toml file. As stated [in this comment](https://github.com/rust-lang/rust-analyzer/issues/2649#issuecomment-691582605), you need to add the following lines to the end of your plugin settings' JSON. Afterward, you will also need to restart the Analyzer for the modification to take effect.

```json
{
    "rust-analyzer.linkedProjects": [
        "/home/matklad/tmp/hello/Cargo.toml"
    ]
}
```

## Updating database crashes app
On Windows it seems like the app crashes when the user tries to update the database. We are aware of this issue and working to fix it. The issue arises because the function needs administrative privileges, which Windows isn't providing. To fix this issue for now, simply execute the app in administration mode, aka. with admin privileges. You can do so by right-clicking the app and clicking `Run as administrator`.
