---
comments: vero
---

# Backend

## Planing
![Raspirus Activity Diagram](../../img/RaspActDark.png#only-dark) ![Raspirus Activity Diahram](../../img/RaspActLight.png#only-light) This diagram describes how the logical flow of the app work. The exact flow can change in the future, but this was the initial planing of the app. As you can see it is rather simple with just a couple if statements and a for-each loop. The backend is actually not that hard to understand, the complicated part is the more in-depth part of how to manage the database, scan files, create the hash and most importantly, comunicate the result to the frontend by emitting signals.

## Concepts
- SQLite
- Tauri Signals emiter
- Scanning with percentage
- Logging
- Portability