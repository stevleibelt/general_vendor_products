# how to install linage os 16

## unlock boot loader

[source](https://www.youtube.com/watch?v=UVKUDZSyjW4)

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
* fastboot reboot

## install twrp

# links

* [linageos page](https://wiki.lineageos.org/devices/payton)
* [How To:Moto X4 Root (Magisk) & TWRP Recovery on Android 9.0 Pie](https://www.youtube.com/watch?v=Z6bZZJseEvg) - 2019-07-05
