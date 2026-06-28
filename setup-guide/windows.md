# Windows

{% include "../.gitbook/includes/if-you-dont-know-where-to-....md" %}

Setting up doukutsu-rs on your Windows PC is straightforward - just follow those steps.

### 1. Download doukutsu-rs

* Go to the doukutsu-rs downloads page: [**https://get.doukutsu.rs**](https://get.doukutsu.rs)
* Choose the **64-bit** version in most cases. This is the standard version for most modern Windows computers. Click the download link for the 64-bit option to begin downloading.
* If you encounter an error message from Windows saying "This app can't run on your PC" when trying to launch the 64-bit version, your computer likely uses a **32-bit** processor. Return to the download page and download the **32-bit** version instead.

### 2. Create a Folder for doukutsu-rs

* Create a new folder on your computer to store all the doukutsu-rs files. This keeps things organized.
* You can create this folder anywhere convenient, such as your Desktop or Documents folder. Name it something recognizable, like "doukutsu-rs" or "doukutsu-rs folder".

### 3. Place doukutsu-rs in the Folder

* Locate the downloaded doukutsu-rs program file (e.g., `doukutsu-rs.{version}.exe`). This is the file you downloaded in Step 1. The `{version}` part of the program file name indicates the specific build you downloaded.
  * For example, a typical program file name might look like: `doukutsu-rs_windows_0.101.0-beta6.x86_64.exe`.
  * In this example:
    * `windows` indicates it's for Windows.
    * `0.101.0-beta6` is the version number (and potentially release stage like "beta").
    * `x86_64` indicates it's for 64-bit computers (if you downloaded the 32-bit version, it would likely say `x86` or `i686` instead).
* The important thing is to move this entire `.exe` file into the folder you created in the previous step. You can do this by dragging and dropping the file.

### 4. Add Game Data

{% include "../.gitbook/includes/on-june-9-2026-an-update-....md" %}

* You will need to add the Cave Story game data files to the same folder. These files are contained within a folder named "**data**". If you have played Cave Story previously, you should already have this folder.
* **For Freeware Cave Story Users:** If you are using the original freeware version of Cave Story, also place the original game executable, "**Doukutsu.exe**", into the doukutsu-rs folder alongside the "data" folder and the `doukutsu-rs.{version}.exe` file.
* This file in original **freeware** version stores some necessary data files, such as credits sequence sprites, background music and map list - it must be present at least during first run - it can be deleted after first successful launch. This is not applicable to **Cave Story+**, as all required data is present in the **"data"** folder.
* Move your "**data**" folder (and "**Doukutsu.exe**" if applicable) into the "doukutsu-rs folder".

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption><p>You should end up with directory structure similar to this.</p></figcaption></figure>

### 5. (Optional) Create a "user" Folder for Self-Contained Settings and Saves

* This step is optional, but recommended if you prefer to keep all doukutsu-rs files together in one folder.
* If you **don't** create a "user" folder, doukutsu-rs will automatically store your settings and save files in a standard Windows location: `%LOCALAPPDATA%/doukutsu-rs`. This location is usually hidden.
* To keep everything self-contained within your doukutsu-rs folder, create a new folder inside it named **exactly** `user` (all lowercase).

#### You can always change this later:

* Even if you skip creating the "user" folder now, you can switch to using a portable "user" folder at any time from within the game. Go to **Options -> Advanced... -> Make portable user directory**.

### Updating doukutsu-rs to a Newer Version

* Updating doukutsu-rs is very easy! When a new version is released, simply download the new `.exe` program file from the [downloads page](https://get.doukutsu.rs) (just like you did in Step 1).
* **Important:** Make sure doukutsu-rs is completely closed before updating.
* Once downloaded, drag the new `.exe` file into your "doukutsu-rs folder".
* You can then delete the old `.exe` file in your folder, or just replace it by dragging the new one in and choosing "Replace" if Windows prompts you.
* **Your settings and save files are safe!** Updating only replaces the program itself. Your game settings and saved games are stored separately ( [#where-are-the-saves-settings-logs](../faq.md#where-are-the-saves-settings-logs "mention") ), so they will not be affected by updating the program file.

**Setup Complete!**

You are now ready to play doukutsu-rs. Run the `doukutsu-rs.{version}.exe` program file located in your "doukutsu-rs folder" to start the game. Enjoy!

{% include "../.gitbook/includes/ask-installation-usage-questions-on-gh-issues-or-the-discord-server.md" %}
