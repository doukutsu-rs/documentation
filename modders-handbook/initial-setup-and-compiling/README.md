---
description: Getting the required tools and building doukutsu-rs from source.
---

# Initial setup and compiling

While you can modify the data files of the base engine using a compatible editor such as Booster's Lab (much like you'd do with Cave Story freeware), a lot of times you might want to tweak the engine's behavior to your needs.

In freeware Cave Story, you'd accomplish advanced modifications of the engine by patching the executable file. This is known as Assembly (ASM) hacking.

It is important to note, however, that none of the Assembly hacks that are compatible with the freeware game will work with doukutsu-rs. However, patching the executable is not needed, since the project is open-source, meaning you can clone it, modify it, and compile it to fit your needs.

In this guide, you'll be able to learn what tools you'll need for the task, how to get them, and how to compile the engine from source. The process itself is fairly straightforward and shouldn't take more than 30-40 minutes.

## Windows

### 1. Install the C++ build tools

While the engine itself is written in Rust, some underlying components have C/C++ bindings, therefore you will need to have the C++ build tools installed to download and build the dependencies.

You can download the [build tools from Microsoft's website](https://visualstudio.microsoft.com/visual-cpp-build-tools/).

Once you open the installer, you should select "Desktop development with C++" in the list of workloads, then press "Install" to start the installation. You don't need the other components. You may also install the build tools from the Visual Studio installer, if you're already a Visual Studio user.

![Visual Studio Build Tools installation screen](<../../.gitbook/assets/image (3).png>)

This process will take a while, as it needs to install many components (around 7-8 GB).

Once the installation process has completed, you can close the installer.

> TL;DR: Install "Desktop development with C++" from the [Visual Studio C++ build tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/).

### 2. Install Rust

You can download the `rustup` installer [from Rust's website](https://www.rust-lang.org/tools/install). Unlike the build tools, Rust doesn't have a graphical installer, but the whole process will only take three keystrokes in total.

Once you've downloaded the executable, double clicking it will open up a command prompt. At the bottom, it will ask you to select an installation option. For our purposes, the default installation settings are sufficient, so you can type `1` and press Enter.

![Installing Rust using the default installation settings](<../../.gitbook/assets/image (18).png>)

This process will also take a bit, but once it's done, it will ask you to press Enter to quit the installer.

> TL;DR: install [Rust](https://www.rust-lang.org/tools/install) with the default settings.

### 3. Install CMake

CMake is a build tool for C and C++ projects. You will not need to use CMake directly, however, some of the dependencies we will compile require it to be installed.

Go to the [CMake download page](https://cmake.org/download/), scroll down to "Binary distributions" and download the MSI installer.

![You should download the MSI installer instead of the ZIP file](<../../.gitbook/assets/image (9).png>)

Once you reach to the install options, it's very important to add CMake to PATH, so you must enable this setting, otherwise CMake will not be recognized by Cargo during dependency building.

![Select this option (or the third one) to add the CMake executable to the PATH.](<../../.gitbook/assets/image (20).png>)

Once CMake is installed, we have installed all of the tools we need to compile the project. Woohoo!

> Install [CMake](https://cmake.org/download/) and make sure to select the option to add it to the PATH when prompted.

### 4. Download the source code

Since doukutsu-rs uses Git for version control, you'd normally want to clone the repository using `git`, however, to make it simpler, in this guide we will just download the source code as a ZIP file.

Head over to [our GitHub repository](https://github.com/doukutsu-rs/doukutsu-rs), click on the green "Code" button and select "Download ZIP".

![Download the doukutsu-rs repository as a ZIP.](<../../.gitbook/assets/image (15).png>)

You may extract the contents of the ZIP archive wherever you want, however, we advise you to not extract it:

* in a system directory, or any directory that requires administrator access (such as Program Files)
* in a cloud sync directory (such as directories synced to OneDrive) - this is because there will be lots of files, which will not only waste your cloud storage, but such folders are known for not being able to handle many smaller files too well (and efficiently)

> TL;DR: download the [source code from GitHub](https://github.com/doukutsu-rs/doukutsu-rs) and extract it to a non-administrator directory.

### 5. Compile the project

We will do most of the work in a terminal/command line, therefore, the next step is to right click the directory you've just extracted and select "Open in Windows Terminal" (or Command Prompt/Powershell).

![Opening the extracted doukutsu-rs directory in Windows Terminal on Windows 11.](<../../.gitbook/assets/image (3) (1).png>)

A window like this should pop up:

![doukutsu-rs source directory opened in Windows Terminal.](<../../.gitbook/assets/image (1) (1).png>)

...and we've finally reached the most exciting part of the process - compiling the engine. Run the following command to create a debug build:

```
cargo build
```

This process is going to take a while, as it needs to download and compile all the dependencies that are required by doukutsu-rs. It's important to note, however, that this will only take so long on the very first time you compile the engine. Any builds after that should be fairly quick.

Once the build has finished, you should be seeing the following:

![doukutsu-rs finished building.](<../../.gitbook/assets/image (14).png>)

> TL;DR: open the extracted directory in a terminal and run `cargo build`.

### 6. Acquire data files and run

doukutsu-rs doesn't bundle the game's data files, therefore you will need to obtain them yourself. There's a [detailed guide on how to do that](https://github.com/doukutsu-rs/doukutsu-rs#data-files) in the README of the GitHub repository.

If you go back to your file explorer now, you'll be able to see a new directory called "target", with another directory called "debug" inside. If you see a file called "doukutsu-rs.exe" there, that means everything went smoothly! You must copy your "data" directory into this directory. You should be seeing the following file structure:

![doukutsu-rs debug target directory with data files.](<../../.gitbook/assets/image (23).png>)

From here, you can double-click the `doukutsu-rs.exe` file to run the game. You can also run the following in the terminal if you want to build and run from one place:

```
./target/debug/doukutsu-rs.exe
```

> TL;DR: copy your [data files](https://github.com/doukutsu-rs/doukutsu-rs#data-files) to the build directory and run the executable.

## Linux

Naturally, most of the installation process will happen through your distribution's terminal. Since there's many flavors of Linux and desktop environments made for Linux operating systems, we can't go into too many details about doing it "the GUI-way", however, we will try to generalize as much as possible. Doing everything from the terminal helps in this process.

### 1. Install the development dependencies

To get started, we will need to following software:

* gcc or clang: for compiling the project's C/C++ dependencies
* cmake: the build system used by some dependencies
* git: for cloning the source files and the game data files
* rust: to compile the project

How you're going to install these dependencies depends on what Linux distribution you're using. We will cover the three most popular ones.

#### Debian-based distributions (Debian, Ubuntu, Linux Mint, Pop!\_OS, etc.)

```
sudo apt update
sudo apt install build-essential cmake git
```

#### Arch-based distributions (Arch Linux, Manjaro, EndeavourOS, etc.)

```
sudo pacman -Sy
sudo pacman -S base-devel cmake git
```

#### Red Hat-based distributions (CentOS, Fedora, etc.)

```
sudo dnf upgrade
sudo dnf install make automake gcc gcc-c++ kernel-devel cmake git
```

{% hint style="warning" %}
**Note:** on a regular desktop Linux installation, these tools should be enough, as everything else should already be installed. However, if you're trying to do this on a server or Windows Subsystem for Linux, you will need to install additional dependencies:

* Debian: `libasound2-dev libudev-dev pkg-config`
* Arch: `alsa-lib`
* Red Hat: `alsa-lib-devel`

Please also note that the project will not run unless you have a valid video device connected to your computer. Thus, while you may be able to compile doukutsu-rs on a server, you will not be able to run it. Newer versions of WSL support proxying video input to Windows if you configure the X Window System on your WSL container.
{% endhint %}

Installing Rust should be identical on every Linux distribution. Just run the following command:

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Press `1` and the Enter key, when prompted for installation options.

Once the installation has completed, you might want to add the Rust binaries to your PATH environment variable. To do this, you want to edit your shell configuration file.

#### bash

```
nano ~/.bashrc
```

Add the following at the end of the file:

```
export PATH="$HOME/.cargo/bin:$PATH"
```

Press Ctrl+S and Ctrl+X when done, then run:

```
source ~/.bashrc
```

#### zsh

```
nano ~/.zshrc
```

Add the following at the end of the file:

```
export PATH="$HOME/.cargo/bin:$PATH"
```

Press Ctrl+S and Ctrl+X when done, then run:

```
source ~/.zshrc
```

#### fish

```
nano ~/.config/fish/config.fish
```

Add the following at the end of the file:

```
set -U fish_user_paths $HOME/.cargo/bin $fish_user_paths
```

Press Ctrl+S and Ctrl+X when done, then run:

```
source ~/.config/fish/config.fish
```

...and just like that you should be ready to go. We can start cloning the repository!

### 2. Clone the source code

You may `cd` in a directory of your choice and use `git` to clone the repository from GitHub:

```
git clone https://github.com/doukutsu-rs/doukutsu-rs.git
cd doukutsu-rs
```

![Cloning the doukutsu-rs repo using git.](<../../.gitbook/assets/image (2) (1).png>)

### 3. Compile the project

Once you're in the `doukutsu-rs` directory, run the following command to fetch all dependencies and compile the project in debug mode:

```
cargo build
```

This process will take a while, as it has to fetch and compile lots of dependencies. Once you see the following message, you should be good to go:

![cargo build finished for doukutsu-rs.](<../../.gitbook/assets/image (8).png>)

This will build the project in debug mode, so you will find the executable in the `target/debug` subdirectory.

### 4. Acquire data files and run

You can use `git` to acquire the data files needed to run the game.

```
git clone https://github.com/doukutsu-rs/game-data.git target/debug/data
rm -rf target/debug/data.git target/debug/data/README.md
```

To run the project, just run the following command:

```
./target/debug/doukutsu-rs
```

## Mac

Similarly to Linux, we will do most of the initial setup process and compilation through the Mac OS terminal. You can search for the Terminal app in the Launchpad or Spotlight.

### 1. Install the Xcode Command Line Tools

While you could install Xcode as a whole from the App Store, it will take a long time (sometimes up to a few hours, even) and you will likely not need most of the tools from there anyway, so it would be a waste of storage space as well. Luckily, Mac OS provides a way to install just the command line tools, without Xcode itself and all the extra tools that comes with it.

To do this, run the following command in the terminal:

```
xcode-select --install
```

You will see a prompt where you'll have to confirm the installation. After confirming it, the installation will take around 8 to 10 minutes, but it could take longer on older devices.

This will install many things, but in our scope, it's responsible for installing the following:

* C/C++ compiler
* git

We will also need to install Homebrew, which will let us install additional packages more easily. To do this, use the following command:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once brew is installed, we can install CMake using the following command:

```
brew install cmake
```

To install Rust, the process is identical to how you'd install it on Linux. Run the following command to set up `rustup`:

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Type `1` when prompted and press Enter:

![rustup asking for installation options on Mac OS](<../../.gitbook/assets/image (6).png>)

After that, you need to add the Rust binaries to your PATH. The Linux guide contains [instructions for zsh (Mac OS default shell) and other shells](./#bash). If you haven't done any development on your Mac before, it's very likely that you need to follow the `zsh` guide. To check, you can run the following command:

```
echo $SHELL
```

### 2. Clone the source code

The initial `xcode-select` command will also install Git, which we will use to clone the doukutsu-rs repository.

Using the `cd` command, navigate to the directory where you want to clone the project, then run the following commands in succession:

```
git clone https://github.com/doukutsu-rs/doukutsu-rs.git
cd doukutsu-rs
```

Type `ls -ahg` to confirm that the cloning was successful. You should be seeing something like this:

![doukutsu-rs root directory on Mac OS.](<../../.gitbook/assets/image (19).png>)

### 3. Compile the project

Run the following command to compile doukutsu-rs in debug mode:

```
cargo install
```

This process will take a while, as it has to fetch and compile lots of dependencies. Once you see the following message, you should be good to go:

![doukutsu-rs finished building on Mac OS.](<../../.gitbook/assets/image (13).png>)

This will build the project in debug mode, so you will find the executable in the `target/debug` subdirectory.

### 4. Acquire data files and run

You can use `git` to acquire the data files needed to run the game.

```
git clone https://github.com/doukutsu-rs/game-data.git target/debug/data
rm -rf target/debug/data.git target/debug/data/README.md
```

To run the project, just run the following command:

```
./target/debug/doukutsu-rs
```
