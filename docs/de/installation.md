---
comments: wahr
---

# Installation
This guide provides instructions on how to install the Raspirus application on your machine.

## Using Executables
The quickest and simplest method to install the application is by using one of the executables available on the [Release page](https://github.com/Raspirus/Raspirus/releases/latest). Once you have downloaded the executable, the installation process may vary depending on your system. For example, on Windows, you can double-click the executable and follow the installation instructions provided by the wizard. Once completed, the installation process is finished.

## Using the Makefile (Debian-based Systems Only)
The project includes a Makefile that facilitates installation, updating, and testing. To install the application, you can clone the repository and execute the Makefile using the following command:
```sh
make install
```

## Einschränkungen
- Glibc can cause issues on Linux. Please refer to the [limitations](https://tauri.app/v1/guides/building/linux#limitations) section of the Tauri documentation for more information.
- The application requires a 64-bit system. Running it on a different system architecture may result in crashes due to the utilization of memory improvements specific to 64-bit systems.

## Step-by-Step Guide
Before executing each step, we recommend reading the entire guide thoroughly.

### 1. Clone the Repository
If you have `git` installed, use the following command to clone the repository:
```sh
git clone https://github.com/Raspirus/Raspirus.git
```
Alternatively, you can download the repository as a ZIP file from [here](https://github.com/Raspirus/Raspirus/) and extract its contents. The [GitHub guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) provides further assistance on this process.

### 2. Rust installieren
For **Linux** (Debian, Ubuntu):
```sh
curl https://sh.rustup.rs -sSf | sh -s -- --help
```
For **Windows**: Download the Rust executable from the [Rust website](https://www.rust-lang.org/tools/install) and follow the installation instructions.

### 3. Install NPM
For **Linux** (Debian, Ubuntu):
```sh
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```
For **Windows**: Visit the [NPM Website](https://docs.npmjs.com/cli/v7/configuring-npm/install) to download the NPM executable and proceed with the installation.

### 4. Next.js installieren
Use the following command with npm to install Next.js and its dependencies:
```sh
npm install next@latest react@latest react-dom@latest eslint-config-next@latest
```

## Schlussfolgerung
The Raspirus application combines a website interface with underlying Rust code, packaged using the Tauri framework. To launch and display the website, a graphical overlay is required. As the project is continually evolving, we encourage you to open an issue on the repository if you encounter any unusual behavior, have suggestions, or discover errors. We are here to assist you.