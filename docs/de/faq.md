---
comments: wahr
---

# FAQ

Welcome to our FAQ section, where we address some of the most frequently asked questions. If you encounter any errors or have queries during development or usage, this page can provide you with useful information. We continually update this section as new questions arise.

## What is the project's icon?

![Transparent logo](../img/transparent-logo.png)

The logo of the Raspirus app features a red monster named Stuart, who is designed to represent a virus-eating creature. The logo was generated using [DALL-E](https://openai.com/product/dall-e-2), along with creative image editing and merging. Stuart is a friendly monster, except when he's hungry for viruses. You can find additional media and documents in the [dedicated repository](https://github.com/Raspirus/media). Feel free to use these images to create your own artwork and share them in the [discussion boards](https://github.com/orgs/Raspirus/discussions).

## How can I generate the documentation for this repository?

The generated documentation can be found in the [rust folder](/rust/). If you want to generate your own documentation, you can use the `cargo doc` command. Here are some parameters you may find useful:

- `--no-deps`: Ignores dependencies and only documents the code itself.
- `--release`: Generates documentation optimized for release builds.
- `--target-dir`: Specifies the output directory for the documentation.

Putting it all together, the command might look like this:

```shell
cargo doc --no-deps --release --target-dir=/docs/generated/
```

## How do I set up Rust Analyzer in VS Code to work with a non-standard directory structure?

The Rust Analyzer plugin in Visual Studio Code searches for a `Cargo.toml` file in the current directory or its parent directory. However, in our case, since the entire application is packed in the `app` directory, the plugin may not work as expected. To address this issue, you can add an option to the plugin settings and specify the location of your `Cargo.toml` file.

As mentioned in [this comment](https://github.com/rust-lang/rust-analyzer/issues/2649#issuecomment-691582605), you can add the following lines to the end of your plugin settings JSON. Afterward, restart the Rust Analyzer for the modifications to take effect.

```json
{
    "rust-analyzer.linkedProjects": [
        "/home/stuart/raspirus/raspirus/Cargo.toml"
    ]
}
```

## The app crashes when updating the database

On Windows, it has been observed that the app crashes when attempting to update the database. We are aware of this issue and actively working to resolve it. The problem arises because the update function requires administrative privileges, which Windows does not automatically provide. To temporarily resolve this issue, you can execute the app with administrative privileges. Right-click on the app and select "Run as administrator" to launch it with the necessary privileges.