# Developers

## Setup

1. Clone the repository.
2. Install [Rust](https://www.rust-lang.org/tools/install).
3. Install the Rust package with:
    ```sh
    cargo install .
    ```
4. Start development with:
    ```sh
    cargo run
    ```
5. Or build Raspirus with:
    ```sh
    cargo build
    ```

Should you encounter any issues during your initial run or build, ensure that you've followed each step carefully. Confirm the accurate creation of both logs and config files.

## Documentation

Since the entire project is written in Rust, you can generate the documentation with:
```sh
cargo doc --no-deps --open
```

This command will open the documentation in your browser.