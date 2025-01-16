---
title: Download Games to Batocera Natively using Firefox
date: 2025-01-16 14:31:40 +0300
categories: [Gaming, Retro]
tags: [batocera,firefox,peazip,flatpak]
author: saleem
---

Recently, we have purchased an old **Dell OptiPlex 9020** and looked for a **Zotac GTX 1660 Super** with a very low price from the local market selling used stuff at my country, it's for my little brother to get him started at gaming.

We have done some modifications to install the graphics card into that PC like upgrading the power supply along with adding two SSD drives which resulted in a great performance for gaming specifically at 1080p resolution.

## The Problem
As might be expected, we have decided to do [Retro Gaming](/categories/retro/) as well and that's when we came across [Batocera](https://batocera.org/) and actually installed it on the secondary internal SSD instead of an USB stick alongside **Windows** which is installed on the primary drive.

We had two options to transfer game files or ROMs to the SSD containing **Batocera**, either by moving them to an USB stick or just by using the file manager to access the SSD drive of Windows then copy data from there.

Ideally, we wanted the files to be saved on the SSD directly from Batocera without going to another PC or booting to windows and also not by using an external storage device or transfering them through the network which is recommended by the instructions on the [official wiki](https://wiki.batocera.org/add_games_bios).

In most scenarios, we had to boot first to Windows and download the files from there then use the methods available to transfer tha data which requires another restart process to boot Batocera again and copy the files which is a hassle obviously.

## The Solution
Apparently, we had to figure out the way to download and add games natively running on **Batocera** without restarting and booting back to **Windows**, which is now possible even on the latest version of Batocera.

### Required Applications
You only have to make use of two applications available on the [Flatpak Package Manager](https://wiki.batocera.org/systems:flatpak) which are:
- Firefox (Popular browser available for Linux distributions)
- PeaZip (Free archiver utility to extract files)

### Installation
You can install the required packages on Batocera easily, make sure you are connected to the internet and follow the steps starting from the main screen:
1. Open the File Manager by pressing `F1` on your keyboard.
2. Navigate to "Applications" from the left sidebar.
3. Launch "flatpak-config" from the shortcut.
4. Search for "firefox" and then "peazip" from the search bar.
5. Click on the "Install" green button for both applications.

Once finished, open "xterm" from the "Applications" menu again then type the following command:

```bash
batocera-flatpak-update
```
{: .nolineno }

Press `Enter` to apply the command, now you can find both applications available in the "Ports" at the main screen of Batocera.

### Fix Firefox
By defult, when downloading files from **Firefox** it will not save your files which is a problem that we can solve by issuing the following command again by using "xterm" from the "Applications" menu:

```bash
flatpak override –filesystem=host org.mozilla.firefox
```
{: .nolineno }

You can now download any file you want from Firefox and it will save just fine.

> You can exit the "xterm" application by typing "exit" as a command and pressing `Enter`.
{: .prompt-tip }

## The Process
It's so easy to achieve what we want now, I will summarize it in a few points.

### Set Path for Downloads
So, open **Firefox** from the "Ports" section in the main screen then click on the row of bars on the upper right corner of the browser to bring up the menu. Now, you will see the options, from there select "Settings".

Scroll down till you find "Downloads" and "Save files to" this is the path of the downloads folder, note that down or just remember it so you can navigate to it from the PeaZip application after you download your ROMs.

> Alternatively, you can create your own folder at any location you want and set it to that path by clicking on `Browse` and selecting your own path.
{: .prompt-info }

### Downloads ROMs
Simply, navigate to your favorite website for downloading game ROMs like you would normally do on any operating system by using **Firefox** as a browser.

### Extract ROMs
Open **PeaZip** from the "Ports" section in the main screen then navigate to the downloads folder path that you have just noted. Find your ROM file and select it then click on "Extract" from the options above then click on the `OK` button.

### Add ROMs
Open **File Manager** from the main screen by pressing on `F1` from the main screen then navigate to the downloads folder path again but this time you will find the extracted raw file which you can then copy to your relevant "roms" directory in Batocera. 