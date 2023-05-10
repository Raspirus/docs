---
comments: vero
---

# Codice
Code are always welcome and strongly needed. Make sure you read the [Guidelines](CODE_OF_CONDUCT.md) before opening your own pull-request. Another good idea is to read about the coding in the [Developer section](/developers/index.md)

## Contributing to the Frontend
The Frontend uses the basic Next.js structure and tries to put as much stuff in components as possible. The pages should look clean and not cluttered with unnecessary code. Each page represents a screen of the app and are accessed via manual routing. User either accesses a page by clicking a button or by getting redirected there after a loading process finishes. The frontend is entirely in Javascript and there are currently no plans to migrate to Typescript.

## Adding to the Backend
The backend is written in Rust for faster scanning speeds and reliability. It uses a big database to locally store the hashes and sends responses over the Tauri API. If you want to contribute here it might be useful to have a look at how Tauri and Rust work. It is not complicated and can be learned quickly with a bit of practice.