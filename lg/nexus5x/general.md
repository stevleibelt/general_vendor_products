# arch linux

## needed software packages

* android-tools
* android-udev
* adb-sync

# arm or arm64?

It has a [arm64](https://duckduckgo.com/?q=does+nexus+5x+has+an+arm+or+arm64+processor&t=ffab&ia=qa)

# error

## Vendor Image Missmatch

Taken from [here](https://www.reddit.com/r/LineageOS/comments/5xwnb9/weird_vendor_image_mismatch_after_update/) and [here](http://www.gandalfk7.it/2018/07/15/nexus-5x-lineageos-15-1-vendor-image-mismatch-has-been-detected/).

* download latest official [vendor image](https://developers.google.com/android/drivers#bullhead)
* extract vendor.img
* sudo fastboot flash vendor vendor.img

# steps to install twrp

* poweron device
* unlock developer option
* adb devices
* adb reboot bootloader
* fastboot flashing unlock
* reboot device
* reenble usb debugging
* [download](https://twrp.me/lg/lgnexus5x.html) twrp
* adb reboot bootloader
* fastboot flash recovery twrp-\*
* select "recovery mode" from the device

# steps to install a rom

* power+volume down
* select recovery mode to start twrp
* enable adb sideload
* adb sideload \<image>
* adb sideload gapps
* adb sideload magisk

# link

* [xda main page](https://forum.xda-developers.com/nexus-5x)
    * [resources compilation](https://forum.xda-developers.com/nexus-5x/general/index-lg-nexus-5x-resources-compilation-t3208297)
    * [wont boot thread](https://www.reddit.com/r/LineageOS/comments/7aowoj/nexus_5x_wont_boot/)
* [magisk](https://forum.xda-developers.com/apps/magisk)
    * [magisk manager](https://magiskmanager.com/)
* [linage os](https://wiki.lineageos.org/devices/bullhead)
* [linageos](https://wiki.lineageos.org/devices/hammerhead/install)
    * [xda thread](https://forum.xda-developers.com/google-nexus-5/orig-development/rom-lineage-os-14-1-nexus-5-t3528849)
    * [adb kickstart](https://wiki.lineageos.org/adb_fastboot_guide.html#setting-up-adb)
    * [lineageos extras download page](https://download.lineageos.org/extras) - use arm64
    * [15.1 image](https://download.lineageos.org/bullhead)
        * [endless boot?](https://www.reddit.com/r/LineageOS/comments/7jf4sb/stuck_at_boot_animation_after_installing_lineage/) - Try "Wipe" -> "Format Data" -> "Yes" in TWRP
* [resurrection remix](http://www.resurrectionremix.com/)
    * [forum](http://forum.resurrectionremix.com/)
    * [v6.1 xda thread](https://forum.xda-developers.com/nexus-5x/development/resurrectionremix-v6-0-08-1-0r11-t3748115)
    * [Install Resurrection Remix v6.0.0 On Nexus 5X (Android 8.1 Oreo)](https://rootmygalaxy.net/install-resurrection-remix-v6-0-0-on-nexus-5x-android-8-1-oreo/) - 2018-03-25
    * [How To Install Official Resurrection Remix On Google Nexus 5X (Android 7.1.2)](https://www.getdroidtips.com/resurrection-remix-nexus-5x/) - 2018-03-07
    * [resurrection image](https://sourceforge.net/projects/resurrectionremix-oreo/files/bullhead/download)
* [bootloop fix](https://www.xda-developers.com/nexus-5x-bootloop-fix-boot-phone/)
    * download [N2G47Z_4Cores.img](https://www.dropbox.com/s/tm7qt98r6d7q2a6/N2G47Z_4Cores.img?dl=0)
    * fastboot flash boot N2G47Z_4Cores.img
* [google android full OTA images / stock rom / factory rom](https://developers.google.com/android/images#bullhead)
    * [vendor image](https://developers.google.com/android/images)
    * [howto](https://developers.google.com/android/images)
* [vendor image](https://androidfilehost.com/?w=files&flid=49360)
* [open gapps](http://opengapps.org/?arch64=arm&api=8.1)
* [twrp](https://dl.twrp.me/bullhead/)
