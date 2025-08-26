# stm32-inator
<img src="images/header-render.png"  width="1200">

In the search for better performance, I moved from RP2040 (`125mhz`) to STM32F405 (`168mhz`).  Getting familiar with STM32 also allows me to move to H723 in future (`550mhz`).

This board has been submitted for production at JLC (PCBA), but not tested yet.

# Features
- STM32F405RGTx w. crystal & 128mb external flash via SPI
- FFC connections (mostly), using 12-pin 0.5mm pitch cables
- Remote-mount USB ports (e.g. [this](https://www.aliexpress.com/item/1005005997783735.html))
  - rather than on-board, I wanted to position the USB/split ports in specific places
  - JLC PCBA charges ~C$6 per usb port (per board...), and I've had soldering issues w. those components before
  - I don't have a USB-C source, and I'm not selling this, so...whatever...
  - note that the remote-port needs to have 5.1k pull-down resistors on the CC lines to function on a USB-C host port
- WS2812 signal conversion to 5v
- DFU button to enter DFU mode for flashing
- Designed w. QMK in mind
- ROW2COL diode alignment
- Diode arrays which were very painful to route traces for, but did save a lot of space
- Solder-pads
  - QMK handedness
  - VBUS power safety bypass (_ESD, polyfuse, diode, etc_)
  - LCD & RGB power enable
- Designed for Arcboard-mk20; 12-pin 0.5mm FPC using Vik footprints
  - 4x dpad outputs (5rows, 1col, DI/DO, 5v/gnd)
  - 3x encoders outputs (encoder A/B, 3.3v/gnd)
  - 1x SPI PMW output (usual)
  - 1x SPI LCD output (usual)
  - 1x 25-pin Cyboard connector (0.3mm FPC connector for [Cyboard](https://www.cyboard.digital/product-page/dactyl-flex-pcbs) connectivity (or via [this](https://github.com/christrotter/mk19-flex-pcb)))
- Breakout
  - Main USB & Split/serial via 2.54mm 4-pin header (I left room for a horizontal JST-XH socket)
  - RGB data output via 2.54mm 3-pin header
  - Reset, boot pins via 1.00mm 4-pin header
  - 5 spare pins via 1.00mm 2-pin and 3-pin headers
  - Debug pins via 1.00mm 4-pin header
- Dimensions
  - 51.55mm hole spacing (square)
  - 59.5x59.7mm actual board size

<img src="images/header-render-front.png"  width="1200">

# BOM
|Designator                                  |Footprint                              |Quantity|Value               |LCSC Part #|
|--------------------------------------------|---------------------------------------|--------|--------------------|-----------|
|C1, C10, C20                                |0805                                   |3       |4.7uF               |C1779      |
|C11, C12, C14, C17, C18, C19, C5, C7, C8, C9|0402                                   |10      |100nF               |C1525      |
|C13, C15, C27                               |0402                                   |3       |1uF                 |C52923     |
|C2, C4                                      |0402                                   |2       |2.2uF               |C12530     |
|C22                                         |C0603                                  |1       |CL10A106MA8NRNC     |C96446     |
|C3, C6                                      |0402                                   |2       |12p                 |C1547      |
|CYBOARD-MAIN1                               |FPC-SMD_ECT818001569                   |1       |ECT818001569        |C711420    |
|D2                                          |D_SOD-323                              |1       |B5817               |C123899    |
|D4                                          |SOD-123FL_L2.8-W1.8-LS3.7-BI           |1       |SMF5_0CA_C364279    |C364279    |
|D5, D7                                      |SOT-666-6_L1.6-W1.2-P0.50-LS1.6-BL     |2       |USBLC6-2P6_C2827693 |C2827693   |
|F1                                          |F1206                                  |1       |Polyfuse            |C2892424   |
|F3                                          |F1206                                  |1       |MF-NSMF075-2        |C89653     |
|J13, J14, J15, J16, J3, J4, J6, J7, J8      |FFC-SMD_FFC05001-12SBA124W5M           |9       |FFC05001-12SBA124W5M|C2833760   |
|L1                                          |L0805                                  |1       |MPZ2012S101AT000    |C15957     |
|LED-LVL1                                    |SOT-563_L1.6-W1.2-P0.50-LS1.6-BR       |1       |SN74LVC1T45DRL      |C352970    |
|MOSFET1, MOSFET2, MOSFET3                   |SOT-23_L2.9-W1.3-P1.90-LS2.4-BR        |3       |AO3401A             |C15127     |
|R1                                          |0402                                   |1       |0402WGF1004TCE      |C26083     |
|R10                                         |0402                                   |1       |5.1k                |C25905     |
|R11, R12, R16, R2, R3, R7, R8               |0402                                   |7       |10k                 |C25744     |
|R14                                         |0402                                   |1       |0402WGF1000TCE      |C25076     |
|R15                                         |0402                                   |1       |0402WGF1001TCE      |C11702     |
|R6                                          |R0603                                  |1       |0603WAF3303T5E      |C23137     |
|R9                                          |0402                                   |1       |0402WGF1003TCE      |C25741     |
|U1                                          |SOT-23-5                               |1       |XC6210B332MR-G      |C82942     |
|U10                                         |SOD-123F_L2.7-W1.6-LS3.8-RD            |1       |1N4148W_C81598      |C81598     |
|U13, U4                                     |SOT-23-3_L2.9-W1.3-P1.90-LS2.4-BR      |2       |2N7002              |C8545      |
|U14                                         |SOIC-8_L5.3-W5.3-P1.27-LS8.0-BL        |1       |W25Q128JVSIQTR      |C97521     |
|U15                                         |SW-SMD_4P-L5.1-W5.1-P3.70-LS6.5-TL_H1.5|1       |TS-1187A-B-A-B      |C318884    |
|U3                                          |LQFP-64_10x10mm_P0.5mm                 |1       |STM32F405RGTx       |C15742     |
|U5, U6, U7, U8, U9                          |SOT-363-6_L2.0-W1.3-P0.65-LS2.1-BL     |5       |BAV70S,115          |C455031    |
|Y1                                          |CRYSTAL-SMD_4P-L3.2-W2.5-BL-1          |1       |Crystal_GND24       |C518154    |

# Layout
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

# Links
[Datasheet for STM32F405](https://www.st.com/resource/en/datasheet/dm00037051.pdf)
[Great article on STM32 DFU circuit](https://acheronproject.com/reset_article_1/reset_article_1/)
[Great article on USB-C CC lines](https://hackaday.com/2023/01/04/all-about-usb-c-resistors-and-emarkers/)
[TI pdf on USB-C power](https://www.ti.com/lit/wp/slyy109b/slyy109b.pdf)
[USB and Type-C demystified](https://www.st.com/content/dam/AME/2019/technology-tour-2019/chicago/presentations/T1S3_Schaumburg_USB-Type-C_G.Gosciniak.pdf)
[SPI flash on STM32](https://mischianti.org/stm32-add-spi-flash-memory-with-fat-fs/)
