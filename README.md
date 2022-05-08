# Installing Droidian

In order to streamline the instructions, a generic installation guide is provided here. The needed files and device-specific considerations are listed in the pages for each device.

**Make a backup now, as your device will be wiped.**

## 0. Download the needed files and tools
- The page specific to your device lists all of the files you'll need to download.
- File types: 
    - `.zip` files can be flashed using the recovery menu when the `Install zip` option is selected. 
    - `.img` files can be flashed using the recovery menu when the `Install image` option is selected. You will need to specify the partition to flash: refer to the device page for each file.

## 1. Device preparation
- Save your APN (Android)
    - The `Access Point Name` or `APN` can be found in the Settings menu of Android
    - Take a piece of paper or a text editor, and write down everything that you see on that screen
    - These are likely to include a URL (e. g., `internet.carrier.net`), a username, and possibly a password
- Unlock the bootloader (Computer)
    - Refer to the instructions provided by the device manufacturer
    - Other useful sources include the [LineageOS wiki](https://wiki.lineageos.org/devices/) and [xda-developers](https://www.xda-developers.com/search2/)
- Boot into recovery (Computer)
    - TWRP is the recommended recovery for Droidian. For other recoveries, refer to the documentation of your recovery of choice.
    - Boot TWRP by running `fastboot boot twrp-VERSION-DEVICE.img`
- Wipe the device (TWRP)
    - Go to the `Wipe` menu
    - Select `Advanced wipe`
    - Tick the boxes called `Dalvik / ART cache`, `Cache`, `System`, `Vendor`, `Data`
    - Swipe to Wipe
    - Go back to the previous menu
    - Choose `Format data` and type `yes`
    - Go back to the main menu and select `Reboot`
    - Choose `Bootloader`
    - Boot TWRP again by running `fastboot boot twrp-VERSION-DEVICE.img` on your computer
- Copy the files to the device  (Computer)
    - When TWRP is booted, open the device's `Internal storage` from your computer
    - Copy all of the files you downloaded to this folder

## 2. Droidian installation (TWRP)
- Install the required base Android version (9, 10, 11)
    - Install the file specified as `Android Base` in the device page
- Install vendor-related packages
    - Install the file(s) specified as `Vendor package` in the device page
- Install TWRP
    - Install the TWRP image file (`twrp-VERSION-DEVICE.img`) to the `Recovery` partition
- Install `rootfs`
    - Install the file named `droidian-rootfs-arm64_YYYYMMDD.zip`
- Install `devtools` (for stable release)
    - Install the file named `droidian-devtools-arm64_YYYYMMDD.zip`
    - This component is already included in nightly builds
    - Installation is optional for stable releases, but it is recommended, because it helps with debugging

## 3. Finalizing the installation
- Install adaptation package as a flashable zip (TWRP)
    - If the device page provides a file specified as `Adaptation zip`, install it now
- Boot your device
    - Go to the `Reboot` menu and choose `System`
    - TWRP might complain that there is no OS installed, but that's fine
    - The first boot may take longer, and at least one spontaneous reboot is expected during the process
    - You should be greeted with the lock screen, the default password is `1234`
- Run a specific command after first boot (Droidian)
    - If the device page specifies a `Command` you need to run, open the `King's Cross` application, and type in the command
    
Congratulations, if everything went well, now you should be running Droidian.
Flashing the `devtools` zip enabled `SSH` over USB. To use it, connect your phone to your computer and type `ssh droidian@10.15.19.82`, the password is `1234` (on Windows, you may need [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/))
