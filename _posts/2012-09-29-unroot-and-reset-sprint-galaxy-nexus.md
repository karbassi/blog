---
layout: post
title: "Unroot and Reset the Sprint Galaxy Nexus - Mac"
date: 2012-09-29
---

> **Warning**: The following steps WILL format the device. Be sure to do a complete backup before preceeding.

1. Download the [Android SDK].

2. Install the SDK as instructed.

3. Follow the instructions on this page from the Android SDK’s "[Adding Platforms and Packages]"

4. Check and install the "Android SDK Platform-Tools" only.

5. You should have a directory called `android-sdk-mac_x86`. Within that, there should be directory called `Platform-Tools`.

6. Go as instructed to the "[Return To Stock (ODIN TARS & FASTBOOT IMGS)]" page. Second post will have the FASTBOOT images. For stock Jelly Bean search for **FH05**. There is 6 files that need to download.

7. Place all the downloaded files inside `android-sdk-mac_x86/platform-tools/` directory.

8. Shut down the device, then press and hold Volume Up, Volumn Down, and Power at the same time. This will enter to the bootloader.

9. Connect the device via USB to the computer.

10. Open terminal and go into the "platform-tools" directory.

11. Enter the following lines, one at a time.
    ```bash
    ./fastboot flash boot boot.img
    ./fastboot flash bootloader bootloader.img
    ./fastboot flash recovery recovery.img
    ./fastboot flash system system.img
    ./fastboot flash radio radio-cdma.img
    ./fastboot flash radio radio-lte.img
    ./fastboot -w
    ```

12. Enter the following to lock the device also.
    ```bash
    ./fastboot oem lock
    ```

[Android SDK]: http://developer.android.com/sdk/index.html
[Adding Platforms and Packages]: http://developer.android.com/sdk/installing/adding-packages.html
[Return To Stock (ODIN TARS & FASTBOOT IMGS)]: http://forums.androidcentral.com/sprint-galaxy-nexus/206954-guide-return-stock-odin-tars-fastboot-imgs.html\#post2140080
