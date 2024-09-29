# ender5plus-klipper-mercuryone
Klipper configurations for Ender 5 Plus with MKS Robin Nano v3 and the Mercury One CoreXY mod.

# Future changes
* Install Rapido UHF hotend<br>
https://trianglelab.net/products/rapido-hotend-20?VariantsId=11312
* Install filament runout detector direct on the orbiter extruder<br>
https://trianglelab.net/products/orbiter-v2-filament-sensor?VariantsId=10610
* Hydra 3-point bed mod
  * https://docs.zerog.one/manual/build/hydra/introduction
  * second MCU instead of replacing the main board with one that has more stepper drivers

# References

## Hardware I Used

| **Item**         | **Name**                | **Link**                                                                          | **Note** |
|-|-|-|-|
| **Base Printer** | Ender 5 Plus| https://www.creality.com/products/ender-5-plus-3d-printer||
| **CoreXY Mod**   | Mercury One Zero G| https://docs.zerog.one/||
| **Mainboard**    | MKS Robin Nano V3.1| https://github.com/makerbase-mks/MKS-Robin-Nano-V3|          |
| **Probe**| BTT Microprobe| https://github.com/bigtreetech/MicroProbe||
| **Hotend**| Triangle Lab Rapido HF| https://trianglelab.net/products/rapido-hotend?VariantsId=10027| Changing to Rapido UHF|
| **Extruder**| Triangle Lab Orbiter v2 | https://trianglelab.net/products/orbiter-extruder-v20%EF%BC%88black-gear%EF%BC%89 ||
| **Filament Sensor** | BTT Smart Filament Sensor | https://github.com/bigtreetech/smart-filament-detection-module | Changing to Orbiter detector|
| **E34M1**|EVA3 for Mercury One| https://jon-harper.github.io/E34M1/||
| **stepper motors**|Mercury One BOM|https://www.omc-stepperonline.com/e-series-nema-17-bipolar-55ncm-77-88oz-in-2a-42x48mm-4-wires-w-1m-cable-connector-17he19-2004s||

## My Contribution
STL file: Mount the BTT Microprobe on the E34M1 head (uses M3 bolts and nuts)

## Software / Documentation
| **Name**                | **Link**                                                                          | **Note** |
|-------------------------|-----------------------------------------------------------------------------------|----------|
| **KIAUH** | https://github.com/dw-0/kiauh?tab=readme-ov-file||
| **TMC Autotuning** | https://github.com/andrewmcgr/klipper_tmc_autotuneGuide** ||
| **Ellis' Tuning Guide** | https://ellis3dp.com/Print-Tuning-Guide/||
| **Ellis' TEST_SPEED macro** | https://github.com/AndrewEllis93/Print-Tuning-Guide/blob/main/macros/TEST_SPEED.cfg  ||

# Custom configuration changes
Using the MKS Robin Nano's unused second extruder ports.

## Dual Z
The "hotend 1" stepper driver is being used for stepper_z1. Z_TILT_ADJUST requires that the stepper motors be connected a specific way.<br><br>With origin at the front-left corner:
* Connect the first/original stepper_z driver to the left-hand stepper motor.
* Connect the second/hotend1 stepper_z1 driver to the right-hand stepper motor.

## Fans
The Ender 5 Plus has three fans - hotend, part cooling, and controller. None of them are "always-on."

| **Connector**|**MCU Pin**| **Device** |
|------------------|-------------------------|----|
| FAN1 | PC14 | controller/case fan
| FAN2 | PB1 | hotend fan
| HE1 | PB0 | part cooling fan(s)
  
