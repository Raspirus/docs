---
comments: true
---

# Guides

Here you will find helpful guides on how to export the documentation to PDF format and how to contribute translations to this project. If you have any additional requests for guides, please leave a comment below!

## Export to PDF
If you would like to have an offline version of this documentation in PDF format, you can follow these step-by-step instructions:

1. Clone this repository by following the instructions on [GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository).
2. Install the necessary requirements for the PDF conversion tool. You can find the requirements specific to your operating system [here](https://github.com/orzih/mkdocs-with-pdf#requirements).
3. Navigate to the cloned directory and install the required dependencies. Please note that you will need Python3 and pip for this step. You can install the dependencies by running the following command: `pip install -r requirements.txt`.
4. Install [mkdocs](https://www.mkdocs.org/user-guide/installation/) and execute the build command: `mkdocs build`.
5. If everything goes smoothly, the resulting PDF file should be located in the `site/pdf` directory with the name `document.pdf`.

Please be aware that the exported PDF may have some issues with images and iFrames, but the text should be readable and suitable for sharing offline.

## Translations
We welcome contributions to translate this documentation into other languages. If you are interested in translating the document, you can find the necessary information and resources at the following link: [Translate this document](https://github.com/ultrabug/mkdocs-static-i18n).

Your contributions are highly appreciated, and they will help make this documentation more accessible to a wider audience.