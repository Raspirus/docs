---
comments: vero
---

# Installazione
This guide provides instructions on how to install the Raspirus application on your machine.

## Using Executables
The quickest and simplest method to install the application is by using one of the executables available on the [Release page](https://github.com/Raspirus/Raspirus/releases/latest). Once you have downloaded the executable, the installation process may vary depending on your system. For example, on Windows, you can double-click the executable and follow the installation instructions provided by the wizard. Once completed, the installation process is finished.

## Using the Makefile (Debian-based Systems Only)
The project includes a Makefile that facilitates installation, updating, and testing. To install the application, you can clone the repository and execute the Makefile using the following command:

```sh
make install
```

## Limitazioni
- Glibc can cause issues on Linux. Please refer to the [limitations](https://tauri.app/v1/guides/building/linux#limitations) section of the Tauri documentation for more information.
- The application requires a 64-bit system. Running it on a different system architecture may result in crashes due to the utilization of memory improvements specific to 64-bit systems.

## Step-by-Step Guide
Before executing each step, we recommend reading the entire guide thoroughly.

### Step 1: Clone the Repository
If you have `git` installed, use the following command to clone the repository:

```sh
git clone https://github.com/Raspirus/Raspirus.git
```

Alternatively, you can download the repository as a ZIP file from [here](https://github.com/Raspirus/Raspirus/) and extract its contents. The [GitHub guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) provides further assistance on this process.

### Step 2: Install Rust
For **Linux** (Debian, Ubuntu):

```sh
curl https://sh.rustup.rs -sSf | sh -s -- --help
```

For **Windows**: Download the Rust executable from the [Rust website](https://www.rust-lang.org/tools/install) and follow the installation instructions.

### Step 3: Install NPM
For **Linux** (Debian, Ubuntu):

```sh
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - && \
sudo apt-get install -y nodejs
```

For **Windows**: Visit the [NPM Website](https://docs.npmjs.com/cli/v7/configuring-npm/install) to download the NPM executable and proceed with the installation.

### Step 4: Install Next.js
Use the following command with npm to install Next.js and its dependencies:

```sh
npm install next@latest react@latest react-dom@latest eslint-config-next@latest
```

### Step 5: Install Tauri
Tauri is the framework that connects the Rust backend with the Next.js frontend. Follow these steps to install Tauri:

1. Make sure you meet the [Prerequisites](https://tauri.app/v1/guides/getting-started/prerequisites) specified by Tauri.
2. Install Tauri using cargo with the following command:

   ```sh
   cargo install tauri-cli
   ```

   Note: We primarily work with cargo in this guide. Refer to [their FAQ section](https://tauri.app/v1/guides/faq#node-or-cargo) to learn about the alternative NPM installation.

### Step 6: Install Project Dependencies
To install the project dependencies, follow these steps:

1. Navigate to the directory that contains the Raspirus code.
2. Open a terminal in the `Raspirus` directory.
3. Execute the command `npm install` to install the necessary node modules.
4. Note: If you encounter an "OpenSSL is missing" error on WSL, resolve it by editing the file `Raspirus/src-tauri/Cargo.toml`. Add the following line to the `[dependencies]` section: `openssl-sys = {version = "0.9.66", features = ["vendored"]}`.

### Step 7: Build the Project
Before building the project, ensure the Rust part works correctly (optional):

1. Open the folder `Raspirus/src-tauri/`.
2. Run the command `cargo build`.
3. If the command succeeds, return to the `Raspirus/` directory.
4. If the command fails, please [open an issue](https://github.com/Raspirus/Raspirus/issues/new) on this repository, providing detailed information about the error.

To build the entire application:

1. In the `Raspirus/` directory, execute the command `cargo tauri build`.
2. After the process completes, the executable file's path will be displayed.
3. By default, the executable is located in the `Raspirus\src-tauri\target\release` folder.

### Step 8: Install the Raspirus Debian Package (for Debian-based Systems)
For Debian-based systems, an alternative installation method is available using the `.deb` package generated in the `Raspirus/src-tauri/target/release/bundle/deb` folder. Follow these steps to install the package:

1. Open a terminal in the `Raspirus/src-tauri/target/release/bundle/deb` directory.
2. Execute one of the following commands:

   - Using `apt`:

     ```sh
     sudo apt install ./raspirus-x.x.x_amd64.deb
     ```

   - Using `dpkg`:

     ```sh
     sudo dpkg -i raspirus-x.x.x_amd64.deb
     ```

   Replace `x.x.x` with the actual version number of the Raspirus package.

### Step 9: Execute the Application
After successfully building and installing the Raspirus application, you can execute it using the following command:

```sh
raspirus
```

Executing this command will launch the Raspirus application. Congratulations! You have now completed the installation process and can begin using the Raspirus app.

## Conclusione
The Raspirus application combines a website interface with underlying Rust code, packaged using the Tauri framework. To launch and display the website, a graphical overlay is required. As the project is continually evolving, we encourage you to open an issue on the repository if you encounter any unusual behavior, have suggestions, or discover errors. We are here to assist you.
