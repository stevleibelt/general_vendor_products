# General

Currently this section contains the drivers and steps you need to do to unlock a Xiaomi Android Smartphone.
All is tested with a Xiaomi Poco X3 (Surya / Karna).

# Unlock

## Unlock Bootloader using a Mi account

* create a [Mi account](https://account.xiaomi.com/)
* on your phone
    * setup your created me account on the phone
    * enable `Developer options`
    * enable `OEM Unlocking`
    * enable `USB debugging`
    * disable `wifi` and enable `mobile data`
    * open `Mi unlock status` and click on `add Mi account with device` (repeat this if step fails)
        * won't work if you are connected via `USB` cable or `WiFi`
        * unlock time can take between one and 21 days
    * power off phone
    * press `volume down` and `power button` to boot into `fastboot`
    * plugin `USB` cable
* on you pc
    * install [`USB`](https://www.xiaomidriversdownload.com/xiaomi-usb-drivers-official/) driver
    * download [`Mi Unlock`](https://www.mi-unlocktool.com/), login with your account and press `unlock`
    * download [`Mi Flash Tool`](https://www.xiaomiflash.com/) and us it 

## Unlock Bootloader with ADB and Fastboot

* it can be that this method won't work
* power off your phone
* press `volume down` and `power button` to boot into `fastboot`
* install [`adb`](https://wiki.archlinux.org/index.php/Android_Debug_Bridge) on your pc
* open a shell
    * `fastboot -h` #if you want to know more
    * `fastboot devices`
    * `fastboot flashing get_unlock_ability`
    * `fastboot flashing unlock`
    * `fastboot flashing unlock_critical`
    * `fastboot reboot`

# Link

* Available Custom Roms
    * [Android Ice Cold Project](https://www.aicp-rom.com/) - 20200108
    * [AOSiP](http://aosip.weebly.com/) - 20200108
    * [Arrowos](https://arrowos.net/) - 20200108
    * [Bliss Roms](https://blissroms.org/) - 20200108
    * [crDroid](https://crdroid.net/) - 20200108
    * [Nitrogen OS](https://sourceforge.net/projects/nitrogen-project/files/surya/) - 20200108
    * [Potato Open Sauce Project / POSP](https://potatoproject.co/) - 20200108
    * [Resurrection Remix OS](https://resurrectionremix.com/) - 20200108
* [Download latest version of Miunlocktool](https://www.mi-unlocktool.com/download-latest-version-of-miunlocktool/) - 20210108
* Stock rom flash files
    * [Fastboot ROM V12.0.4.0QJGMIXM - Europe Stable ROM](https://bigota.d.miui.com/V12.0.4.0.QJGEUXM/surya_eea_global_images_V12.0.4.0.QJGEUXM_20201025.0000.00_10.0_eea_587f5a5a97.tgz) - 20200108
    * [Recovery ROM V12.0.4.0QJGMIXM - Europe Stable ROM](https://bigota.d.miui.com/V12.0.4.0.QJGEUXM/miui_SURYAEEAGlobal_V12.0.4.0.QJGEUXM_6898c27142_10.0.zip) - 20200108
    * [XDA Thread](https://forum.xda-developers.com/f/xiaomi-poco-x3-nfc-roms-kernels-recoveries-ot.11531/) - 20210108
* [xiaomi.eu - MI builds for european law.](https://xiaomi.eu/community/) - 20200108
