# f8 fc - Open source brushed x8 AIO

![PCB](/ardupilot/pcb.jpg)

[f8 fc](https://github.com/victorhook/f8-fc) is a fully open source AIO flight controller that is made primarily for small drones with brushed drones. It features:
- STM32F405 microcontroller with 1MB flash
- BMI270 imu
- BMP388 barometer
- Onboard 16MB external flash for data logging
- Status LEDs
- 1-4s input voltage
- 4 available UARTs
- **8** brushed motor drives with 6A mosfets
- Voltage & current sensing
- Runs ardupilot

## How to flash Ardupilot
1. Get ardupilot toolchain and put the `hwdef.dat` and `hwdef_bl.dat` in `ardupilot/libraries/AP_HAL_ChibiOS/hwdef/f8-fc/`
2. Build bootloader
```
./waf clean
./waf configure --board f8-fc --bootloader
./waf bootloader
```
3. Flash bootloader using something like STM32CubeProgrammer. Hold boot button when powering on the board to boot in DFU mode.
4. Build firmware and upload using the bootloader (have board plugged in to USB and ensure you get a new serial port)
```
./waf configure --board f8-fc
./waf copter --upload
```
