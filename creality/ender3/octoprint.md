# klipper

[source - 3dprintbeginner.com](https://3dprintbeginner.com/install-klipper-on-ender-3/) - 20190806
[source - klipper3d.org](https://www.klipper3d.org/Installation.html)
[upgrade octopi to python3](https://octoprint.org/blog/2020/09/10/upgrade-to-py3/)

```
#bo: install klipper source code
cd ~
mkdir klipper
cd klipper
git clone https://github.com/KevinOConnor/klipper .

bash scripts/install-octopi.sh

/home/pi/klippy-env/bin/python2 -m pip install --upgrade pip
#eo: install klipper source code

#bo: configure and compile code
make menuconfig
#select: Micro-controller Architecture: Atmega AVR
#select: Processor model: atmega1284p
#select: Processor Speed: 16Mhz
#exit

make
#eo: configure and compile code

#bo: flash build
sudo service klipper stop
#find usb port for printer
ls /dev/serial/by-id/*
#replace <your port> with the output of previous command
make flash FLASH_DEVICE=/dev/serial/by-id/usb-<your port>
#should end with "Thank you"
#eo: flash build

#bo: configure octoprint
sudo service klipper start
cp ~/klipper/config/example.cfg ~/printer.cfg
#go to the Octoprint web ui main screen
#open configuration
#   Serial Connection -> General -> Additional Serial Port
#       add: /tmp/printer
#   Serial Connection -> General -> Serial Port
#       select: /tmp/printer
#   Serial Connection -> General -> Baudrate
#       insert: 250000
#   Serial Connection -> Behaviour -> Baudrate
#       select: Cancel any ongoing prints but stay connected to the printer
#   click on save
#go to the Octoprint web ui main screen
#   try to connect the printer
#go to the Octoprint web ui main screen
#open configuration
#   Plugin Manager -> Get more -> ... from URL: `https://github.com/KevinOConnor/klipper`
#   click on install
#go to the Octoprint web ui main screen
#open configuration
#   OctoKlipper -> Klipper Configuration
#   add configuration from ## OctoKlipper Configuration
#   click on save
#reboot printer and octoprint
#eo: configure octoprint
```

## OctoKlipper Configuration
* search in the following code block for `[mcu]` and replace `<your port>` with the output of `ls /dev/serial/by-id/*`

```
# This file contains common pin mappings for the 2018 Creality
# Ender 3. To use this config, the firmware should be compiled for the
# AVR atmega1284p.

# Note, a number of Melzi boards are shipped with a bootloader that
# requires the following command to flash the board:
#  avrdude -p atmega1284p -c arduino -b 57600 -P /dev/ttyUSB0 -U out/klipper.elf.hex
# If the above command does not work and "make flash" does not work
# then one may need to flash a bootloader to the board - see the
# Klipper docs/Bootloaders.md file for more information.

# See the example.cfg file for a description of available parameters.

[bltouch]
sensor_pin: ^PC4
control_pin: PA4
pin_move_time: 0.500
pin_up_reports_not_triggered: True
pin_up_touch_mode_reports_triggered: False
x_offset: +48 
y_offset: -2
#z_offset: -1
speed: 2

[force_move]
enable_force_move: True

[homing_override]
gcode: SET_KINEMATIC_POSITION Z=0
 G0 Z10 F500
 G28 X Y
 G0 X0 Y10 F5000
 G28 Z
 G0 Z10 F500
axes: z
set_position_z: -5

[bed_mesh]
horizontal_move_z: 10
min_point: 0,10
max_point: 175,225
probe_count: 4,4

[stepper_x]
step_pin: PD7
dir_pin: !PC5
enable_pin: !PD6
step_distance: .0125
endstop_pin: ^PC2
position_endstop: 0
position_max: 235
homing_speed: 50

[stepper_y]
step_pin: PC6
dir_pin: !PC7
enable_pin: !PD6
step_distance: .0125
endstop_pin: ^PC3
position_endstop: 0
position_max: 235
homing_speed: 50

[stepper_z]
step_pin: PB3
dir_pin: PB2
enable_pin: !PA5
step_distance: .0025
endstop_pin: probe:z_virtual_endstop
position_endstop: 0.0
position_min: -5
position_max: 250

[extruder]
max_extrude_only_distance: 100.0
step_pin: PB1
dir_pin: !PB0
enable_pin: !PD6
step_distance: 0.010526
nozzle_diameter: 0.400
filament_diameter: 1.750
heater_pin: PD5
sensor_type: EPCOS 100K B57560G104F
sensor_pin: PA7
control: pid
pid_Kp: 21.548
pid_Ki: 0.921
pid_Kd: 126.059
min_temp: 0
max_temp: 260
pressure_advance: 0.6
pressure_advance_lookahead_time=0.075

[heater_bed]
heater_pin: PD4
sensor_type: EPCOS 100K B57560G104F
sensor_pin: PA6
control: pid
pid_Kp: 54.027
pid_Ki: 0.770
pid_Kd: 948.182
min_temp: 0
max_temp: 130

[fan]
pin: PB4

[mcu]
serial: /dev/serial/by-id/usb-<your port>

[printer]
kinematics: cartesian
max_velocity: 300
max_accel: 3000
max_z_velocity: 5 
max_z_accel: 100
square_corner_velocity: 5.0

[display]
lcd_type: st7920
cs_pin: PA3
sclk_pin: PA1
sid_pin: PC1
encoder_pins: ^PD2, ^PD3
click_pin: ^!PC0

#*# <---------------------- SAVE_CONFIG ---------------------->
#*# DO NOT EDIT THIS BLOCK OR BELOW. The contents are auto-generated.
#*#
#*# [bed_mesh default]
#*# points =
#*# 	-0.007500, 0.295000, 0.437500, 0.707500
#*# 	0.500000, 0.537500, 0.570000, 0.677500
#*# 	0.577500, 0.697500, 0.765000, 0.765000
#*# 	0.860000, 1.075000, 1.127500, 1.095000
#*# x_count = 4
#*# y_count = 4
#*# min_x = 0.0
#*# max_x = 174.99
#*# min_y = 10.0
#*# max_y = 224.98
#*# x_offset = 48.0
#*# y_offset = -2.0
#*# mesh_x_pps = 2
#*# mesh_y_pps = 2
#*# algo = lagrange
#*# tension = 0.2
#*#
#*# [bltouch]
#*# z_offset = 1.600
```
