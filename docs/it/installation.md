---
comments: vero
---

# Installazione
Questa guida vi aiuterà a costruire il progetto sulla vostra macchina.

## Use an executable
The fastest and easiest way to install the app on your system is using one of the executables provided in the [Release page](https://github.com/Raspirus/Raspirus/releases/latest). Once downloaded, it will depend on your system on how to run it, but on Windows for example you can easily double-klick on the executable and follow the installation instructions from the wizard. And that's it, you are done.

## Use the Makefile (Debian based systems only)
The project also features a Makefile for easier installation, update and testing. You can therefore simply clone the repository and execute the Makefile with the command:
```sh
make install
```

## Limitazioni
- Glibc può causare problemi su Linux: https://tauri.app/v1/guides/building/linux#limitations
- You need to use 64-bit systems, else the app might crash because it's using memory improvements that only work there

## Step-by-step guide
Si prega di leggere l'intera guida una volta prima di iniziare ad eseguire ogni passaggio!

### 1. Clone the repository
With `git` installed, do:
```sh
git clone https://github.com/Raspirus/Raspirus.git
```
Else, download the repository from [here](https://github.com/Raspirus/Raspirus/) and extract the `.zip` file. [The GitHub guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) might help you.


### 2. Installa Rust
On **Linux** (Debian, Ubuntu):
```sh
curl https://sh.rustup.rs -sSf | sh -s -- --help
```
On **Windows**: Download the executable from the [Rust website](https://www.rust-lang.org/tools/install) and install it.

### 3. Install NPM
On **LInux** (Debian, Ubuntu):
```sh
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```
On **Windows**: Head over to the [NPM Website](https://docs.npmjs.com/cli/v7/configuring-npm/install) and download the executable to install it.

### 4. Installa Next.js
Execute the command with npm:
```sh
npm install next@latest react@latest react-dom@latest eslint-config-next@latest
```


## Conclusione
Questa applicazione è fondamentalmente un sito web collegato ad alcuni codici Rust e confezionato con il framework Tauri. Sarà quindi necessaria una sovrapposizione grafica per avviare e visualizzare il sito web. Questo progetto è in costante sviluppo e quindi, se si trova qualcosa di insolito, avere alcune buone idee o trovare alcuni errori, non abbiate paura di aprire un problema su questo repository e sarò felice di aiutarvi.
