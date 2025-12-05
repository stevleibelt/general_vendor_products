# Xiaomi Poco X3

You can [verify](https://www.mi.com/global/verify#/en/tab/imei) your device to find the right firmware.

Model M2007J20CG is handled as global.

You have to enable developer options via `About this phone` -> Tap on `Build number` until you've unlocked the developer options.  
You have to enable usb debugging via `System` -> `Developer options` -> `USB debugging`

## Unlock bootloader

```bash
fastboot flashing get_unlock_ability
```

## Backup using adebar

```bash
# ref: https://codeberg.org/izzy/Adebar
mkdir my_backup
cd my_backup
mkdir data
wget https://codeberg.org/izzy/Adebar/raw/branch/master/doc/quickstart_config.sample
mv quickstart_config.sample poco_x3.config
# open the files and adapt it
vim poco_x3.config
# enable usb debugging on your phone
# enable usb debugging on your phone
# check to allow adb connection
adebar data
cd data
# unlock your device and confirm all steps
./sysbackup
./userbackup
```

## Install `/e/OS`

This is a summary of [this](https://doc.e.foundation/devices/surya) page and the [official installation instruction](https://doc.e.foundation/devices/surya/install).  
It is assumed:
* You've already unblocked the bootloader
* Your system as a working `adb` command
* Your system as a working `fastboot` command

```bash
mkdir e_os
cd e_os
rm *
# This is the recovery image
# ref: https://images.ecloud.global/community/surya/
wget https://images.ecloud.global/community/surya/recovery-e-3.2-a15-20251023539368-community-surya.img
wget https://images.ecloud.global/community/surya/recovery-e-3.2-a15-20251023539368-community-surya.img.sha256sum
sha256sum recovery-e-3.2-a15-20251023539368-community-surya.img

# Download /e/OS
wget https://images.ecloud.global/community/surya/e-3.2-a15-20251023539368-community-surya.zip

# This is the global firmware
wget https://bn.d.miui.com/V14.0.2.0.SJGMIXM/miui_SURYAGlobal_V14.0.2.0.SJGMIXM_9aaad01ef3_12.0.zip
# Flash to this firmware
unzip -qq miui_*.zip firmware-update/*
cd firmware-update
# Power one the device while holding `Volume Down` + `Power` until `FASTBOOT` appeads
fastboot flash abl abl.elf
fastboot flash ablbak abl.elf
fastboot flash aop aop.mbn
fastboot flash aopbak aop.mbn
fastboot flash bluetooth BTFM.bin
fastboot flash cmnlib cmnlib.mbn
fastboot flash cmnlibbak cmnlib.mbn
fastboot flash cmnlib64 cmnlib64.mbn
fastboot flash cmnlib64bak cmnlib64.mbn
fastboot flash devcfg devcfg.mbn
fastboot flash dsp dspso.bin
fastboot flash hyp hyp.mbn
fastboot flash hypbak hyp.mbn
fastboot flash imagefv imagefv.elf
fastboot flash imagefvbak imagefv.elf
fastboot flash keymaster km4.mbn
fastboot flash keymasterbak km4.mbn
fastboot flash storsec storsec.mbn
fastboot flash modem NON-HLOS.bin
fastboot flash qupfw qupv3fw.elf
fastboot flash qupfwbak qupv3fw.elf
fastboot flash tz tz.mbn
fastboot flash tzbak tz.mbn
fastboot flash uefisecapp uefi_sec.mbn
fastboot flash uefisecappbak uefi_sec.mbn
fastboot flash xbl xbl.elf
fastboot flash xblbak xbl.elf
fastboot flash xbl_config xbl_config.elf
fastboot flash xbl_configbak xbl_config.elf
cd ..
fastboot reboot

# Conect device via usb
adb reboot bootloader
# Or if the device is powered of
# Power one the device while holding `Volume Down` + `Power` until `FASTBOOT` appeads

# Validate that your system sees the device
fastboot devices

# Flash recovery image
fastboot flash recovery recovery-e-3.2-a15-20251023539368-community-surya.img
# If you run into an issue like: Warning: skip copying recovery image avb footer (recovery partition size: 0, recovery image size: 134217728)
#   fastboot erase misc
#   fastboot set_active a
#   fastboot reboot

# Power one the device while holding `Volume Up` + `Power` until the `POCO` logo appeads
# Select: Factory reset
# Select: Format data / Factory reset
# Select: Format data
# Return to main menu
# Apply Update
# Apply update from adb
adb sideload e-3.2-a15-20251023539368-community-surya.zip
# Select Reboot system now
```


## Install Linage OS 22

[Official page](https://wiki.lineageos.org/devices/surya/) with all information and instructions.

```bash
mkdir linageos
cd linageos
# ref: https://download.lineageos.org/devices/surya/builds
# Download mandatory files
wget https://mirrorbits.lineageos.org/full/surya/20251201/lineage-22.2-20251201-nightly-surya-signed.zip
wget https://mirrorbits.lineageos.org/full/surya/20251201/boot.img
wget https://mirrorbits.lineageos.org/full/surya/20251201/dtbo.img
wget https://mirrorbits.lineageos.org/full/surya/20251201/recovery.img
wget https://mirrorbits.lineageos.org/full/surya/20251201/super_empty.img
wget https://mirrorbits.lineageos.org/full/surya/20251201/vbmeta.img

# This is the european firmware
# ref: https://wiki.lineageos.org/devices/surya/fw_update/
wget https://bn.d.miui.com/V14.0.5.0.SJGEUXM/miui_SURYAEEAGlobal_V14.0.5.0.SJGEUXM_b6b33a8d86_12.0.zip

# Verify device exists
fastboot device

# Flash recovery
fastboot flash recovery recovery.img
fastboot boot recovery.img
# Select Factory Reset
# Select Format data / Factory reset
# Return to main menu
# Select Apply update
# Select Apply from ADB
adb sideload lineage-22.2-20251201-nightly-surya-signed.zip
# Optionally sideload more zip files
# Select Reboot system now
```

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

## Install older Linageos

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

* [AnxCam](https://sourceforge.net/projects/miuicamerapocox3/files/MIUICameraPocoX3.zip/download)
* [crCdroid 9.1 for poco x3](https://crdroid.net/surya/9)
* [Firmware download for poco x3](https://xiaomifirmwareupdater.com/firmware/surya/)
* [LinageOS 20](lineage-20.0-20230206-recovery-surya.img) - 20230212
* [Magisk](https://github.com/topjohnwu/Magisk/releases)
  * [Saftynet-fix](https://github.com/kdrag0n/safetynet-fix/releases)
* [NikGapps](https://sourceforge.net/projects/nikgapps/files/Releases/NikGapps-T/08-Sep-2022/)
* [OrangeFox download for poco x3](https://sourceforge.net/projects/builds-ardjlon/files/surya/recovery/OrangeFox-Unofficial-surya_FBEv2.zip/download)
* [xiaomi.eu](https://xiaomi.eu/) - Hpyer OS without spyware

