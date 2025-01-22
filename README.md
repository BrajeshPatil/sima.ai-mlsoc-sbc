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
4. The SBC can be powered through two ways, i) USB Type C and ii) XT-60 Connector.
    - The TPS548D22 IC is used to generate 0.85V Core Voltage.
    - SiC437DED used for generating 1.8V and 1.1V.
    - The PMIC Switching Regulator is used to generate 3.3V, 1.8V, 2.5V and 4.2V.
5. The SoC contains 3 SPI controllers.
    - 1 SPI controller has been provided externally.
    - The other 2 SPI chipsets have been used to implement a QSPI interface using a MUX and a DEMUX. 
6. The 2 I2C Controllers have been provided on the SBC. These can be used for interfacing with sensors, storage devices, displays or any device working on I2C Protocol.
7. JTAG Test functionality has been provided by providing access to them through a 2x14 Pin Shrouded Connector.
8. The SBC also provides GPRS, GSM, and a Clock and Reset Circuitry.

# File structure
 
The repository contains directories for all sub-sections of the hardware layout.
