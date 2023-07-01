# Nintendo Wii U

## How to homebrew

### Prepare the sd card
* Insert SD Card to your pc
* Extract [zip](bin/environmentloader-c451287+wiiu-nanddumper-payload-5c5ec09+fw_img_loader-c2da326+payloadloaderinstaller-98367a9+tiramisu-41104c4.zip) to the root of your sd card
* Copy the [01_sigpatches.rpx](bin/01_sigpatches.rpx) to your sd card in the path `wiiu/environments/tiramisu/modules/setup`
* Unplug the SD card from your computer

### Launch the exploit

* Plug the sd card in the wii u
* Launch the internet browser
* Open the webpage `wiiuexploit.xyz`
* Click on `Run Exploit!`
* Hold the `B` Button until you see the menu

## Backup your NAND

* Navigate to `nanddumper`
* Press `A`
  * Dump SLC: `yes`
  * Dump SLCCMPT: `yes`
  * Dump MLC: `optional`
  * Dump OTP: `yes`
  * Dump SEEPROM: `yes`
* Press `A`
* When the process is done
  * Power of your Wii u
  * Unplug the SD Card
  * Plug the SD Card into your pc
  * Copy the following files to a save place `slc.bin`, `slccmpt.bin`, `otp.bin` and optional `mlc.bin.*`
  * Delete the files from your sd card

## Install the PayloadLoader

* [Lunch the exploid](#lunch-the-exploit)
* Navigate to `installer`
* Press `A`
* Select `default`
* Press `A` to select `Install `
* Press `A`
* Select `Check`
* Press `A`
* Select `Install / Update`
* Press `A`
* Select `Install`
* Press `A`
* Press `A` to shut down the console

## Manually boot into tiramisu

* Boot the Wii U
* Launch the "Health and Safety Information App"
* Select `tiramisu`
* Press `A`

## Autobooting Tiramisu

* Start the console
* Launch the "Health and Safety Information App" and hold the `X` Button
* Select `installer`
* Press `A`
* Select `Check`
* Select `Boot options`
* Press `A` to select `Switch to PayloaderLoader`
* Press `A` to shut down the console

## Change back autobooting to normal

* Start the console and Press `+` (start)
* Navigate to the title you want to autoboot
* Press `Y`
* Press `A` to launch the selected title

## Block Updates

## Finalize the setup

* Read [this](https://wiiu.hacks.guide/#/tiramisu/finalizing-setup) to finalize your setup

## Usefull applications

* `Wii U Usb helper` for games
* `WUP installer` to installgames on your wii up
* `NUSpli` (Channel zip)

## Links

* [How to homebrew a wii u](https://wiiu.hacks.guide/#/tiramisu/sd-preparation)
* [How to install Tiramisu](https://wiiu.hacks.guide/#/tiramisu/sd-preparation)
  * [Buy the developer of Tiramisu a coffee](https://ko-fi.com/maschell)
  * [Sponsore the developer of Tiramisu via github](https://github.com/sponsors/Maschell)
* [Developer of the WiiU Sigpatches](https://github.com/marco-calautti/SigpatchesModuleWiiU/releases)
* [How to block wii u updates](https://wiiu.hacks.guide/#/block-updates)
* [NUSpli](https://github.com/V10lator/NUSspli/releases)
* [Aroma](https://wiidatabase.de/wii-u-downloads/hacks/aroma/) - Is the new "gold standard" and should be used instead of tiramisu - 20230402

