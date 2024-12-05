# Samsung Galaxy A5 SM-A500FU

## How to install postmarkos

ref: https://wiki.postmarketos.org/wiki/Samsung_Galaxy_A5_2015_(samsung-a5)

* Install [heimdall](https://glassechidna.com.au/heimdall/)
* Download [lk2nd-msm8916.img](https://github.com/msm8916-mainline/lk2nd/releases/download/19.0/lk2nd-msm8916.img)
* Download [postmarkos](https://postmarketos.org/install/)
* Power off the device
* Hold `Power`+`Volume-Up`+`Home`-Button together until you see the Samsung logo
* Select `Reboot to bootloader`
* `heimdall flash --BOOT lk2nd-msm8916.img`
* `heimdall print-pit` to list the partitions
* `unxz *samsung-a5*.img.xz`
  * You can safely ignore the small *-<device>-*-boot.img.xz file.
* `fastboot flash userdata 20241127-1002-postmarketOS-v24.06-sxmo-de-sway-1.15.0-samsung-a5.img`
* `fastboot erase system`
* `fastboot reboot`

Hints:

* Default login pin is `147147`
* `Volume-Down`+`Power` enters `lk2nd` fastboot mode
* `Volume-Down`+`Home`+`Power` enters `Samsung` download mode

### SXMO gestures

[!Image containing sxmo gestures on the display](sxmo_gestures.jpg)

The default swipe gestures are: 

* 1 finger right-to-left from right edge: Focus next tag/workspace 
* 1 finger left-to-right from left edge: Focus previous tag/workspace 
* 2 fingers right-to-left (anywhere): Move focused application to previous tag/workspace 
* 2 fingers left-to-right (anywhere): Move focused application to next tag/workspace 
* 1 finger top-to-bottom along the left edge (held pressed): Volume down 
* 1 finger bottom-to-top from the top edge: Show the application menu 
* 2 finger bottom-to-top from the top edge: Show the system menu 
* 1 finger top-to-bottom onto the top edge: Close the active menu 
* 1 finger bottom-to-top from the bottom edge: Show virtual keyboard 
* 1 finger top-to-bottom onto the bottom edge: Hide virtual keyboard 
* 2 finger top-to-bottom onto the bottom edge: Close the current active window 
* 3 finger top-to-bottom onto the bottom edge: Kill the current active window 
* 1 finger from bottom-right corner, swiping diagonally: Rotate the screen 
* 1 finger from bottom-left corner, swiping diagonally: Lock the device 
* 1 finger left-to-right along the top edge (held pressed): Increase screen brightness 
* 1 finger right-to-left along the top edge (held pressed): Decrease screen brightness 

There are various default gestures that translate to keypresses for the underlying application, this facilitates navigation in a variety of applications, including terminal-based applications, without needing the virtual keyboard: 

* 1 finger right-to-left onto the left edge: Send Left arrow 
* 1 finger left-to-right onto the right edge: Send Right arrow 
* 1 finger top-to-bottom along the right edge (held pressed): Send Key down (scroll down) 
* 1 finger bottom-to-top along the right edge (held pressed): Send Key up (scroll up) 
* 1 finger right-to-left along the bottom edge: Send Backspace 
* 1 finger left-to-right along the bottom edge: Send Return 

HOOKS: sxmo_hook_lisgdstart.sh (controls how lisgd is started and what the default gestures are), sxmo_hook_inputhandler.sh defines the avarious actions. 

Volume Raise: 
* 1 tap: Launch Main Menu if no app open or Context Menu if app open. 
* 2 taps: Launch Main Menu 
* 3 taps (or hold): Launch Window Management Menu 

Volume Lower: 
* 1 tap: Toggle virtual keyboard 
* 2 taps: Toggle the window manager layout state (between monocle/tile/bstack) 
* 3 taps (or hold): Kill app 

Power button: 
* 1 tap: Transition to next state 
* 2 taps: Transition to state after next state 
* 3 taps (or hold): Launch terminal 

## Links

* [sxmo user guide](https://sxmo.org/docs/user/sxmo.7.html) - 20241204
