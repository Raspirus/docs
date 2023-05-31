---
comments: vero
---

# Sviluppatori

The Raspirus project employs two distinct programming languages and frameworks: one for the frontend and one for the backend. The frontend utilizes JavaScript with the Next.js framework, while the backend is built with Rust. Communication between these languages is facilitated by the Tauri framework, enabling seamless integration of Rust functions in the frontend.

## Technologies Used
- [NPM](https://www.npmjs.com): To achieve an aesthetically pleasing frontend, I explored native application development options initially. However, the customization capabilities fell short of my expectations. Consequently, I opted for a web-based frontend and selected Node.js over [Deno](https://deno.land/) due to my familiarity with Node.js.
- [Next.js](https://nextjs.org): Next.js, a frontend framework, proved to be easy to implement and incredibly powerful once set up. The project extensively leverages Next.js's capability to export the website as static HTML, which is crucial for the functioning of Tauri. Additionally, Next.js optimizes the application by automatically eliminating unnecessary components, resulting in a lightweight and fast application. Navigation with Next.js is nearly instantaneous.
- [Rust](https://www.rust-lang.org): While C++ was my initial choice for the backend, my proficiency wasn't sufficient to develop the entire application in that language. I turned to Python, my preferred language and one in which I am proficient, for faster development. However, Python's speed limitations became a significant drawback. Fortunately, a friend helped rewrite the entire backend in Rust, boosting the application's speed by 100x. Rust's compilation-based approach and performance superiority over interpreted languages like Python made it an ideal choice. If you are interested in the previous Python implementation, you can refer to the dedicated [repository](https://github.com/Raspirus/python-cli).
- [Tauri](https://tauri.app/v1/guides/getting-started/setup/next-js): Tauri plays a vital role in this project by bridging the Rust backend with the JavaScript frontend. This allows us to have an elegant frontend with Next.js and an impressively fast backend with Rust. Furthermore, Tauri simplifies the compilation of the application into installers or binaries for different systems like Windows, Linux, or macOS, greatly enhancing the installation experience.
- [SweetAlert2](https://sweetalert2.github.io): When presenting errors, warnings, or information to the user as pop-ups, the default JavaScript alert lacks visual appeal. SweetAlert2 significantly enhances the appearance of these pop-ups. It is easy to install and use. In our case, SweetAlert2 is mainly used for displaying errors or warnings, such as when the scanning process is abruptly interrupted.
- [next-i18next](https://github.com/i18next/next-i18next): Although the application contains minimal text and relies on icons and colors for clarity, we decided to incorporate translations. This is achieved using the Next.js plugin called i18next, which facilitates easy translation management through .JSON files.
- [Crowdin](https://crowdin.com/project/raspirus): Crowdin is a website that aids in translating open-source and private projects, and I am particularly grateful that it offers free pricing for open-source projects. Crowdin allows translators to focus solely on translations without the need to examine code. It also streamlines the translation synchronization process between Crowdin and GitHub.
- [MkDocs](https://www.mkdocs.org/): MkDocs, a Python framework, is utilized to generate project documentation. In fact, this very translation you are reading was created using MkDocs. It is user-friendly and facilitates document structuring and integration with plugins like

 Crowdin.
- [Dependabot](https://docs.github.com/en/code-security/dependabot/working-with-dependabot): Dependabot, a built-in feature in GitHub repositories, ensures that dependencies are up to date by automatically checking for updates. This helps maintain an up-to-date application with the latest patches and functionality. By improving dependencies, the application's performance and efficiency can be enhanced. Moreover, Dependabot notifies users of any security vulnerabilities in the utilized dependencies or crates, ensuring the application's security.
- [GitHub](https://github.com/): GitHub was selected as the file hosting platform due to its popularity, user-friendly interface, and comprehensive feature set. Additionally, it offers free hosting. Although a company suggested hosting the project on their GitLab servers, GitHub's ease of use and collaboration capabilities prevailed over the complexities of utilizing a VPN to connect to a PC that connects to GitLab. GitHub offers numerous features, including project planning, milestones, issues, and actions.
- [CodeQL](https://codeql.github.com/): CodeQL, another powerful tool from GitHub, scans the project for vulnerabilities in the code. It detects issues like cross-site scripting, improper handling of passwords and secrets, and inefficient coding practices. CodeQL ensures a higher level of code reliability.
- [CodeCov](https://about.codecov.io/): Codecov, an external tool installable on GitHub, tracks test coverage. It provides insights into the effectiveness of written tests and their coverage across the entire project. Although testing the frontend is challenging as it often involves user interaction, testing the backend is feasible. Therefore, we integrated Codecov to monitor test coverage in our Rust backend.

## Integration
Raspirus is a self-contained application, operating solely within its environment. There are no external APIs for retrieving information, nor is the application designed for integration with other apps. The primary user interaction occurs via a touchscreen interface, eliminating the need for text input fields, which can be frustrating on low-quality touchscreens like the one found on a Raspberry Pi.

Although API calls are made, they are internal to the application. For instance, in the `loading.js` file, we invoke the scanning function from the frontend to initiate the scanner in Rust:
```js
const message = await invoke("start_scanner", {
    path: scan_path,
    dbfile: db_location,
    obfuscated: obfuscatedMode,
});
```
The `start_scanner` function is called with the required parameters, and the resulting message is stored in the `message` constant. This basic Tauri API call enables seamless communication between the frontend and backend.

To send data from the backend to the frontend, Tauri employs the signal principle:
```rs
fn calculate_progress(&mut self, last_percentage: &mut f64, file_size: u64) {
    self.scanned_size += file_size;
    let scanned_percentage = (self.scanned_size as f64 / self.folder_size as f64 * 100.0).round();
    info!("Scanned: {}%", scanned_percentage);
    if scanned_percentage != *last_percentage {
        self.tauri_window.emit_all("progress", TauriEvent { message: scanned_percentage.to_string() }).unwrap();
        *last_percentage = scanned_percentage;
    }
}
```
For further details on how this internal API system operates, refer to the official [Tauri guide](https://tauri.app/v1/guides/features/command).