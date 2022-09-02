# Samsung xpress M2022 b/w laser printer

## How to install it on an arch linux

* Use the [samsung-unified-driver](https://aur.archlinux.org/packages/samsung-unified-driver/) and install this.
* Afterwards, fire up your cups and install the printer by choosing the driver "Samsung M2020 Series".
* Add your user to the group lp (usermod -a -G lp <user name>).
* `wget "https://raw.githubusercontent.com/stevleibelt/general_vendor_products/master/samsung/xpress_m2022/Samsung_M2020_Series.ppd"`

## How to setup cups on debian

```bash
sudo apt install cups printer-driver-gutenprint
```

## General

### Server

```bash
sudo systemctl enable cups.socket
sudo systemctl start cups.socket

#We are working in the path >>/etc/cupsd<<
####
#to be able to add a printer from the gui
#check if >>lpadmin<< is used in >>cups-files.conf<< as >>SystemGroup<<
#   cat cups-files.conf | grep SystemGroup
sudo usermod -a -G lpadmin <your user name>

#to be able to access the webgui from remote
#search for <Listen> in cupds.conf
#replace >>Allow @LOCAL<< with >>Allow >>192.168.178.*<<

#make remote accesses easily
cupsctl WebInterface=yes
cupsctl --remote-admin --remote-any
#after you are done
cupsctl --no-remote-admin

#to be able to share the printer via ipp
sudo systemcl edit cups.socket
#add
#[Socket]
#ListenStream=631
systemctl restart cups.socket
```

### Client

* Remote connection via `http://<ip_address>:631/printers/<printer_name>`
* Used driver: `Generic IPP Everywhere Printer`
* `sudo lpadmin -p <printer_name> -u allow:<user_name>`

