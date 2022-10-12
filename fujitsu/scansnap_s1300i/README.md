# Fujitsu scansnap s1300i

## How to install

```bash
#install sane sane-utils ipp-usb
echo "" >> /etc/sane.d/fujitsu.conf
echo "#ScanSnap s1300i" >> /etc/sane.d/fujitsu.conf
echo "usb 0x04c5 0x1155" >> /etc/sane.d/fujitsu.conf
mkdir -p /usr/share/sane
cd /usr/share/sane
mkdir epjitsu/
cd /usr/share/sane/epjitsu/
wget "https://github.com/stevleibelt/general_vendor_products/blob/master/fujitsu/scansnap_s1300i/1300i_0D12.nal?raw=true" --output-document=1300i_0D12.nal
#on some systems needed
ln -s epjitsu fujistu
systemctl enable saned.socket
systemctl start saned.socket
systemctl enable ipp-usb.servce
systemctl start ipp-usb.servce
#use >>sane-find-scanner<<
#list know scanners >>scanimage --list-devices<<
* use simple-scan, sane or xsane
* vim /etc/sane.d/epjitsu.conf #if needed
```

## Share scanner over the network

```
echo "localhost" >> /etc/sane.d/saned.conf
echo "192.168.178.0/24" >> /etc/sane.d/saned.conf
```

# Links

* [debian scanner wiki page](https://wiki.debian.org/Scanner) - 20220902
* [sane project - fujistu vendor](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-FUJITSU) - 20220902
* https://github.com/ckunte/scansnap-firmware
* http://www.documentsnap.com/fujitsu-scansnap-in-linux/
* http://www.fujitsu.com/global/support/products/computing/peripheral/scanners/scansnap/manuals/s1300i.html
* http://www.fujitsu.com/global/support/products/computing/peripheral/scanners/scansnap/software/s1300i.html
