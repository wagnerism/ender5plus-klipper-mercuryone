# ender5plus-klipper-mercuryone
Klipper configurations for Ender 5 Plus with MKS Robin Nano v3 and the Mercury One CoreXY mod.

# References - What I used
Hardware:
* Ender 5 Plus https://www.creality.com/products/ender-5-plus-3d-printer
* Mercury One CoreXY mod https://docs.zerog.one/
* MKS Robin Nano V3.1 motherboard https://github.com/makerbase-mks/MKS-Robin-Nano-V3.X
* BTT Microprobe https://github.com/bigtreetech/MicroProbe
* E34M1 - EVA3 for Mercury One - Toolhead https://jon-harper.github.io/E34M1/
* 17he19-2004s stepper motors are from the Mercury One BOM
https://www.omc-stepperonline.com/e-series-nema-17-bipolar-55ncm-77-88oz-in-2a-42x48mm-4-wires-w-1m-cable-connector-17he19-2004s

Software and docs:
* TMC Autotuning https://github.com/andrewmcgr/klipper_tmc_autotune
* Ellis' Print Tuning Guide https://ellis3dp.com/Print-Tuning-Guide/
* Ellis' TEST_SPEED macro https://github.com/AndrewEllis93/Print-Tuning-Guide/blob/main/macros/TEST_SPEED.cfg

# Customized configuration changes

## Dual Z
The MKS Robin Nano v3 has a stepper driver for the "hotend 1" extruder that is being used for stepper_z1.<br>
The connections to stepper_z and stepper_z1 matter for Z_TILT_ADJUST.  With origin at the front-left corner:
* Connect the first/original stepper_z driver to the left-hand stepper motor.
* Connect the second/hotend1 stepper_z1 driver to the right-hand stepper motor.

## Fans
The Ender 5 Plus has three fans - hotend, part cooling, and controller.<br>
The MKS Robin Nano has two fan outputs of which only one is hardware PWM. The configuration provided with klipper assigns the 
hardware PWM fan to the hotend fan, not the part cooling fan that can benefit from varying speeds.

Here is the fan configuration:
* \[fan\] print cooling fan
  * "fan2" connector
  * pin PB1
  * has PWM control
* \[heater_fan\] hotend fan
  * "fan1" connector
  * pin PC14
  * no PWM control
* \[controller_fan\] fan in the enclosure
  * "HE1" hotend 1 heater connector
  * pin PB0
  * has PWM control but is not needed
