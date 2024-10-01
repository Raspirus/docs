# Raspberry Pi

## Requirements

- Raspirus requires a screen to function. You can use it without a mouse or keyboard, operating solely through a touchscreen.
- The screen should ideally be larger than 7 inches. The app is tested on a 10-inch screen, and we can't guarantee proper scaling on smaller screens.

### Packages

On Linux, ensure you have the same packages installed as those used to build the application. Not having the correct versions may result in errors such as: `raspirus : error while loading shared libraries : libssl.so.3 : cannot open shared object file : no such file or directory`.

Required packages:

- libwebkit2gtk-4.1-dev
- openssl 3

To check if a package is installed, use:

```sh
apt list [package]
```

## Installation

!!! danger
Do not install or perform actions as the sudo user. Always run commands as the main user and use `sudo` when necessary. Switching to the sudo user and performing the installation will break it.

### Remote Access

If you don't have direct access to the Raspberry Pi, you can install the application remotely using the CLI.

1. Connect to the Raspberry Pi via CLI. Follow a tutorial that suits your situation, such as the [official Raspberry Pi tutorial](https://www.raspberrypi.com/documentation/computers/remote-access.html).
2. Visit our [GitHub Release](https://github.com/Raspirus/Raspirus/releases/latest) page and copy the link to the `.deb` file for your architecture.
3. On the CLI of your Raspberry Pi, run:
   ```sh
   wget [URL copied above]
   ```
   This will download the Raspirus `.deb` file. Now, follow the Direct Access instructions to install the app.

### Direct Access

If you have direct access to the Raspberry Pi with a mouse and keyboard:

1. Download the `.deb` file from [our website](https://raspirus.deno.dev/downloads).
2. Install it using:
   ```sh
   apt install ./[path to raspirus file.deb]
   ```
   or
   ```sh
   dpkg -i ./[path to raspirus file.deb]
   ```
3. Alternatively, install Raspirus from the [Snap Store](https://snapcraft.io/raspirus). Ensure you select the correct architecture.

## Tips

- Check if a package is installed:
  ```sh
  apt list [package]
  ```
- Check the architecture:
  ```sh
  uname -m
  ```

## Known Issues

- When installing the app via remote access, an error might occur indicating the app is not detecting a screen. This happens because the system doesn't detect a screen when running the app from the CLI, even if one is connected.
- If you encounter dependency issues, try the AppImage. If issues persist, consider downgrading or upgrading your OS. Always report these issues to us on Discord or GitHub so we can analyze them further.
