---
comments: vero
---

# Guide
## COMANDO SUONO


## Note
### Esporta in PDF:
- Segui le istruzioni per il tuo sistema operativo qui: https://github.com/orzih/mkdocs-with-pdf#requirements
- Installa tutte le dipendenze usando pip con `pip install -r requirements.txt`
- Esegue `mkdocs build`
- PDF si trova in sito/pdf/document.pdf

### Traduzioni
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