# Android

{% include "../.gitbook/includes/if-you-dont-know-where-to-....md" %}

### 1. Install doukutsu-rs

* Go to the doukutsu-rs downloads page: [**https://get.doukutsu.rs**](https://get.doukutsu.rs)
* Choose the installation file for Android.
* Tap on the downloaded file and install it. If you're asked to choose which app to open the file with, select Package Installer.
* If a warning appears stating that installation from unknown sources is not allowed, allow it and install the application.

### 2. Add Game Data

When you launch doukutsu-rs, you will be prompted to download data files, if they're missing. These files are the game data of the English translation by Aeon Genesis for the freeware (2004) edition of the game, which are downloaded from the [Cave Story Tribute Site](https://www.cavestory.org/download/cave-story.php). You can also install your own data files, e.g. game data from purchased editions of Cave Story+ for PC (2011) or Switch (2017). Do this by first copying the game data (the `data` folder) to your device, then copying these files to doukutsu-rs scoped storage. Here's how to do it.

If there's already a data folder in doukutsu-rs scoped storage, delete it or rename it. If you copy data files to an existing data folder, doukutsu-rs might use the old data files instead of the ones you copied.

{% hint style="info" %}
doukutsu-rs doesn't support almost all Cave Story mods, including Jenka's Nightmare.
{% endhint %}

{% hint style="warning" %}
The sequence of actions described above only works for the original Cave Story data files and the English translation by Aeon Genesis. For translations of the freeware game, this sequence won't work, as applying the translations requires a number of additional steps that are beyond the scope of this guide.
{% endhint %}

### Updating doukutsu-rs to a Newer Version <a href="#updating-doukutsu-rs-to-a-newer-version" id="updating-doukutsu-rs-to-a-newer-version"></a>

Currently, doukutsu-rs doesn't have a feature to check for updates, so you should check for new versions on [get.doukutsu.rs](https://get.doukutsu.rs). If a new version is available, repeat step 1.

{% include "../.gitbook/includes/ask-installation-usage-questions-on-gh-issues-or-the-discord-server.md" %}
