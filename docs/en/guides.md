# Guides

## Setting Up Your Local Documentation

Easily set up the documentation on your machine with these straightforward steps:

1. Clone the Repository:
   Start by cloning the repository to your local machine using this command:

   ```bash
   git clone https://github.com/Raspirus/docs.git
   ```

2. Install Python Dependencies:
   Navigate to the project directory and install the necessary Python dependencies from the `requirements.txt` file using this command:

   ```bash
   pip install -r requirements.txt
   ```

3. Launch the Project Locally:
   Begin your local project by executing this command:

   ```bash
   mkdocs serve
   ```

   This will initiate a development server, allowing you to access the documentation via [http://localhost:8000](http://localhost:8000) in your preferred web browser.

## Exporting Documentation to PDF

If you prefer an offline PDF version of this documentation, follow these step-by-step instructions:

1. Follow the setup process outlined above.

2. Build the Documentation:
   Employ [mkdocs](https://www.mkdocs.org/user-guide/installation/) and use the build command: `mkdocs build`.

3. Access the PDF:
   If the process goes smoothly, locate the resulting PDF file named `document.pdf` within the `site/pdf` directory.

Please note that the exported PDF may display minor issues with images and iFrames. Nevertheless, the text remains legible and suitable for offline sharing.

## Introducing Translations

For translations of this documentation, visit [Crowdin](https://crowdin.com/project/raspirus), a collaborative platform. Translations for UI strings are managed through JSON files. To contribute, craft your translations within the [locales folder](https://github.com/Raspirus/Raspirus/tree/main/public%2Flocales). Retain the uniqueness of keys when translating from the `en.json` file.

## Scanner Insights

### Scanning Compressed Files

While Raspirus defaults to scanning folders, you can alter this behavior via the settings page. By toggling a switch, you can scan individual files, including compressed ones. It's important to note that only one file can be scanned at a time.

### Navigating Logs and Configurations

In the event of unexpected occurrences or sudden app crashes, examining logs and configurations can provide insights. Locate these files in the following folders, based on your operating system:
{COMING SOON}

Ensure to include these files when reporting bugs, as they greatly assist in troubleshooting.

## GitHub Integration

### Enriching the Signature Database

Stay tuned for the upcoming release on this topic.

### Compiling for Multiple Platforms

Stay tuned for the upcoming release on this topic.

## Raspberry Pi Deployment

Originally tailored for standalone Raspberry Pi deployment with touchscreen functionality (akin to kiosk mode), this project's primary purpose was scanning attached USB drives. While the project's scope has expanded, this feature remains intact. Follow this guide for simple step-by-step instructions:
{COMING SOON}

Thank you for choosing Raspirus as your malware protection solution. These comprehensive guides will ensure your experience is seamless and efficient.