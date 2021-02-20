# howto

* download [mainsailos](https://github.com/raymondh2/MainsailOS/releases)
* `unzip mainsailos-rpi*.zip`
* `sudo dd if=mainsailos-raspios-lite-latest.img of=/dev/<your device>`
* `ssh pi@<ip address of your pi>`, password is `raspberry`
* change default password with `passwd`
* `sudo apt update`
* `sudo apt dist-upgrade`
* `sudo apt autoremove`
* `sudo apt autoclean`
* `sudo reboot`
* `ssh pi@<ip address of your pi>`, password is `raspberry`
* open `http://<ip address of your pi>` in your webbrowser
* navigate to `burger menu` -> `settings`
* update all available packages
* click on the `plus file` button on the left hand side (`Config Files`)
* name it `printer.cfg`
* click on `printer.cfg`
* replace content with [ender 3.cfg](data/printer-creality-ender3-2018.cfg)
* add line `[include mainsail.cfg]`
* click on `save`
* click on `mainsail.cfg`
* replace content with [mainsail.cfg](data/mainsail.cfg)
* click on `restart`

# link

* [3D-Drucker: Weboberfläche und höheres Drucktempo für 30 Euro nachrüsten](https://www.techstage.de/ratgeber/3d-drucker-weboberflache-und-hoheres-drucktempo-fur-30-euro-nachrusten/f7eeby0?wt_mc=ko.red.ho.conrad-nl.2021-02-20.link.link) - 2021-02-19
