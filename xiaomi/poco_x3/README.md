# Xiaomi Poco X3

## Install CRDroid 8.12

* First of all, donate for each used software named below
* Make a backup 
  * Use [Neo Backup](https://f-droid.org/en/packages/com.machiav3lli.backup/)
  * And [Syncthing](https://f-droid.org/packages/com.nutomic.syncthingandroid/)
* Download
  * [Magisk](https://github.com/topjohnwu/Magisk/releases)
  * [Saftynet-fix](https://github.com/kdrag0n/safetynet-fix/releases)
  * [AnxCam](https://sourceforge.net/projects/miuicamerapocox3/files/MIUICameraPocoX3.zip/download)
* Reboot to twrp/ofox.
* Do factory reset + format data.
  * `wipe` -> `advanced wipe`
    * `Dalvik / ART Cache`
    * `Package Cache`
    * `Cache`
    * `Metadata`
    * `Data`
* Reboot to twrp/ofox and flash ROM.
  * `Install`
    * `Flash firmware`
    * `Flash crdroid`
* Flash Gapps & Magisk (optional)
  * `Install`
    * `Flash magisk`
    * `Flash gaps`
  * `Wipe`
    * `Format Data`
* Flash #dfe if you want to be decrypted
* Reboot to system and profit

## Install Linageos

* [Download](https://download.lineageos.org/surya) linageos and recovery for poco x3
* [Download](https://wiki.lineageos.org/gapps.html) opengapps for poco x3 and fittng android
* Reboot into recovery
* `fastboot flash recovery linage*-recovery-sury.img`
* `fastboot boot linage*-recovery-sury.img`
* `Factory Reset` -> `Format data / factory reset`
* Return to main menu
* `Apply Update` -> `Apply from ADB`
* For each zip file you want to sideload
  * `adb sideload <package>.zip`

## Links

* [crCdroid 9.1 for poco x3](https://crdroid.net/surya/9)
* [Firmware download for poco x3](https://xiaomifirmwareupdater.com/firmware/surya/)
* [OrangeFox download for poco x3](https://sourceforge.net/projects/builds-ardjlon/files/surya/recovery/OrangeFox-Unofficial-surya_FBEv2.zip/download)
* [NikGapps](https://sourceforge.net/projects/nikgapps/files/Releases/NikGapps-T/08-Sep-2022/)
* [Magisk](https://github.com/topjohnwu/Magisk/releases)
  * [Saftynet-fix](https://github.com/kdrag0n/safetynet-fix/releases)
* [AnxCam](https://sourceforge.net/projects/miuicamerapocox3/files/MIUICameraPocoX3.zip/download)
