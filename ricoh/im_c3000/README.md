# Add Ricoh IM C3000 to a Cups Linux system

## Steps

* Install `cups`, `gutenprint` and `foomatic-db-gutenprint-ppds`
* `sudo systemctl enable cups.socket`
* `sudo systemctl start cups.service`
* Open `http://localhost:631`
* Add new network printer
* As Connection, choose `ipp://<string: ip_address>/ipp`
* As PPD, choose `Ricoh-IM_C3000-PDF-Ricoh.ppd`
* Happy printing

## Links

* [CUPS on arch linux wiki: archlinux.org](https://wiki.archlinux.org/title/CUPS) - 20240730
* [PPD files for Ricoh IM C3000: openprinting.org](https://www.openprinting.org/printer/Ricoh/Ricoh-IM_C3000) - 20240730
