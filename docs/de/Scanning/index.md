# Scannen

Scanning files for malware can be achieved through various methods, such as Yara Rules or sandboxing. Antivirus applications often scan the entire process tree of an executable to identify malware. However, Raspirus is designed differently. It is a lightweight, on-demand file scanner optimized for low-end devices like the Raspberry Pi.

Raspirus now leverages the power of the `yara-x` crate and Yara rules for its malware detection. Instead of relying on file signatures, Raspirus uses a flexible and powerful rule-based approach, scanning files for patterns and characteristics that match known malware behaviors. Yara rules are stored in a dedicated repository [here](https://github.com/Raspirus/yara-rules), and these rules are regularly updated to ensure broader and more accurate malware detection.

There are no restrictions on the type or size of files you can scan with Raspirus.

## Disadvantages

While the shift to Yara rules improves detection capabilities, there are still some limitations:

1. **Rule Complexity**: Writing and maintaining Yara rules can be complex. Although the rules provide more flexibility than simple hash matching, they require constant updating to cover new and evolving malware.

2. **False Positives**: Due to the pattern-based nature of Yara rules, there may still be cases where legitimate files are flagged as malware. However, the rules are designed to minimize these occurrences compared to a pure signature-based approach.

## Advantages

Raspirus, powered by Yara, offers several distinct advantages:

1. **Improved Detection**: Yara rules enable Raspirus to detect malware more accurately, even if the malware has been altered slightly or does not have a matching hash in a database. This allows for a more robust defense against various malware types.

2. **Efficiency**: Although Yara rules are more resource-intensive than signature matching, Raspirus remains optimized for low-resource devices like Raspberry Pi, providing fast and efficient scans without overwhelming system resources.

3. **Offline Capability**: Once the Yara rule database is downloaded and updated, Raspirus continues to function offline, maintaining the convenience of offline scanning.

Raspirus no longer uses pure signature matching due to its limitations in detecting modified or new malware. Instead, it provides a more comprehensive scanning solution while still remaining lightweight. However, like any security tool, it is not intended to replace a full-fledged antivirus application. Users should be cautious when scanning internal system files to minimize false positives.

Raspirus is continually evolving, and we are actively working to improve its scanning accuracy and expand its Yara rule database.
