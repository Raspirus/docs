---
comments: wahr
---

# Anleitungen
## KOMMT BALD


## Notizen
### Export in PDF:
- Folgen Sie den Anweisungen für Ihr Betriebssystem hier: https://github.com/orzih/mkdocs-with-pdf#requirements
- Installieren Sie alle Abhängigkeiten mit Pip mit `pip install -r requirements.txt`
- `mkdocs build` ausführen
- PDF befindet sich in site/pdf/document.pdf

### Übersetzungen
- Link: https://github.com/ultrabug/mkdocs-static-i18n

### Raspberry Pi
Instructions:
- curl -sL https://deb.nodesource.com/setup_16.x | sudo bash -
- sudo apt install nodejs
- sudo chown -R pi .         # To change permission for folder and avoid needing sudo for cargo commands
- npm install next@latest react@latest react-dom@latest eslint-config-next@latest
- cargo install tauri-cli
- npm i

In the file: nano ~/.config/lxsession/LXDE-pi/autostart Add the line: @raspirus