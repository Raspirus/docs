
# Home

## Welcome to Raspirus Docs

## Contents:
- [Introduction](#introduction)
- [Installation](installation.md)
- [Guides](guides.md)
- [FAQ](faq.md)
- [Usage and Diagrams](usage.md)
- [Developers Section](developers/index.md)
    - [Frontend (Next.js)](developers/frontend.md)
    - [Backend (Rust)](developers/backend.md)
- [Contributing](contributing/index.md)
    - [Coding](contributing/coding.md)
    - [Translations](contributing/translations.md)

## Introduction
This repository contains all documentation of the Raspirus project. It is currently in development and therefore not too reliable.

## Related projects
Raspirus is a simple virus scanner, and there are many similar projects out there. I will list a few of them I know and why I decided not to use them for my project, or why Raspirus is better.

- [Clam AV](https://www.clamav.net/): This program is an open-source Antivirus, but it can also be used like Raspirus to scan single files or folders. It surely is more accurate when it comes to search for viruses, but it is very resource intensive and a bit slow. Therefore, it is not suited for single-board computers like the Raspberry Pi, as it doesn't have enough RAM. Nonetheless, Clam AV is a great open-source tool.
- [Windows Defender](https://www.microsoft.com/en-us/windows/comprehensive-security): This program from Windows doesn't just scan files and folders on-demand, but scans the entire system continuously. This slows down the entire system. Furthermore, it is also Windows-only, while Raspirus is cross-platform.
- [Bitdefender](https://www.bitdefender.com/): This is another great Antivirus software, but it comes with a cost. I think that security should be a must, not something you need to pay for. But if you are willing to pay a bit, this piece of software really has it all, and as far as I know it is even cross-platform.

There surely are many others that I could compare here, but Raspirus is not aimed at beating other Antivirus software. Its aim is to do one thing, and do it as best as possible: Compare Hashes of a file with a list of signatures.

- This project is free and will always stay free. 
- It is open-source, so you can look at the code and judge for yourself if you trust the app or not.
- Community helps grow the project, and many smart minds surely can achieve a lot if they work together
- Cross-platform as a standard: Raspirus should work everywhere
- Lightweight and fast, usable even on your Potato PC