---
comments: true
---

# Guides
## COMING SOON


## Notes
### Export to PDF:
- Follow instructions for your OS on here: https://github.com/orzih/mkdocs-with-pdf#requirements
- Install all dependencies using pip with `pip install -r requirements.txt`
- Run `mkdocs build`
- PDF is located in site/pdf/document.pdf

### Translations
- Link: https://github.com/ultrabug/mkdocs-static-i18n

### Raspberry Pi
Instructions:
- curl -sL https://deb.nodesource.com/setup_16.x | sudo bash -
- sudo apt install nodejs
- sudo chown -R pi .         # To change permission for folder and avoid needing sudo for cargo commands
- npm install next@latest react@latest react-dom@latest eslint-config-next@latest
- cargo install tauri-cli
- npm i

In the file: nano ~/.config/lxsession/LXDE-pi/autostart
Add the line: @raspirus