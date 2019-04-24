# How to install a custom ROM on Xiaomi Mi A2 Lite

### Prerequisites
* Official 10.3.0.0 firmware: http://bigota.d.miui.com/V10.0.3.0.PDLMIXM/daisy_global_images_V10.0.3.0.PDLMIXM_20190114.0000.00_9.0_e8d8d4a6d0.tgz
* Fastboot and ADB: https://www.xda-developers.com/google-releases-separate-adb-and-fastboot-binary-downloads/
* Offain's TWRP image: https://androidfilehost.com/?fid=1395089523397933315
* Offain's TWRP ZIP: https://androidfilehost.com/?fid=1395089523397933316
* ForceEncryption disabler: https://zackptg5.com/downloads/Disable_Dm-Verity_ForceEncrypt_04.03.19.zip
* A custom ROM ZIP, for example crDroid: https://crdroid.net/daisy

### Introduction
Installing a custom ROM on an Android phone used to be a walk in the park. However, some newer phones, like Xiaomi Mi A2 Lite, have what's called an **A/B partition layout**. This facilitates an update process on stock ROMs, however it makes it harder to install and develop custom ROMs. You can read more about A/B partitions here: https://www.xda-developers.com/how-a-b-partitions-and-seamless-updates-affect-custom-development-on-xda/  

The upshot is that Mi A2 Lite doesn't have a recovery partition. Instead, when you install TWRP, it gets installed in the boot partition. Which means that every time you install or update the ROM, you will need to re-flash the recovery ZIP. One more thing to keep in mind is that the ROM **always gets installed to another slot**. Meaning, if you're currently in the slot B, the ROM will be installed to the slot A, vice versa. 

## Installation process

#### 1. Install the stock ROM
* Install fastboot and adb on your computer
* Put all the prerequisites in one folder on your computer
* Turn off your phone, wait for 3 seconds, then press volume down and power buttons simultaneously until you see the fastboot logo (you won't miss it)
* Connect the phone to the computer (do it fast, because the phone will turn off after a few seconds without being connected to the computer)
* Back up all of the data on your phone, then go to the folder with stock firmware (*daisy_global_images_V10.0.3.0.PDLMIXM_9.0*)
* Double click on `flash_all.bat` 
* Wait for the process to be finished

#### 2. Flash the custom ROM
* After your phone has rebooted successfully, turn it off and go into the fastboot mode again. Connect the phone to the computer
* Launch the command line and go to the folder where you put all the prerequisites (`cd Folder_name`)
* Boot the recovery image: `fastboot boot twrp-daisy-3.3.0-0-offain.img`
* You will see the recovery on your phone, prompting to enter the password. Choose "Cancel"
* In the main menu, choose "Wipe", then tap "Format Data". Type "yes".
* On your computer, copy all the ZIPs you've downloaded earlier using adb: `adb push *.zip /sdcard`
* On your phone, tap "Install" and flash the files in the following order:
  * Custom ROM
  * TWRP ZIP
  * ForceEncryption Disabler
* Don't install Magisk, GApps or anything else yet, we will do that later!
* After everything is done, **DON'T TAP REBOOT YET**. Instead, go back to the main menu, choose "Reboot", change the slot (e.g. if it says "Current Slot: A", tap "Slot B", vice versa. Finally, tap "Reboot"

#### 3. Post installation
* After your phone has successfully booted into the ROM, turn your phone off, wait for a few seconds, then press Volume Up and Power buttons simultaneously for ~3 seconds. This will make your phone boot into recovery mode
* Copy anything you would like to install on your phone (Magisk, Gapps, modules, etc.) and flash it the usual way.
* Reboot your phone

