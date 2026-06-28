# Android

{% include "../.gitbook/includes/if-you-dont-know-where-to-....md" %}

### 1. Install doukutsu-rs

* Go to the doukutsu-rs downloads page: [**https://get.doukutsu.rs**](https://get.doukutsu.rs)
* Choose the installation file for Android.
* Tap on the downloaded file and install it. If you're asked to choose which app to open the file with, select Package Installer.
* If a warning appears stating that installation from unknown sources is not allowed, allow it and install the application.

### 2. Add Game Data

{% include "../.gitbook/includes/on-june-9-2026-an-update-....md" %}

When you launch doukutsu-rs, you will be prompted to download data files, if they're missing. These files are the game data of the English translation by Aeon Genesis for the freeware (2004) edition of the game, which are downloaded from the [Cave Story Tribute Site](https://www.cavestory.org/download/cave-story.php). You can also install your own data files, e.g. game data from purchased editions of Cave Story+ for PC (2011) or Switch (2017). Do this by first copying the game data (the `data` folder) to your device, then copying these files to doukutsu-rs scoped storage. Here's how to do it.

<details>

<summary>How to set up data files on Android</summary>

If your phone has an app called **"Files"**:

1. Launch this app.
2. Press **☰** on the top left corner.
3. Tap on **"doukutsu-rs"**.
4. Copy your game data files to the opened folder.

If there is no such application, then you can install [shortcut](https://play.google.com/store/apps/details?id=com.marc.files) for it and repeat with it the same actions described above.

***

If you don't want to install this shortcut, then:

1. Install the **"Material Files"** app from _Hai Zhang_ and launch it ([Google Play](https://play.google.com/store/apps/details?id=me.zhanghai.android.files) | [F-Droid](https://f-droid.org/en/packages/me.zhanghai.android.files/) | [Github Releases](https://github.com/zhanghai/MaterialFiles/releases)).
2. Press **☰** on the top left corner.
3. Press **"+ Add storage"**.
4. In the popped-up window, press **"External storage"**.
5. Press **☰** on the top left corner.
6. Tap on **"doukutsu-rs game data"**.
7. Press the large blue button at the bottom labelled **"USE THIS FOLDER"**.
8. Then click on **☰** in the top left corner again.
9. Tap on **"files"** above **"+ Add storage"**.
10. Copy your game data files to the opened folder.

</details>

If there's already a data folder in doukutsu-rs scoped storage, delete it or rename it. If you copy data files to an existing data folder, doukutsu-rs might use the old data files instead of the ones you copied.

{% hint style="info" %}
doukutsu-rs doesn't support almost all Cave Story mods, including Jenka's Nightmare.
{% endhint %}

{% hint style="warning" %}
The sequence of actions described above only works for the original Cave Story (and Cave Story+) data files and the English translation by Aeon Genesis. For translations of the freeware version, this sequence won't work, as applying the translations requires a number of additional steps that are beyond the scope of this guide.
{% endhint %}

### Updating doukutsu-rs to a Newer Version <a href="#updating-doukutsu-rs-to-a-newer-version" id="updating-doukutsu-rs-to-a-newer-version"></a>

Currently, doukutsu-rs doesn't have a feature to check for updates, so you should check for new versions on [get.doukutsu.rs](https://get.doukutsu.rs). If a new version is available, repeat step 1.

{% include "../.gitbook/includes/ask-installation-usage-questions-on-gh-issues-or-the-discord-server.md" %}
