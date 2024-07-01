# Usage

Using Raspirus is fairly simple. It has been designed to be used without a keyboard or mouse and completely with touchscreen. 
Generally speaking you shouldn't have any issues trying to ue Raspirus, as the UI is made very simple.
In this section we further explain the available settings andscanning functionality.


## Navigating Logs and Configurations

In the event of unexpected occurrences or sudden app crashes, examining logs and configurations can provide insights. Locate these files in the following folders, based on your operating system. The [ProjectDirs crate](https://docs.rs/directories-next/latest/directories_next/struct.ProjectDirs.html) stores them at the following location:

**Log file location:**

|Platform | Value                                                                      | Example                                                       |
| ------- | -------------------------------------------------------------------------- | ------------------------------------------------------------- |
| Linux   | `$XDG_DATA_HOME`/`_project_path_` or `$HOME`/.local/share/`_project_path_` | /home/alice/.local/share/barapp                               |
| macOS   | `$HOME`/Library/Application Support/`_project_path_`                       | /Users/Alice/Library/Application Support/com.Foo-Corp.Bar-App |
| Windows | `{FOLDERID_LocalAppData}`\\`_project_path_`\\data                          | C:\Users\Alice\AppData\Local\Foo Corp\Bar App\data            |
    

Ensure to include these files when reporting bugs, as they greatly assist in troubleshooting.