---
comments: wahr
---

# Frontend

## Planing

The planing of the Raspirus frontend happened on an external Website called Figma. The styling changed a bit and there are some more functions now, but the logical structure is roughly the same. Each screen you see is a single page on Next.js. Furthermore, the pop-ups have been replaced with ones from SweetAlertv2. You can explore the Figma project in the iFrame below, else if nothing is showing up, you can look at the project [here](https://www.figma.com/file/pkgpwieNbhYiOi4Gz6Uyt6/Raspirus).

<iframe title="The original Raspirus project on Figma" style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FpkgpwieNbhYiOi4Gz6Uyt6%2FRaspirus%3Fnode-id%3D0%253A1%26t%3DGr4YG3Ynv24YVlz2-1" allowfullscreen></iframe>

## Screenshots

## Pages

The entire project is structurized in components and pages. The frontend is basically a normal website, so it has routing, links and so on. We have one page for each important action of the app. There is one for the scanning process, for the settings, for the informations, ... Pages link to each other and apart from the scanning and home page, they all have a button to return to the home-page. In our case we have all pages double, this has to do with an [issue in the translation plugin](https://github.com/Raspirus/Raspirus/issues/137). So now the actualy page resides inside the [lang] folder and the pages outside of it are simply used for routing. Note that there are some special pages, like the app.js and the document.js page that have a special structure. To learn more about them, visit the Next.js page [about this topic](https://nextjs.org/docs/basic-features/pages)

## Components

Components are used to store repeated or cluttered code. This helps in keeping the code of the pages clean and move the focus of certain code outside of them. Each component should only fulfill a single task. For example it should display a single card in the settings page. Both components and pages are stored in different directories at root and can be imported. Only import components into pages, not the other way around.

## Localizing

The frontend is also translated into different languages. The languages can be found in the public directory, where each langauge has its own folder with a json file. The JSON files are built on a key-value basis. The keys always need to be the same on all JSON files and the value gets translated. Make sure to look at the app before blindly translating, as some things might change depending of the context. For the translations, we used the Nextjs feature [i18n](https://nextjs.org/docs/advanced-features/i18n-routing), which works fine but is a bit complicated to setup with Tauri. If you want to add new languages, make sure to specify it in your pull-request or in the issue, as we also need tu update some of the code to cover the changes. For example we need to update the button on the main page to display the new language, this is not automatic. Here is how localizing looks like on the frontend:

```js
Swal.fire(t("usb_list_error"), t("usb_list_error_msg"), "error");
```

In this case we are calling a SweetAlert with a title and a message. The important part is the `t(key)` function. The function will return the text associated with the given string key, if it is able to find it in the JSOn file.

## Invoke Rust

The frontend doesn't do any calculations, because that's what we have the Rust backend for. Rust is much faster, and also has the ability to actually access local files. But to let the frontend and the backend communicate with each other we need Tauri. Tauri offers us an API to call functions from Rust and wait for a result on the frontend. It basically works like a Promise. Here an example:

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

As you can see, we use a Tauri function called `invoke()` that calls a Rust function and then awaits for it result or catches a possible error.
