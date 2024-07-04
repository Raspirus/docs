# Scannen

Scanning files for malware can be achieved through various methods, such as Yara Rules or sandboxing. Antivirus applications often scan the entire process tree of an executable to identify malware. However, Raspirus is designed differently. It is a lightweight, on-demand file scanner optimized for low-end devices like the Raspberry Pi.

Raspirus leverages a streamlined approach by comparing file signatures against a comprehensive database of known malware. This database, hosted on GitHub [here](https://github.com/Raspirus/signatures), contains MD5 signatures of malware samples collected from various sources. When Raspirus scans a file, it generates the file's signature and compares it to the entries in the database.

There are no restrictions on the type or size of files you can scan with Raspirus.

## Disadvantages

The Raspirus scanning method comes with some limitations:

1. **Accuracy and Currency**: The system is not highly accurate and may become outdated quickly. It detects malware only if the file's hash matches an entry in the database. Any alteration in the file, even a minor change, will result in a different hash, and the malware might go undetected.

2. **False Positives**: Due to the extensive list of signatures and the lack of precise mechanisms to distinguish between true and false positives, legitimate files may often be flagged as malware.

## Advantages

Despite its drawbacks, Raspirus offers several benefits:

1. **Speed and Efficiency**: The scanning process is fast and reliable, making it ideal for low-resource environments.
2. **Offline Capability**: Raspirus operates offline after the initial download and subsequent updates of the database, eliminating the need for constant internet access.

Raspirus does not use Yara or sandboxing techniques due to their high resource demands. While Raspirus provides a quick and superficial scanning solution, it requires regular updates and careful monitoring. It is not intended to replace a full-fledged antivirus application. Users should avoid scanning internal operating system files with Raspirus to minimize false positives.

Remember, Raspirus is a work in progress, and we are continually striving to enhance its scanning accuracy.
