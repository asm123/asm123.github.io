---
layout: post
date: 2023-12-22
title: Open Visual Studio Code from terminal (macOS)
tags: programming
last_updated: 2023-12-22
status: final
type: article
---

This post assumes Visual Studio Code is already installed.

Open "Command Palette" in Visual Studio Code. This can be done from the menubar with `View -> Command Palette`, or by hitting `Cmd+Shift+P`.

In the Command Palette, search `Install code`.
![Alt text](/assets/images/vscode-from-terminal/command-palette.png)

Select `Shell Command: Install 'code' command in PATH` and hit enter.

This will open a popup asking for admin privileges to install the shell command.  Hit enter.
![Alt text](/assets/images/vscode-from-terminal/pop-up-1.png)

Next popup will ask for your system password so that `osascript` can Visual Studio Code binary in the `PATH` variable for your shell. Type in your password and hit enter.
![Alt text](/assets/images/vscode-from-terminal/password-pop-up.png)

You will see another popup with success message. 
![Alt text](/assets/images/vscode-from-terminal/install-successful.png)

And we are done!!! Open a new terminal and use `code` command to open Visual Studio Code from terminal. Try `code --help` to know what else can be done using terminal.

## Behind the scene

What happened behind the scene?

* We are launching Visual Studio Code from terminal with command `code`. Where does `code` point to? Let's find out:

    Command:
    ```shell
    which code
    ```

    Output:
    ```shell
    /usr/local/bin/code
    ```

* `/usr/local/bin` directory holds binaries or symlinks to binaries. Let's see what `/usr/local/bin/code` is:

    Command:
    ```shell
    ls -l /usr/local/bin/code
    ```
    Output:
    ```
    lrwxr-xr-x  1 root  wheel  68 Dec 22 20:08 /usr/local/bin/code -> /Applications/Visual Studio Code.app/Contents/Resources/app/bin/code
    ```
    This tells us that `/usr/local/bin/code` is a symlink to `code` executable within the application directory.

* Very likely `/usr/local/bin` is already in your `PATH` shell variable. Therefore, `code` command (or rather symlink to the command) becomes available to you as soon as the symlink was created. Check it out by printing the `PATH` variable:

    Command:
    ```shell
    echo $PATH
    ```

Now that we know what changed behind the scene, we can alternatively do the same thing on our own:

1. Find the path for Visual Studio Code `code` executable and create a symlink to the `code` binary in `/usr/local/bin`:
    ```
    ln -s /Applications/Visual Studio Code.app/Contents/Resources/app/bin/code /usr/local/bin/code
    ```
    
    We can change the symlink to something other than `code` as well.

2. Alternatively, skip creating symlink altogether and instead append the `/Applications/Visual Studio Code.app/Contents/Resources/app/bin/` path to your `PATH` shell variable.
    ```
    export PATH=$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin/
    ```
    Be aware that this will make all the executables in `/Applications/Visual Studio Code.app/Contents/Resources/app/bin/` directly similar to how `code` became instantly available. Option 1 may be cleaner.