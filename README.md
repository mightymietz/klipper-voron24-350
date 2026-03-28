# klipper-voron24-350

### Update

# stop klipper
systemctl stop klipper.service

## Update EBB36

# build klipper
cd ~/klipper
make menuconfig

[*] Enable extra low-level configuration options
    Micro-controller Architecture (STMicroelectronics STM32)  --->
    Processor model (STM32G0B1)  --->
    Bootloader offset (8KiB bootloader)  --->
    Clock Reference (8 MHz crystal)  --->
    Communication interface (CAN bus (on PB0/PB1))  --->
(1000000) CAN bus speed
()  GPIO pins to set at micro-controller startup

# flash klipper
 ~/klippy-env/bin/python3 ~/katapult/scripts/flash_can.py -i can0 -f ~/klipper/out/klipper.bin -u 9e1d04953b6c


## Update Kraken

# build klipper
cd ~/klipper
make menuconfig

* [*] Enable extra low-level configuration options
* Micro-controller Architecture (STMicroelectronics STM32) --->
* Processor model (STM32H723) --->
* Bootloader offset (128KiB bootloader (SKR SE BX v2.0)) --->
* Clock Reference (25 MHz crystal) --->
USB Interface
* Communication interface (USB (on PA11/PA12)) --->
CANBUS Interface
* Communication interface (CAN bus (on PD0/PD1)) --->

# flash klipper
~/klippy-env/bin/python3 ~/katapult/scripts/flash_can.py -i can0 -f ~/klipper/out/klipper.bin -u 49c000c1c373

# start klipper
systemctl start klipper.service

Reference
https://canbus.esoterical.online/mainboard_flashing.html#stm32-based-boards