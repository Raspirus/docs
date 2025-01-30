# FAQ

Below are some frequently asked questions about Raspirus. Click on any question to expand the answer.

## General

??? question "Where does the Raspirus logo come from?"\
The Raspirus logo features a red monster named **Stuart**, designed to represent a virus-eating creature. The logo was generated using [DALL-E](https://openai.com/product/dall-e-2), with additional image editing and merging.

```
Stuart is a friendly monster—except when he's hungry for viruses. You can find additional media and assets in the [dedicated repository](https://github.com/Raspirus/media). Feel free to use these images for your own artwork and share them in the [discussion boards](https://github.com/orgs/Raspirus/discussions).  
```

??? question "Can I use Raspirus offline?"\
Yes! Raspirus works offline except for updates. The YARA rules database is built locally, and an internet connection is only needed when fetching the latest rules from our GitHub repository.

## Installation & Compatibility

??? question "What are the minimum system requirements?"\
Raspirus is lightweight and works on most systems, including low-power devices like the Raspberry Pi 3B+. However, for the best experience, we recommend:

```
- **RAM:** ~1 GB  
- **Storage:** ~200 MB  
- **CPU:** Dual-core processor (higher performance results in faster scans)  
- **Display:** Required for the GUI (no strict minimum size, but smaller screens may impact usability)  
```

??? question "Issue when installing Raspirus on Linux"\
**Do not install or perform actions as the `sudo` user.** Always run commands as your main user and use `sudo` only when necessary.

```
Switching to the `sudo` user and performing the installation will **break** the setup.  
```

??? question "Why can't I select directories or files?"\
To change the type of asset you want to scan, click the **orange icon** near the selection dropdown. You can choose between:

```
- **USB drives**  
- **Folders**  
- **Individual files**  
```

??? question "Which operating systems and architectures are supported?"\
Raspirus supports multiple operating systems and CPU architectures:

```
- **Windows:** Windows 10 & 11 (x86_64)  
- **Linux:** Debian-based distributions (Debian, Ubuntu, PopOS, Mint, etc.) (x86_64, ARM64)  
- **macOS:** Intel & Apple Silicon (x86_64, aarch64)  

Additionally, Raspirus is **unofficially supported** on:  

- OpenSUSE (x86_64, ARM64)  
- Arch-based Linux distributions (x86_64, ARM64)  

**Experimental support:** RISC-V 64 on Linux.  
```

## Customization

??? question "How do I add my own YARA rules?"\
Raspirus fetches rules from the [yara-rules repository](https://github.com/Raspirus/yara-rules) and builds the database locally.

```
If you want to contribute new rules:  
- Open an **issue** or submit a **pull request (PR)** on the [yara-rules repository](https://github.com/Raspirus/yara-rules).  

If you prefer to use your own rules:  
- Modify the configuration file to fetch rules from your own repository instead.  
```

---

## Known Issues

??? warning "Remote installation error: App not detecting a screen"\
If you install Raspirus via remote access, you may see an error indicating the app **is not detecting a screen**.

```
This happens because the system doesn't register a screen when running the app from the CLI, even if one is physically connected.  
```

??? warning "Dependency issues when installing Raspirus"\
If you encounter dependency issues:* Try using the **AppImage** version.
* If issues persist, consider **downgrading or upgrading your OS**.

```
Always report these issues on [Discord](https://discord.gg/raspirus) or [GitHub](https://github.com/Raspirus/raspirus/issues) so we can investigate further.  
```

---

## Important GitHub Issues to Check

Before reporting a problem, please check the following commonly referenced issues:

??? note "Commonly Reported Issues"* **[#852 - No armv7 (32-bit) support](https://github.com/Raspirus/raspirus/issues/852)**
* **[#891 - Missing fonts](https://github.com/Raspirus/raspirus/issues/891)**
* **[#902 - "Failed to open yar file" error](https://github.com/Raspirus/raspirus/issues/902)**
* **[#937 - ARM64 deb does not install on RaspiOS (Debian 12 Bookworm)](https://github.com/Raspirus/raspirus/issues/937)**

This is not a complete list—just a selection of frequently reported issues. If you encounter an error, check the [GitHub issues](https://github.com/Raspirus/raspirus/issues) first to see if a solution already exists before requesting support.

## Contributing Fixes

We are happy to assist when possible, but our time is limited. If you find a solution to a problem, consider sharing it:

- If an **existing issue** covers your problem, add a comment with your fix.
- If you discover a **new issue** and a workaround, open an issue and document the solution for others.

Your contributions help improve Raspirus for everyone! 🚀
