---
comments: wahr
---

# Anleitungen
Here are some guides on how to export the docs to PDF format, or how to add translations to this project. If anything is missing, make sure to post a comment below and request a guide!

## Export to PDF
This documentation can be exported in PDF format for offline sharing. The exported PDF has some issues with Images and iFrames, but the text is readable and can be shared. Here step by step:
1. [Clone](https://github.com/Raspirus/docs) this repository, you can find instructions on how to it on [GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)
2. Install the requirements for the PDF conversion tool, you can find them for your OS [here](https://github.com/orzih/mkdocs-with-pdf#requirements)
3. Change to the cloned directory and install the required dependencies. Note: You will need Python3 and pip for this. You can install the dependencies with the command: `pip install -r requirements.txt`
4. Install [mkdocs](https://www.mkdocs.org/user-guide/installation/) and run the build command: `mkdocs build`
5. If everything works as expected, your PDF should be located in `site/pdf/document.pdf`

## Übersetzungen
- Translate this document: https://github.com/ultrabug/mkdocs-static-i18n