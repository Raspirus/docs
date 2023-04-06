---
comments: true
---

# Backend
The backend mainly has three components:
- A database that stores all signatures of known viruses and exports functions to search for them and insert new ones. This database can be updated manually with a dedicated function call, or automatically by setting a specific interval
- A logger that writes important information for bug hunting in a txt file
- The file scanner that retrieves all files from a specific folder and checks if its hash exists in the database.

All components have their own files in the backend directory and can be edited. Most of the documentation for this part is written in the code itself using comments. The full documentation can therefore be generated using the command ``cargo doc`

## The database
COMING SOON

## The Logger
COMING SOON

## The FileScanner
COMING SOON