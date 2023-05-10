---
comments: true
---

# Installation
This guide will help you in building the project on your own machine.

## Use an executable
The fastest and easiest way to install the app on your system is using one of the executables provided in the [Release page](https://github.com/Raspirus/Raspirus/releases/latest). Once downloaded, it will depend on your system on how to run it, but on Windows for example you can easily double-klick on the executable and follow the installation instructions from the wizard. And that's it, you are done.

## Use the Makefile (Debian based systems only)
The project also features a Makefile for easier installation, update and testing. You can therefore simply clone the repository and execute the Makefile with the command:
```sh
make install
```

## Limitations
- Glibc can cause problems on Linux: https://tauri.app/v1/guides/building/linux#limitations
- You need to use 64-bit systems, else the app might crash because it's using memory improvements that only work there

## Step-by-step guide
Please read the whole guide once before starting to execute each step!

### 1. Clone the repository
With `git` installed, do:
```sh
git clone https://github.com/Raspirus/Raspirus.git
```
Else, download the repository from [here](https://github.com/Raspirus/Raspirus/) and extract the `.zip` file. [The GitHub guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) might help you.


### 2. Install Rust
On **Linux** (Debian, Ubuntu):
```sh
curl https://sh.rustup.rs -sSf | sh -s -- --help
```
On **Windows**:
Download the executable from the [Rust website](https://www.rust-lang.org/tools/install) and install it.

### 3. Install NPM
On **LInux** (Debian, Ubuntu):
```sh
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```
On **Windows**:
Head over to the [NPM Website](https://docs.npmjs.com/cli/v7/configuring-npm/install) and download the executable to install it.

### 4. Install Next.js
Execute the command with npm:
```sh
npm install next@latest react@latest react-dom@latest eslint-config-next@latest
```


## Conclusion
This application is basically a website attached to some Rust code and packaged with the Tauri framework. It will therefore need a graphical overlay to start and display the website. This project is in constant development and therefore, if you find anything unusual, have some good ideas or find some errors, don't be afraid to open an issue on this repository and I will be happy to help you out.
