# Epson perfection v39

## Installation for debian or ubuntu

* Download the deb 64 bit package from the [official epson linux scanner driver download](https://support.epson.net/linux/en/epsonscan2.php) page.

```bash
# install mandatory epson firmware
tar xzf epsonscan2-bundle-6.7.70.0.x86_64.deb.tar.gz
sudo dpkg -i core/*.deb
sudo dpkg -i plugins/*.deb

# install sane software
sudo apt install sane simple-scan
```

# Links

* [arch linux wiki about epson sane problems](https://wiki.archlinux.org/title/SANE/Scanner-specific_problems#Epson)
  * [arch linux forum usinc firmware for iscan](https://bbs.archlinux.org/viewtopic.php?pid=2074344#p2074344)
