# Developers

## Setup

1. Clone the repository.
2. Install [Rust](https://www.rust-lang.org/tools/install).
3. Install [Tauri and Prerequisites](https://v2.tauri.app/start/prerequisites).
4. Install Trunk with:
    ```sh
    cargo install trunk
    ```
5. Install the `src-tauri` submodule:
    ```sh
    cargo install --path src-tauri/
    ```
6. Start development with:
    ```sh
    cargo tauri dev
    ```
7. Or build Raspirus with:
    ```sh
    cargo tauri build
    ```

Should you encounter any issues during your initial run or build, ensure that you've followed each step carefully. Confirm the accurate creation of both logs and config files.

## Documentation

Since the entire project is written in Rust, you can generate the documentation with:
```sh
cargo doc --no-deps --workspace --open
```

This command will open the documentation in your browser.