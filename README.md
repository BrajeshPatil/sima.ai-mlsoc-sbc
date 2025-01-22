# sima.ai_mlsoc_sbc
The Single Board Computer designed using the SiMa.ai MLSoC is a part of a project that I did under ARTPARK. The SBC was designed in order to run computationally heavy softwares such as SLAM, VIO and Autonomous Guidance Systems. The SiMa.ai MLSoC which is a state-of-the-art ML-based SOC was selected.

This repository provides the design files for only the hardware part of the project.

# Hardware Architecture
![Hardware Layout](https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/Hardware_Layout.png)

Features of the SBC:
1. SiMa.ai MLSoC provides 4 Ethernet Chipsets. Only 1 of these chipsets have been used in our SBC. The Ethernet PHY IC DP83867EIS has been used for implementing the physical layer for Communication. RJ45 Connectors with internal magnetic isolation have been used.
2. 5 UART Controllers have been used for working of the following sub-systems:
    - UART0 Controller has been used for functioning of the WiFi Module.
    - UART1 Controller has been used for functioning of A9G AI Thinker GSM and GPRS module.
    - Linux Boot functionality is provided by using UART2 and Troot Boot has been implemented using UARTB. These are also connected to FTDI chip so that the SBC can be booted using a Type C Cable.
    - UART3 currently doesn't have any functionality but has been made accessible. It can be used to communicate with an external UART device.
    - UART0, UART1 and UART3 have been connected to external I2C connectors.  
3. The SoC contains 32 GPIO pins. They are implemented as follows:
    - GPIO Pins 21, 22 and 23 have been used in the WiFi Module. As the WiFi Module works on 3.3V voltage level, a (1.8V to 3.3V) voltage translator has been used.
    - GPIO Pins 0 - 7 have been translated to 3.3V and have been provided externally.
    - GPIO Pins 9 - 16 have been translated to 5V and have been provided externally.
    - GPIO Pins 19, 20 have been used for functioning of the Ethernet PHY IC.
4.  DRAM (Dynamic Random-Access Memory) is fast, temporary storage that holds data while a computer runs, but it loses information when powered off. It stores data in capacitors that require periodic refreshing, using operations like activate, read/write, precharge, and refresh to manage access and integrity. 4x 32-bit LPDDR4 chipsets with P/N MT53E1G32D2FW-046 IT:B from Micron is mounted on the MLSoC Evaluation Board. The operating frequency of the LPDDR4 chip is 1866MHz.
5. The SBC can be powered through two ways, i) USB Type C and ii) XT-60 Connector.
    - The TPS548D22 IC is used to generate 0.85V Core Voltage.
    - SiC437DED used for generating 1.8V and 1.1V.
    - The PMIC Switching Regulator is used to generate 3.3V, 1.8V, 2.5V and 4.2V.
6. The SoC contains 3 SPI controllers.
    - 1 SPI controller has been provided externally.
    - The other 2 SPI chipsets have been used to implement a QSPI Flash Memory using a MUX and a DEMUX. 
7. The 2 I2C Controllers have been provided on the SBC. These can be used for interfacing with sensors, storage devices, displays or any device working on I2C Protocol.
8. The eMMC interface includes a clock (CLK), command (CMD), and an 8-bit data bus (D0-D7), with separate power pins for core (VCC), I/O (VCCQ), and stabilization (VDDI). It also features DS for HS-400 mode, card detect (CRD DET N), and write protect (CRD WR PROT) functionality.
9. The MLSoCsupports SD3.0 controller interface for loading the boot files from an external SD card. A Micro-SD Push-Push connector with P/N 693071020811 is used for interfacing the external SD card with the MLSoC Evaluation Board.
10. JTAG Test functionality has been provided by providing access to them through a 2x14 Pin Shrouded Connector.
11. The GPS and GSM functionalities for tracking the vehicle's location and enabling SMS communication have been implemented using the A9G Ai-Thinker module. The clock and reset circuitry has also been employed. 

# File structure
 
The repository contains directories for all sub-sections of the hardware layout.

# Contributors
- [Karteek Nayak](https://github.com/Karteek-N)
- [Brajesh Patil](https://github.com/BrajeshPatil)
