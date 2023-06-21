# How to Cross-Compile Raspirus for the Raspberry Pi

> **Note:** The following guide explains how to cross-compile the Raspirus application from a Linux machine to run on a Raspberry Pi. Please ensure that you have a Linux machine with GLIBC compatible with your target Raspberry Pi.

## Prerequisites

Before proceeding with the cross-compilation process, ensure that you have the following:

- A Linux machine with GLIBC compatible with the target Raspberry Pi.

## Initial Setup

To begin cross-compiling Raspirus, follow these initial setup steps to install Rust, Node.js, Tauri, and their dependencies:

1. Update the Linux distribution:

   ```sh
   sudo apt-get update && sudo apt-get upgrade -y
   ```

2. Install Tauri system requirements by executing the following command:

   ```sh
   sudo apt install libwebkit2gtk-4.0-dev \
       build-essential \
       curl \
       wget \
       libssl-dev \
       libgtk-3-dev \
       libayatana-appindicator3-dev \
       librsvg2-dev
   ```

3. Install Rust by running the following command:

   ```sh
   curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
   ```

   Ensure that Rust is up-to-date:

   ```sh
   rustup update
   ```

4. Install Tauri using Cargo, the Rust package manager:

   ```sh
   cargo install tauri-cli
   ```

5. Install Node.js using your preferred method. For example, on Windows WSL, you can follow this [guide](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl#install-nvm-nodejs-and-npm). The steps involve installing NVM (Node Version Manager) and then installing Node.js using NVM.

6. Remove any existing `node_modules` directory from the project folder:

   ```sh
   sudo rm -rf node_modules
   ```

7. Install the required Node.js modules:

   ```sh
   npm install
   ```

8. **Important!** If you are using Linux WSL, add the following dependency to the `Cargo.toml` file located in `<project-root>/src-tauri/`:

   In the `[dependencies]` section, add the following line:

   ```toml
   openssl-sys = { version = "0.9.66", features = ["vendored"] }
   ```

## Cross-Compiling

The following steps explain how to compile Raspirus for the Raspberry Pi on an x86_64 Linux host:

1. Install the Rust target for the Raspberry Pi:

   ```sh
   rustup target add armv7-unknown-linux-gnueabihf
   ```

2. Install the linker for ARM:

   ```sh
   sudo apt install gcc-arm-linux-gnueabihf
   ```

3. Open or create the file `.cargo/config.toml` in the project root directory and add the following:

   ```toml
   [target.armv7-unknown-linux-gnueabihf]
   linker = "arm-linux-gnueabihf-gcc"
   ```

4. Enable `armhf` in the package manager:

   ```sh
   sudo dpkg --add-architecture armhf
   ```

5. Update the package sources by opening the file `/etc/apt/sources.list` and adding the following lines (Note: This step can be ignored in Debian):

   ```plaintext
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-

ports jammy main restricted
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy-updates main restricted
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy universe
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy-updates universe
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy multiverse
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy-updates multiverse
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy-backports main restricted universe multiverse
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy-security main restricted
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy-security universe
   deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports jammy-security multiverse
   ```

6. Verify that the `armhf` architecture is still enabled:

   ```sh
   sudo dpkg --add-architecture armhf
   ```

7. Update the package information:

   ```sh
   sudo apt-get update && sudo apt-get upgrade -y
   ```

8. Install `webkitgtk` for the ARM architecture:

   ```sh
   sudo apt install libwebkit2gtk-4.0-dev:armhf
   ```

9. Set the `PKG_CONFIG_SYSROOT_DIR` environment variable to tell `pkg-config` where to find the libraries for the ARM architecture:

   ```sh
   export PKG_CONFIG_SYSROOT_DIR=/usr/arm-linux-gnueabihf/
   ```

10. Finally, build the Raspirus application for the Raspberry Pi:

    ```sh
    cargo tauri build --target armv7-unknown-linux-gnueabihf
    ```

## Conclusione

Once the cross-compilation process is complete, you will find the static website in the `out` folder. Please note that if you encounter any issues during the process, such as the inability to run the project, it can be safely ignored as you are likely not on a Raspberry Pi, and therefore, running it directly is not possible.

Congratulations! You have successfully cross-compiled Raspirus for the Raspberry Pi.