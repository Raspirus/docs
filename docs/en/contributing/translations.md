---
comments: true
---

# Translations
Translations are very important and can help other people understand the app easier and make it wider available. If you know a language outside of English and would like to add your translations you can do so in two ways: The first one is to translate the documentation, the second one is to translate the frontend strings.


## Translating code
This is a work in progress, but essentially it will be done in one of two possible ways:

### Translation file
There is a translations file in JSON format for each different language. So the app would load the strings it needs from that file. This is a bit easier to implement for the developers, but not very efficient or great for translators, as it involves forking the repository.

### Translation service
We use an external translations service to translate the project. This option would allow translators to just translate the given strings and have an overview of how much has been translated and what still needs to be translated. This would be the preferred option, but the downside is the setup for this option. Since we don't know which service to use yet, this option will be added in the future when we have more concrete ideas and hopefully a bigger team. We will probably use [Crowdin](https://crowdin.com/)

## Translating Docs
The document you are reading right now is the project documentation. To add translations to this project, the best way is to add translations using [Crowdin](https://crowdin.com/project/raspirus). An alternative is using the instructions below:

1. [Fork this repository](https://github.com/Raspirus/docs/fork): You can follow a [guide](https://docs.github.com/en/get-started/quickstart/fork-a-repo) online on how to do it properly.
2. Enter the `docs` folder and, if the language you want to translate doesn't exist yet, add a new directory whose name is the name of the language you want to write translations for. For example, it would be `it` for italian, `de` for german and so on.
3. Then change to that directory and edit the Markdown files inside that directory. Make sure you keep the original folder structure.
4. After you have finished editing, save your files and upload them to your fork on GitHub. Basically make a [GitHub commit](https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project)
5. Now you can open a [pull-request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) to the original repository and request that your changes get added to the main project.
6. Someone of the team will review the translations and if accepted add them to the main project.