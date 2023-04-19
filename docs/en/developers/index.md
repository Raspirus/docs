---
comments: true
---

# Developers

The Raspirus project mainly uses two different programming languages and frameworks. One for the backend and one for the backend and one for the frontend. \
The frontend is written in JavaScript using the [Next.JS](https://nextjs.org/) framework. The backend on the other side is written in Rust. The communication between these two programming languages is made using the [Tauri](https://tauri.app/) framework. Using this framework one can write functions in Rust and call them from the frontend easily.

## Technologies used
- [NPM](https://www.npmjs.com):
    I wanted the frontend to be beautiful, and at first I tried creating an actual native application, but that just didn't have the customisation I was searching for. Therefore I decided to write a Web-frontend, and for that I could choose between Node.js or [Deno](https://deno.land/). I ended up using Node.js as it's the one I am mostly familiar with.
- [Next.js](https://nextjs.org):
    Next.js is a frontend framework that is fairly easy to implement, and once setup can be very powerful. The most useful feature used in this project is the export of the website in static HTML. This is essential for Tauri to function. Another advantage of Next.js is that it optimizes itself, by automatically stripping away everything unnecessary, this makes the app lightweight and fast. Navigation with Next.js is practically instant.
- [Rust](https://www.rust-lang.org):
    Rust was not my first choice for the backend. At first I started with C++, but I was not skilled enough to create the entire app with that language, so I turned to Python. Python is way slower than C++, but it's my favorite language and the one I know best, so I was able to develop faster. Nonetheless, the lack of speed with Python was a big drawback. Luckily a friend of mine helped me out an rewrote the entire backend in Rust, basically speeding the app up by 100x. What previously took a couple of minutes, now took mere seconds. Rust is compiled language and faster than Python, which is an interpreted language. If you want to test the old Python system, there is an entire [repository](https://github.com/Raspirus/python-cli) for that.
- [Tauri](https://tauri.app/v1/guides/getting-started/setup/next-js):
    Tauri plays a very important part in this project, as it is a framework that allows connecting the Rust backend to a JavaScript frontend. This essentially allowed us to have a beautiful frontend in Next.js and a impressively fast backend in Rust. Furthermore, Tauri compiles the application for different systems, like Windows, Linux or MacOS by creating installers or binaries. THis improved the installation of the app.
- [SweetAlertv2](https://sweetalert2.github.io):
    When errors occur, or there are warnings and information to display as a pop-up to the user, the simple JavaScript alert just doesn't look that good. SweetAlert improves the look of these pop-ups by a lot. It's fairly easy to install and to use. In our case it is mainly used to display errors or warnings, for example when the scanning process is suddenly interrupted.
- [next-i18next](https://github.com/i18next/next-i18next):
    The app doesn't have much text, and with the icons and colors it should be fairly simple to understand what you need to do. Nonetheless, we decided to add translations to the app. This is done using a Next.js plugin named i18next, that allows to translate the project easily with .json files.
- [Crowdin](https://crowdin.com/project/raspirus):
    Crowdin is a website that collects translations from users and helps translate open-source and private projects. I am especially grateful that for open-source projects the price for this service is free. It is useful for translators to focus on translations, without the need to look at code. It also helps developers, as it automatically syncs new translations with GitHUb and viceversa.
- [MkDocs](https://www.mkdocs.org/):
    MkDocs is a Python framework used to create documentation for projects. In fact it is the framework used to create this specific translation. It is really easy to use and makes structurizing docs or integrating plugins like Crowdin fairly easily.
- [Dependabot](https://docs.github.com/en/code-security/dependabot/working-with-dependabot):
    Dependabot comes with every GitHub repository, and can be activated fairly easily. Its job is to check dependencies for updates and therefore to keep the entire app up-to-date. This also ensures that the app has the latest patches and functions. By improving its dependencies, the app might become faster and more efficient. Furthermore Dependabot also informs the user about Security vulnerabilities of used dependencies or crates, a very useful feature to maintain the app secure.
- [Github](https://github.com/):
    GitHub has been chosen as the file hosting platform mainly because it is popular, easy to use and has ec´verything needed. Plus it's free. A company also suggested hosting the project on their GitLab servers, but in the end the project remained on GitHUb as it is easier to use and to collaborate than to use a VPN to connect to a PC that then connects to GitLab. GitHUb also has a lot of features: Project planing, Milestones, Issues, Actions, ...
- [CodeQL](https://codeql.github.com/):
    CodeQL is another powerful tool from GitHub. It scans the entire project and checks for vulnerabilities in the code. For example if there is cross-site-scripting happening somewhere, or we are not hiding passwords and secrets correctly, or we are coding inefficiently. This is very useful, as it assures a certain reliability of the code.
- [CodeCov](https://about.codecov.io/):
    Codecov is an external tool that can be installed on GitHub and it tracks test coverage. It basically tells you how efficient the tests you just wrote actually are and if they cover the entire project. Testing the frontend is hard, as we would likely need to test user interaction, but testing the backend is duable. Therefore we setup Codecov to check our Rust backend for test coverage.


## Integration
Technical infos (APIs), description, important classes and code
