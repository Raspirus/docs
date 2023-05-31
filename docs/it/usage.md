---
comments: vero
---

# Utilizzo

## Tutorial
Using the Raspirus app is straightforward and user-friendly. Once you have installed the application, it requires only a few simple steps to perform a scan. The app is designed with a focus on usability for touchscreens and does not require any input devices or keyboards to operate. Here's a step-by-step guide:

1. Open the app from the main page.
2. Insert a USB drive and select it, or click the folder icon to choose a local folder for scanning.
3. Carefully review and accept the user agreement.
4. Allow the app to perform its scanning process.
5. The results will be displayed, and you can initiate a new scan if necessary.

## Case Study
Let's delve into some key metrics and specifications of the Raspirus app, evaluating its speed, reliability, and functionality. Additionally, we will outline the intended use of the application.

### Specifications
- App size: 5MB
- RAM usage: Approximately 50MB
- Works offline, requiring an internet connection only for database file updates

### Performance Metrics
The scanning speed of the app depends on three factors:
- The storage medium (USB or local) used for scanning.
- The CPU performance of the system running the app.
- The file size of individual files being scanned.

For optimal scanning speed, it is recommended to utilize modern storage media with high read speeds, employ a capable CPU that is not overwhelmed with other applications, and focus on scanning smaller files. Scanning 100 files of 10GB each will generally be faster than scanning a single 10GB file, as the hashing function performs more efficiently on smaller files. For Raspberry Pis, CPU speed is of greater importance than RAM capacity, as the app only requires a few megabytes of memory.

### Application Scope
Initially developed for Raspberry Pis with touchscreens, the Raspirus app offers easy setup and high security on Linux-based systems. Given that most viruses target Windows PCs, Linux-based Raspberry Pis are inherently less vulnerable. Additionally, by configuring a Raspberry Pi with a battery and enabling Kiosk mode, it is possible to create a portable Raspirus scanning box specifically tailored for scanning USB drives.

Thanks to Tauri's cross-compilation feature, the Raspirus app is now available for macOS, Windows, and Linux. While primarily developed and tested on Windows and Debian Linux, installation instructions for various operating systems can be found on the [Installation page](installation.md).