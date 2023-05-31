---
comments: vero
---

# Translators

Translations play a vital role in making the app accessible to users worldwide. If you are fluent in a language other than English and would like to contribute by providing translations, we welcome your assistance. There are two main areas where you can contribute: translating code and translating documentation.

## Translating Code

Translating the app's frontend strings is an essential task that allows users to interact with the app in their native language. There are two possible ways to handle translations within the codebase:

### Translation File

Each language has its own translation file in JSON format. The app loads the required strings from these files. While this approach is relatively simpler for developers to implement, it may not be the most efficient or user-friendly for translators, as it involves forking the repository and manually editing the JSON file.

### Translation Service

To streamline the translation process and provide a better experience for translators, we plan to integrate an external translation service. This service would enable translators to focus solely on translating the strings and provide an overview of the progress. We are considering using [Crowdin](https://crowdin.com/) as the preferred translation service. However, the setup for this option is still being worked on, and it will be added in the future as the team expands and we have more concrete plans.

## Translating Documentation

The documentation itself also requires translations to make it accessible to users who are more comfortable in languages other than English. Translating the documentation is a more significant undertaking compared to translating frontend strings. If you are eager to contribute translations to the documentation, follow these steps:

1. [Fork this repository](https://github.com/Raspirus/docs/fork): You can find a comprehensive guide on how to fork a repository [here](https://docs.github.com/en/get-started/quickstart/fork-a-repo).
2. Navigate to the `docs` folder in the forked repository. If the language you want to translate to doesn't exist yet, create a new directory with the name of the language you wish to translate into (e.g., `it` for Italian, `de` for German).
3. Enter the language directory and start editing the Markdown files while maintaining the original folder structure.
4. Once you have finished the translations, save your files and upload them to your forked repository. You can commit your changes following the [GitHub commit guide](https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project).
5. Finally, open a [pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) to the original repository, proposing your changes to be added to the main project.
6. A member of our team will review your translations and, if accepted, merge them into the main project.

We understand that this manual process might be cumbersome, but rest assured that in the future, we plan to integrate an external service like [Crowdin](https://crowdin.com/). This service will simplify the translation workflow, allowing you to focus solely on your translations without any distractions.

We appreciate your contribution to making the app accessible to a global audience through your translations. Thank you for your support!

