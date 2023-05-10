---
comments: vero
---

# Utilizzo

## Tutorial
Using the app is really easy. Once you have it installed it is just as easy as pressing a couple of buttons. The entire app is built around the concept of being used on a bad touchscreen, so it needs no input or keyboard to work. **Step by step:**
1. Open the app on the main page
2. Insert an USB and select it, or click the folder icon to select a local folder to scan
3. Accept the user agreement after you have read it carefully
4. Wait for the app do to it's magic
5. Result is shown and you can now start a new scan if needed

## Case study
Here are some metrics of the app, how fast it is, how reliable and what it can actually do. It also describes how the app is intended to be used.

### Specification
- App size: 5MB
- RAM usage: ~ 50MB
- Works offline, only requires connection to Internet to update the database file

### Metrics
The speed in which the app is able to scan highly depends on three things:
- The USB or Storage medium used
- The CPU of the system the app runs on.
- The size of the single files that need to be scanned

For optimal scanning speed, you should use a modern storage medium with high read speeds, a modern CPU that is not overloaded with other apps and files that are low in size. It is faster to scan 100 files of 10GB than 1 file of 10GB. The reason being that the Hash funktion is faster on smaller files. For Raspberry Pis, don't look at RAM, as the app only requires a couple MB. Instead, look at CPU speed, as that's more important.

### Application
The app was originally intended to use only on Raspberry Pis with a touchscreen. The Raspberry Pi with Linux on it is easy to setup and very secure. Most of the viruses target Windows PC, and therefore have no effect on Linux. Furthermore, if you add a battery to your Raspberry Pi and set the app in Kiosk mode, you can create some sort of Raspirus box that can be carried around and is focused on scanning USB sticks. Thanks to Tauri and it's cross-compilation feature, Raspirus is available for all major systems: macOS, Windows, Linux. The app is primarly being developed and tested on Windows and Debian Linux. You can find installation instructions in the [Installation page](installation.md).