# how to install linage os 16

## unlock boot loader

[source - xda-developers.com](https://forum.xda-developers.com/moto-x4/how-to/guide-how-to-root-moto-x4-install-twrp-t3806460)
[source - youtube.com](https://www.youtube.com/watch?v=UVKUDZSyjW4)
[source - androidjunkies.com](https://www.androidjungles.com/root-moto-x4-install-twrp-recovery-payton/)

* power on the phone
* go to settings->system->about phone->tab seven times on >>Build Number<< to enable developer mode
* go to settings->system->developer options->enable >>OEM unlocking<<
* go to settings->system->developer options->enable >>USB debugging<<
* turn phone off
* go into fastboot by pressing "volume down"+"power"-buttons
* connect phone with your pc and switch to a shell
* fastboot devices
* fastboot oem get_unlock_data
* register and login to this [motorola page](3A65150618936951#5A593232344B374D5250006D6F746F2078340000#D9248C1343950C4E55BC3)
* [request unlock key](https://motorola-global-portal.custhelp.com/app/standalone/bootloader/unlock-your-device-b)
* fastboot oem unlock <unlock key>
* fastboot flashing unlock
* fastboot reboot

## install twrp

[source - youtube.com](https://www.youtube.com/watch?v=Z6bZZJseEvg)
[source - android.com](https://source.android.com/setup/build/running)
[source - twrp.me](https://twrp.me/motorola/motorolamotox4.html)

* [read](https://twrp.me/motorola/motorolamotox4.html)
* [download](https://dl.twrp.me/payton/) twrp (img and zip)
* fastboot devices
* fastboot boot twrp-\*-payton.img
* adb sideload way
    * adb push twrp-installer-\*.zip /sdcard
* put twrp installer on the android filesystem and install it from there
* fastboot reboot

## install magisk

* [download](https://github.com/topjohnwu/Magisk/releases) apk
* [source - trueandroid.com](https://www.trueandroid.com/how-to-root-motorola-moto-x4-in-2019-easy-guide/)

* either by adb push or by doing it from the android file system
* install magisk-\*.zip
* reboot and install magisk manager

## install linage os

[source - xda-developers.com](https://forum.xda-developers.com/moto-x4/development/rom-lineage-os-15-1-t3802265)
[source - youtube.com](https://www.youtube.com/watch?v=NWOBa88eJRs)

* [download linageos](https://download.lineageos.org/payton) linage os
* [download open gapps](https://opengapps.org/) (arm64, 9.0, nano)
* [download copy-partitions-payton](https://androidfilehost.com/?fid=11410963190603889559)
* start into twrp
* install linageos
* install gapps

## root it

[source - lineageosrom.com](https://www.lineageosrom.com/2018/09/lineage-os-16-root-android-pie-90-super.html)

* [download supersu](https://download.chainfire.eu/1220/SuperSU/SR5-SuperSU-v2.82-SR5-20171001224502.zip)
* restart into recovery mode
* install supersu
* restart lineage os

# links

* [linageos page](https://wiki.lineageos.org/devices/payton)
* [How To:Moto X4 Root (Magisk) & TWRP Recovery on Android 9.0 Pie](https://www.youtube.com/watch?v=Z6bZZJseEvg) - 2019-07-05
