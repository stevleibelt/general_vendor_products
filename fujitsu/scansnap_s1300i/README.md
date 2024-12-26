# Fujitsu scansnap s1300i

## How to install

```bash
# install
apt install sane-airscan sane-utils ipp-usb
#   only for graphical frontend
# apt install sane

#find your scanner
sane-find-scanner
# example output
#   found USB scanner (vendor=0x04c5 [FUJITSU], product=0x128d [ScanSnap S1300i]) at libusb:001:004
cat >> /etc/sane.d/fujitsu.conf <<DELIM
# [FUJITSU], [ScanSnap S1300i]
# <connection-type> <vendor-id> <device-id>
usb 0x04c5 0x128d
DELIM
mkdir -p /usr/share/sane/epjitsu
cd /usr/share/sane/epjitsu/
wget "https://github.com/stevleibelt/general_vendor_products/blob/master/fujitsu/scansnap_s1300i/1300i_0D12.nal?raw=true" --output-document=1300i_0D12.nal
#on some systems needed
ln -s epjitsu fujistu
systemctl enable saned.socket
systemctl start saned.socket
systemctl enable ipp-usb.service
systemctl start ipp-usb.service
#list know scanners >>scanimage --list-devices<<
* use simple-scan, sane or xsane
```

* vim /etc/sane.d/epjitsu.conf #if needed
* echo "#my_local_scanner" >> /etc/sane.d/net.conf
* echo "<string: ip_of_your_local_scanner>" >> /etc/sane.d/net.conf

## Share scanner over the network

```bash
#required
echo "localhost" >> /etc/sane.d/saned.conf
#allow local subnet
echo "192.168.178.0/24" >> /etc/sane.d/saned.conf
```

## Links

* [debian scanner wiki page](https://wiki.debian.org/Scanner) - 20220902
* [sane project - fujistu vendor](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-FUJITSU) - 20220902
* https://github.com/ckunte/scansnap-firmware
* http://www.documentsnap.com/fujitsu-scansnap-in-linux/
* http://www.fujitsu.com/global/support/products/computing/peripheral/scanners/scansnap/manuals/s1300i.html
* http://www.fujitsu.com/global/support/products/computing/peripheral/scanners/scansnap/software/s1300i.html
