# arcboard-stm32
In the search for better performance, I moved from RP2040 (125mhz) to STM32F405 (168mhz).  Getting familiar with STM32 also allows me to move to H723 in future (550mhz).

# Features
- STM32F405RGTx w. crystal & 128mb external flash via SPI
- only(mostly) FFC connections, using 12-pin 0.5mm pitch cables
- remote-mount USB ports
- WS2812 signal conversion to 5v
- DFU button to enter DFU mode for flashing
- Solder-pads
  - QMK handedness
  - VBUS power safety bypass (_ESD, polyfuse, diode, etc_)
  - LCD power
  - RGB power
- support for Arcboard-mk20
  - 4x dpad outputs
  - 3x encoders outputs
  - 1x SPI PMW output
  - 1x SPI LCD output
  - 1x 25-pin Cyboard connector
- headers
  - Split/serial via 4-pin
  - Main USB via 4-pin header
  - RGB data output via 3-pin header
  - Reset, boot pins via 4-pin header
  - 5 spare pins via 2-pin and 3-pin headers
  - debug pins via 4-pin header
- Dimensions:
  - 51.55mm hole spacing (square)
  - 59.5x59.7mm

# Render
<img src="images/pcb-render-front.png"  width="600">
<img src="images/pcb-render-back.png"  width="600">

# PCB overview
<img src="images/pcb-overview.png"  width="600">

# Schematic
<img src="images/schematic-overview.png"  width="1200">

<img src="images/schematic-mcu.png"  width="600">

<img src="images/schematic-power-usb.png"  width="600">

<img src="images/schematic-encoders.png"  width="600">

<img src="images/schematic-rgb.png"  width="600">

<img src="images/schematic-row2col.png"  width="600">

<img src="images/schematic-spi-devices.png"  width="600">

<img src="images/schematic-other.png"  width="600">
