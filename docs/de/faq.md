# FAQ

??? question "App crashes when updating"
On Windows, it has been observed that the app crashes when attempting to update the database. We are aware of this issue and actively working to resolve it. The problem arises because the update function requires administrative privileges, which Windows does not automatically provide. To temporarily resolve this issue, you can execute the app with administrative privileges. Right-click on the app and select "Run as administrator" to launch it with the necessary privileges.

??? question "Where does the Raspirus logo come from?"
The logo of the Raspirus app features a red monster named Stuart, who is designed to represent a virus-eating creature. The logo was generated using [DALL-E](https://openai.com/product/dall-e-2), along with creative image editing and merging. Stuart is a friendly monster, except when he's hungry for viruses. You can find additional media and documents in the [dedicated repository](https://github.com/Raspirus/media). Feel free to use these images to create your own artwork and share them in the [discussion boards](https://github.com/orgs/Raspirus/discussions).

??? question "Can I use Raspirus offline?"
Yes, except for the update, everything on Raspirus works offline. The database is built locally, you only need to be connected to the internet during the database update, as we fetch the signatures from our GitHub repository.

??? question "What are the minimum requirements for the app to work?"
Raspirus is built to work and almost any system. It even works well on a RPi 3B+. Nonetheless, we recommend having:

```
- 1 GB of RAM
- minimum of 10 GB of space (probably less)
- Dual core CPU (The better, the faster Raspirus will be)
- A display for the GUI
```

??? question "Can't select directories/files"
You can change what type of asset you want the scan by clicking the orange icon near the selection dropdown and select what you would like to scan. The options are: USBs, Folder or File.

??? question "How do I add my own yara rules to the main repository?"
Raspirus fetches rules from the [yara-rules repository](https://github.com/Raspirus/yara-rules) and creates the database locally. You can add rules to the repository by creating an issue or PR request on that repository.
