
# macOS

{% include "../.gitbook/includes/if-you-dont-know-where-to-....md" %}

### 1. Download doukutsu-rs

* Go to the doukutsu-rs downloads page: [**https://get.doukutsu.rs**](https://get.doukutsu.rs)
* Choose either the **Apple Silicon (ARM64)** version or the **Intel (x86_64)** depending on [the type of your processor](https://support.apple.com/116943). All Macs made since 2024 have an Apple silicon processor.

As with most Mac programs, it is recommended that you store the application file (`dokutsu-rs.app`) in either the global or user `Applications` directory on your computer.

### 2. Add game data

* Right-click on the downloaded application (`dokutsu-rs.app`) and click `Show Package Contents`.
* Inside the application, navigate to `Contents/Resources/` and place the Cave Story game data directory in the folder. The data directory is a folder named "**data**" in the original game files. 

Note that due to the self-contained nature of Mac applications, this will have to be repeated if a newer version is downloaded.

### 3. Authorise application

Modern Mac computers [only permit software that has been signed and notarised to run by default](https://support.apple.com/en-nz/102445). As of this writing, dokutsu-rs is not notarised. To grant permission for it run:

* Open the application. A notice will be displayed that dokutsu-rs does not have permission to run.
* Open System Preferences and select Privacy and Security settings.
* Scroll down to the bottom and authorise dokutsu-rs by selecting `Open Anyway`. The application can now be opened normally in the future.

### Updating doukutsu-rs to a Newer Version

* Updating doukutsu-rs is very easy! When a new version is released, simply download the new `.app` program file from the [downloads page](https://get.doukutsu.rs) (just like you did in Step 1).
* **Important:** Make sure doukutsu-rs is completely closed before updating.
* Once downloaded, repeat Step 2 with the new application file you downloaded. The extant application can then be replaced if desired.
* **Your settings and save files are safe!** Updating only replaces the program itself. Your game settings and saved games are stored separately ([#where-are-the-saves-settings-logs](../faq.md#where-are-the-saves-settings-logs "mention")), so they will not be affected by updating the program file.

**Setup Complete!**

You are now ready to play doukutsu-rs. Run `doukutsu-rs.app` to start the game. Enjoy!
