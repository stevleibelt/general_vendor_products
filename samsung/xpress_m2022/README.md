# Samsung xpress M2022 b/w laser printer

## How to install it on an arch linux

* Use the [samsung-unified-driver](https://aur.archlinux.org/packages/samsung-unified-driver/) and install this.
* Afterwards, fire up your cups and install the printer by choosing the driver "Samsung M2020 Series".
* Add your user to the group lp (usermod -a -G lp <user name>).
* `wget "https://raw.githubusercontent.com/stevleibelt/general_vendor_products/master/samsung/xpress_m2022/Samsung_M2020_Series.ppd"`

## How to setup cups on debian

```bash
sudo apt install cups printer-driver-gutenprint
cd /etc/cups/ppd
wget "https://raw.githubusercontent.com/stevleibelt/general_vendor_products/master/samsung/xpress_m2022/Samsung_M2020_Series.ppd"
chmod 0644 Samsung_M2020_Series.ppd
```

### Server

```bash
# check that printer is available via usb
lsusb

# start printing server
sudo systemctl enable cups.socket
sudo systemctl start cups.socket

cd /etc/cups

#### Using the cli to adminstrate the printer

# List available printers
lpinfo -v
# example output
#   direct usb://Samsung/M2020%20Series?serial=AB12C3DE4F56GHI

# Add the printer
# lpadmin -p <string: printer_name> -E -v <string: device_uri>
#   -p: printer name
#   -E: enable the printer and accept printer jobs
#   -v: device uri
#   -m: model driver to use
#       we use >>everywhere<< since we want to configure this for ipp
lpadmin -p PRINTER_NAME -E -v usb://Samsung/M2020%20Series?serial=AB12C3DE4F56GHI

# Set as default printer
lpoptions -d PRINTER_NAME

# Share printer via network
# Enable general printer sharing
cupsctl --share-printers
# Share this printer
lpadmin -p PRINTER_NAME -o printer-is-shared=true

cupsenable PRINTER_NAME
cupsaccept PRINTER_NAME

# Check printer status
lpstat -p
lpstat -t

# Print test file
echo 'This is a test' > my_file.txt
lp -d PRINTER_NAME my_file.txt

#### Using the gui to adminstrate the printer
#   check if >>lpadmin<< is used in >>cups-files.conf<< as >>SystemGroup<<
#   grep SystemGroup cups-files.conf
sudo usermod -a -G lpadmin <your user name>

#To be able to access the webgui from remote
#   search for <Listen> in cupds.conf
#   replace >>Allow @LOCAL<< with >>Allow >>192.168.178.*<<

#make remote accesses easily
cupsctl WebInterface=yes
cupsctl --remote-admin --remote-any
#after you are done
cupsctl --no-remote-admin

#### Optional
#To enable sharing the printer via ipp
sudo systemctl edit cups.socket
#add
#[Socket]
#ListenStream=631
systemctl restart cups.socket
```

### Client

* Remote connection via `http://<ip_address>:631/printers/<printer_name>`
* Used driver: `Generic IPP Everywhere Printer`
* `sudo lpadmin -p <printer_name> -u allow:<user_name>`
