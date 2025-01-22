# WiFi Module
WiFi Module has been integrated in our SBC in order to enable wireless communication with the controller. The Wifi module is designed using the ESP8266ex IC and a PCB antenna is made on the board.

# WiFi Module Hardware Architecture
![Hardware Architecture](https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/WiFi_Block_Diagram.png)
We have used the ESP8266ex IC for designing the WiFi module for the SBC as it has open source software and hardware, also it is easily available and programmable. The WiFi module uses UART_0 chipset for communication. A PCB antenna supporting 2.4GHz communication and having 50Ohm impedance is used for increasing signal strength. This antenna connected to the output of the Low Noise Amplifier. 

A 40 MHz ABM crystal is used for time synchronization. LSF0204- Quad Bit and SN74 Single Bit Voltage Translators are used to translate voltages from 1.8V to 3.3 V. The 8 pin SST25VF016B 16Mbit Serial Flash is used to store Firmware. The GPIO pins from MLSoC are connected to the RST, GPIO2 and GPIO 0 of the WiFi module for external control of modes. The ESP8266ex IC works on 3.3 V level.

# WiFi Module Schematic
<img src="https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/WiFi_1.png" alt="Image description" width="400" />

The ESP8266ex IC works on 3.3V logic. The power pins VDDD(29), VDDA(1, 30), VDDPST(11, 17), and VDD3P3(3 , 4) are supplied with 3.3V generated in the power section. The Chip_EN pin is also connected to 3.3V.

A PCB antenna which is created by forming paths on the top layer of the board is used to increase signal strength of the Low Noise Amplifier Output. The two inductors and one capacitor are used to retain as much power as possible which can be transmitted by the antenna.

The pins ADC_IN(6), GPIO16(8), GPIO5(24) are created as test points which can be used to inject signals or monitor the circuitry. As per the datasheet a bias resistor of 12K is used on RES12K (31) pin. UART_0 of the SiMa.ai MLSoC is used for communication with the ESP8266ex. Also the three GPIO pins 21, 22 and 23 are used.

# ESP FLASH
<img src="https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/WiFi_2.png" alt="Image description" width="400" />

Pins 18-23 connect to the SST25VF016B SPI Flash for firmware storage, with SD CLK using a 200Ω series resistor. The SPI Flash operates on 3.3V logic. The ESP8266EX RST pin is connected to MLSoC GPIO 23, allowing user-controlled resets.

<img src="https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/WiFi_5.png" alt="Image description" width="400" />

The SN74XC1T45-Q1 voltage translator converts MLSoC 1.8V logic to WiFi module 3.3V logic. DIR is set to logic 1 for signal flow to the ESP8266EX RST pin.

<img src="https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/WiFi_3.png" alt="Image description" width="400" />
 
Similar to the RST pin, the GPIO2(14), GPIO0(15) are also connected to the GPIO 21 and GPIO 22 pins of the MLSoC. The Level translator used in this case is LSF0204 Quad Bit level translator. The IC Quad bit so it can translate four signal lines at a time. The other two inputs of this level translator are used to convert 1.8 V UART signals (UART_0_RX and UART_0_TX) from the MLSoC to 3.3V UART signals UTXD (25) and URXD (26) of the ESP8266ex.

# Mode Selection
The WiFi module can work in two modes. One of the modes is UART mode in which the WiFi module can communicate with other users. The other mode is Flash Boot mode which can be used to install or update the firmware in the external SPI flash. These modes can be selected by changing logic values on the GPIO15, GPIO2 and GPIO0 of the Circuit.

The following is dependency of the modes on these GPIO pins:
- If GPIO15 is LOW, GPIO0 is LOW and GPIO2 is HIGH then UART Mode is
 selected.
- If GPIO15 is LOW, GPIO0 is HIGH and GPIO2 is also HIGH then SPI Flash Boot
 Mode is selected.
