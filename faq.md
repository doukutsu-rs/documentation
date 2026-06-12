---
description: Comprehensive answers to common questions
---

# FAQ

## General

### What is this project?

The answer to this question is on the home page [of our website](https://doukutsu.rs):

> **A reimplementation of Cave Story engine with many quality-of-life improvements.**

Please note that doukutsu-rs **is not a decompilation**, as it's written from scratch and does not contain the source code of the original game (unlike CSE2[^1], which is actually a fan decompilation of a freeware executable).

**doukutsu-rs** was originally started as a Rust learning project and meme[^2], but after a while it evolved into a drop-in replacement for the major editions of the game (the original 2004 freeware edition, Cave Story+ for PC and Cave Story+ for Switch).

Starting with version 0.99.0-beta1, released on January 16, 2022, **the game is fully playable**. Work is currently underway to further improve the engine and fix some discrepancies with the original game.

While doukutsu-rs **tries to be faithful** in behavior to the original game, it **doesn't aim to be an exact copy** of it. For example, doukutsu-rs lacks bugs that exist in the vanilla version of the game, so there are some differences in behavior (e.g. [issue #278](https://github.com/doukutsu-rs/doukutsu-rs/issues/278#issuecomment-2403594236)), but also includes features such as cutscene skip, lighting effects, subpixel scrolling and V-Sync support.

Also some features are not planned to be implemented such as Steam achievements, leaderboard, coop off-screen or floor particles in Sand Zone.

### Where are the saves/settings/logs?

You can open the folder with saves and settings via the menu: `Options` -> `Advanced` -> `Open user data directory`.

If you created a portable user data directory, the saves will be in the `user` folder next to the doukutsu-rs executable.

Otherwise, the location of the user data depends on the platform:

* on **Windows**: `%LOCALAPPDATA%\doukutsu-rs\data\` (that is `AppData\Local\doukutsu-rs\data\`)
* on **macOS**: `~/Library/Application Support/doukutsu-rs/saves`
* on **Linux**:
  * if installed from **FlatHub**: `$XDG_DATA_HOME/doukutsu-rs/` (usually this is `$HOME/.var/app/io.github.doukutsu_rs.doukutsu-rs/data/doukutsu-rs/data`)
  * if you downloaded **the `.elf` executable file**: `$HOME/.local/share/doukutsu-rs/`
* on **Android**: see [#how-to-open-game-user-data-directory-on-android](faq.md#how-to-open-game-user-data-directory-on-android "mention")

The logs are stored in the `logs` folder next to the user data directory.

### How to open game/user data directory on Android?

If you have an app on your device called `Files` (app id `com.google.android.documentsui`), open it, swipe from the left edge to the right (or press the `≡` menu icon) and select `doukutsu-rs` from the list. Saves will be in the `saves` folder, game data in the `data` folder, logs in the `logs` folder.

If there is no such application, then you can install [shortcut](https://play.google.com/store/apps/details?id=com.marc.files) for it and repeat with it the same actions described in the previous paragraph.

If you don't want to install this shortcut, then install Material Files ([Google Play](https://play.google.com/store/apps/details?id=me.zhanghai.android.files)|[F-Droid](https://f-droid.org/en/packages/me.zhanghai.android.files/)|[Github Releases](https://github.com/zhanghai/MaterialFiles/releases)) by Hai Zhang. Once you open it, click on the menu icon `≡` -> `Add storage` -> `External storage` -> `≡` -> `doukutsu-rs` -> `USE THIS FOLDER` -> `ALLOW`. The `files` folder will appear in the menu, clicking on it will take you to the doukutsu-rs internal storage directory.

## Features Support

### Are the mods supported?

Shortly, doukutsu-rs doesn't support almost all Cave Story mods, including Jenka's Nightmare.

Only mods that modify game data files (textures, maps, text scripts, music, sounds) and don't modify the original game executable are supported. Cave Story+ mods and challenges are also supported, but there are [graphics issues](https://github.com/doukutsu-rs/doukutsu-rs/issues/118) for some mods.

### Is multiplayer supported?

Local co-op is available on PC, and starting with version 1.0.0, it's also available on Android.

Remote co-op (netplay) is not supported, and there are no plans to work on it in the near future.

### Are saves from CS+ supported?

> I copied the CS+ save file, but only the first slot is loaded/saved.

doukutsu-rs uses a freeware compatible save format, so each slot is stored in a separate file. Cave Story+ saves are stored in a single file, so doukutsu-rs only reads the first slot from this file, and writes only the first slot to it.

However, work on adding support for CS+ (PC, 2011) and CS+ Switch saves has already [started](https://github.com/doukutsu-rs/doukutsu-rs/pull/317).

### Is a fixed window ratio (e.g. 4:3 as in the freeware) or resolution supported?

This feature is already present in one of the development branches, and it's expected to be added to the nightly and stable builds in one of the future releases.

Also this feature is implemented in the [DrGlaucous's fork](https://github.com/DrGlaucous/doukutsu-rs-nm). However, it doesn't have prebuilts, so you'll have to build it from the source code. See [initial-setup-and-compiling](modders-handbook/initial-setup-and-compiling/ "mention") (don't forget to add the `--release` argument to `cargo build`).

## Platform Support

### Is controller supported on Android?

Support for controllers on Android was added in version 1.0.0.

### Which platforms is doukutsu-rs available on?

doukutsu-rs is officially supported on PC ([Windows 10+](#user-content-fn-3)[^3], Linux, macOS 10.12+) and Android 7+. Builds for these platforms are stable: release builds as well as nightly builds are available for them.

In addition, doukutsu-rs also has an experimental port for Nintendo Switch. Experimental ports may be unstable and lack certain features.

### You should make a port to the XYZ platform.

doukutsu-rs is available on the most common platforms, so **there are no plans** to port to other platforms yet.

Although there are a number of unfinished experimental ports, specifically for iOS and UWP (Xbox), work on them is currently on hold.

### The controls on Android are awkward, how do I customize them? How to make the buttons bigger or change their position?

No way. You cannot change the location of touch screen controls and their size. You can only disable their display in `Options` -> `Controls` -> `Display touch controls` -> `OFF`.

***

Although you can try changing the size and position of the buttons in the source code and rebuild the executable file, but this is very inconvenient and will take some time to find the right values.

If you're ready for it, in the file [src/input/touch\_controls.rs](https://github.com/doukutsu-rs/doukutsu-rs/blob/2f1159c14f671bb77e845d46b48de9fcfb5eb814/src/input/touch_controls.rs#L100-L146) on line 100-146 you can adjust the location of controls (the first argument of the `add_rect_tinted` function is an X-axis coordinate, and the second argument is a Y-axis coordinate), and in the file [src/input/touch\_player\_controller.rs](https://github.com/doukutsu-rs/doukutsu-rs/blob/2f1159c14f671bb77e845d46b48de9fcfb5eb814/src/input/touch_player_controller.rs#L81-L239) on line 81-239 you can adjust the zones for registering button presses (the zones in which the game will count pressing a particular button).

## Troubleshooting

### Japanese language applies only to the menus/interface, while the game itself (dialogues) remains in English.

This happens because the data files you installed were most likely taken from the English translation of the game. You can fix this by installing the Japanese data files from the original game.

You can do this in two ways.

#### 1. Replace English data files with the Japanese ones

If you don't need the English translation, delete the old `data` folder and replace it with the `data` folder from the archive containing the original Japanese version of the game. Place the `Doukutsu.exe` file from the archive next to the `doukutsu-rs` executable, as the engine will extract a number of additional files from it during the first launch.

{% hint style="info" icon="box-open" %}
If you installed doukutsu-rs from FlatHub and therefore cannot place the `Doukutsu.exe` file next to the `doukutsu-rs` executable, use the `vanilla-extractor` utility, which is included with the application starting from version 1.0.0 (or download it from [its repository](https://github.com/doukutsu-rs/vanilla-extractor/releases/latest)). It works the same way: place its executable file next to the `Doukutsu.exe` file and the `data` folder, run it, and the necessary files will be extracted to the folder. If needed, set the path to the `data` folder in the `VANILLA_OUT_DIR` environment variable.

Example of use:

```shellscript
cd "path to the dir where Doukutsu.exe is located"
VANILLA_OUT_DIR="path to the data dir" vanilla-extractor.elf
```
{% endhint %}

However, in the settings, Japanese will be displayed as a language with missing data files, even though this is not the case. This is due to how the engine handles translations: by default, it considers that the files in the `data` folder are in English. Since you replaced the English translation data files with Japanese ones, it considers the Japanese data files are missing.

#### 2. Add Japanese data files as alternative

If you want to keep the English translation, repeat the steps described in the first option, but instead of deleting the `data` folder containing the English translation, rename it (the new name doesn't matter). Then run doukutsu-rs so that the application can extract the necessary files. After that, rename the `data` folder containing the Japanese game files to `jp`. Rename the folder with the English translation data back to `data`, and place the `jp` folder inside it. After that, when you change the language in the settings, the in-game dialogs should be in the language you selected.

***

There will probably be an easier way to do this in the future, but for now, this is how it's done.

## Game Info

### What are the differences between the difficulty levels?

* Easy - damage dealt by enemies is halved.
* Hard - no life capsules and missile launcher.

Also on difficutly level other than Normal, Quote (the player) will have a corresponding skin if CS+ data files are used.

### How to activate seasonal textures?

They're used automatically if `Graphics -> Seasonal textures` option is enabled and the appropriate date has arrived.

* Christmas textures are active from December 24 through January 6.
* Halloween textures are active from October 26 through November 2.

### How to change the character's skin?

You **cannot** select a skin for Player 1.

When CS+ game data is used, Player 1's skin changes auomatically during seasonal events (see [#how-to-activate-seasonal-textures](faq.md#how-to-activate-seasonal-textures "mention")) and when playing on a difficulty level other than Normal. These data files also allow you to select a skin for Player 2.

***

## Still have questions?

&#x20;Feel free to ask them on the project's [Discord server](https://discord.gg/fbRsNNB) or [GitHub issues](https://github.com/doukutsu-rs/doukutsu-rs/issues/new/choose).

[^1]: Cave Story Engine 2

[^2]: RiiR — Rewrite it in Rust.

[^3]: Although doukutsu-rs can be built for Windows 7, there are no release builds targeting this platform.
