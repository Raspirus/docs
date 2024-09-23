## Scanning

### Options
Raspirus allows you to scan the following:

- A folder and all its subfolders
- A single file, including compressed files
- A detachable drive, such as USB sticks

### Requirements
You need permissions to access and read the files you want to scan. Raspirus cannot scan password-secured compressed files or folders secured by your operating system. Additionally, avoid scanning the entire operating system or your entire computer with Raspirus. For comprehensive system scans, use a full-fledged antivirus instead.

### Scanning Procedure
Scanning involves inspecting the patterns of each file. In the case of compressed files, Raspirus extracts and scans the files within. Each pattern is checked against the database of rules, determining whether it matches known malware patterns. If a match is found, the file is flagged as malware; otherwise, it's deemed safe.

### After the Scan
If no malware is detected, you can proceed with your tasks. If malware is found, Raspirus displays a list of identified threats. You have the option to submit suspicious signatures to VirusTotal for further analysis.

Raspirus does not offer options to delete or quarantine files because our database may produce false positives. Always inspect files flagged by Raspirus and decide on their disposition based on your judgment.
