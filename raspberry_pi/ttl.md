# Running Raspberry Pi with usb to serial TTL

## Example based on a PL2303 and a Raspberry Pi Model 1

```
#connection
GPIO P01-2 -> Red (+5V)
GPIO P01-6 -> Black (0V)
GPIO P01-8 -> White (RX)
GPIO P01-10 -> Green (TX) 
```

```
screen /dev/ttyUSB0 115200
```

# links

* http://raspberry.tips/raspberrypi-tutorials/raspberry-pi-konsolenkabel-verwenden-usb-serial
* https://raspberrypi-aa.github.io/session1/connecting.html
* http://villagescience.org/wp-content/uploads/2014/03/RPi_GPIOs.png
