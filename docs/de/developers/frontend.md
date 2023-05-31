---
comments: wahr
---

# Frontend

The frontend of the Raspirus app was planned using an external website called Figma. Although there have been some changes in styling and additional functions, the logical structure remains largely the same. Each screen in the app corresponds to a single page in Next.js. Additionally, the pop-ups in the original design have been replaced with ones from SweetAlertv2. You can explore the Figma project in the embedded iFrame below. If the iFrame doesn't load, you can access the project [here](https://www.figma.com/file/pkgpwieNbhYiOi4Gz6Uyt6/Raspirus).

<iframe title="The original Raspirus project on Figma" style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FpkgpwieNbhYiOi4Gz6Uyt6%2FRaspirus%3Fnode-id%3D0%253A1%26t%3DGr4YG3Ynv24YVlz2-1" allowfullscreen></iframe>

## Screenshots

(Screenshots are missing in the provided content.)

## Pages

The entire project is structured into components and pages. The frontend of the app functions like a regular website, with routing and links between pages. There is a separate page for each important action in the app, such as scanning, settings, and information. All pages, except the scanning and home pages, have a button to return to the home page. In the case of this project, each page exists in duplicate due to an [issue with the translation plugin](https://github.com/Raspirus/Raspirus/issues/137). Therefore, the actual page resides inside the `[lang]` folder, while the pages outside of it are used for routing. It's important to note that there are special pages like `app.js` and `document.js` that have a specific structure. To learn more about these special pages, refer to the Next.js documentation on [basic features/pages](https://nextjs.org/docs/basic-features/pages).

## Components

Components are used to store repeated or cluttered code, helping keep the code of the pages clean and focused. Each component should have a single responsibility. For example, a component may display a single card on the settings page. Both components and pages are stored in separate directories at the root and can be imported. Components should be imported into pages, but not the other way around.

## Localization

The frontend of the app is also translated into different languages. The language files can be found in the `public` directory, with each language having its own folder containing a JSON file. The JSON files follow a key-value structure, where the keys need to be consistent across all language files, while the values are the translations. When translating, it's important to review the context and consider any potential changes. The app utilizes Next.js' [i18n](https://nextjs.org/docs/advanced-features/i18n-routing) feature for localization, which works well but can be complicated to set up with Tauri. If you want to add new languages, be sure to specify it in your pull request or issue, as some code adjustments may be necessary. For example, updating the language display on the main page requires manual changes and is not automated. Here's an example of how localization works on the frontend:

```js
Swal.fire(t("usb_list_error"), t("usb_list_error_msg"), "error");
```

In this case, a SweetAlert pop-up is displayed with a title and message. The important part is the `t(key)` function, which retrieves the translation associated with the given key from the JSON file.

## Invoking Rust

The frontend doesn't perform calculations itself, as that task is handled by the Rust backend. Rust is faster and has access to local files. To establish communication between the frontend and backend, Tauri is used. Tauri provides an API to call Rust functions and await results on the frontend, similar to a Promise. Here's an example:

```js
invoke("list_usb_drives", {})
  .then((output) => {
    setDictionary(JSON.parse(output));
    setTimeout(() => {
      refreshButton.classList.remove(styles.refreshStart);
    }, 3000);
  })
  .catch((error) => {
    console.error(error);
    refreshButton.classList.remove(styles.refreshStart);
    Swal.fire(t("usb_list_error"), t("usb_list_error_msg"), "error");
  });
```

In this code snippet, the `invoke()` function from Tauri is used to call a Rust function, and then the frontend waits for the result or handles any potential errors.