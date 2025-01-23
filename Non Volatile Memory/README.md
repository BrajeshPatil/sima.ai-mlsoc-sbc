# Non Volatile Memory
The DRAM interface studied was a volatile memory, meaning that once the power is turned off, the data contents get erased off memory. However, if we want memory to be stored in an IC, we need to use Non-Volatile memory ICs like eMMC Flash, QSPI flash and µSD Card.

## eMMC Flash Memory
eMMC Flash Memory with P/N IS22TF16G-JCLA1 is being used in the DroneSense Board. ISSI eMMC products follow the JEDEC eMMC 5.1 standard. It is ideal for embedded storage solutions for industrial and automotive application, which require high performance across a wide range of operating temperatures.

### Hardware Architecture
<img src="https://github.com/user-attachments/assets/0707285a-34ea-4f16-90e5-b8ccc755822d" width="500"/>

- We have the main clock signal, which has different frequencies and can be set according to requirements. Similarly we have a command signal CMD.
- D0-D7 is the data bus.
- VCC is the supply voltage for controller and Flash memory power. VCCQ is the supply voltage for controller and Flash memory I/O power.
- The DS is used in HS-400 mode of the eMMC.
- The VDDI pin must be connected to a capacitor to ground to stabilize internal power.
- The eMMC CRD DET N pin is the Card detect pin, which is tied to 3.3V via resistor as it must be on always.
- eMMC write protect pin EMMC CRD WR PROT is used to configure eMMC as read only. By default, this pin should be pulled high (write protected, read only).

### Schematic
<img src="https://github.com/user-attachments/assets/0cb59842-d6f1-4b33-9844-ae4d5fd2e1af" width="500"/>

## SDIO Flash Memory
The MLSoC supports the SD3.0 controller interface, enabling the loading of boot files from an external SD card. SDIO (Secure Digital Input/Output) is used for high-speed data transfer, connecting the MLSoC to peripherals like storage devices, sensors, and other external components. This interface allows seamless communication between the MLSoC and SD cards, making it ideal for loading firmware, storing data, and expanding the system's memory capacity.

### Hardware Architecture
<img src="https://github.com/user-attachments/assets/8e59eb6e-e311-43d7-81a8-33b06c048fc5" width="500"/>

Features of the SDIO Interface Implementation:
- SD3.0 standard interface supports up to 104MBps bus speed.
- A Micro-SD Push-Push connector with P/N 693071020811 is used for interfacing the external SD card with the MLSoC Evaluation Board.
- SD3.0 standard requires voltage switching. After the initial negotiation with the SD card, the controller begins to switch the voltage from 3.3V to 1.8V. So a level translator is a must to switch the voltage level from 3.3V to 1.8V if the card is detected as SD3.0.
- An SD3.0 compliant level translator with P/N NVT4857UKAZ from NXP semi-conductors takes care the aforementioned switching requirement.
- This level translator IC has integrated EMI filter and ESD protection circuitry on the output side.
- For input ESD and EMI Filtering, we have used a Filtering IC with P/N EMIF06-MSD02N16.
- Both pull-up and pull-down options are provided for write protect signal SD WP, and by default, this pin is pulled high.

### Schematic
![image](https://github.com/user-attachments/assets/73ed801e-1212-4b1e-bf28-065e7fac0512)

## QSPI Flash Memory
### Hardware Architecture
<img src="https://github.com/user-attachments/assets/fd4dac63-7432-414f-b46f-6aaba730fa17" width="500"/>

The following things can be said about QSPI Flash used on the Single Board Computer:
- Three Octal SPI controllers are present in the MLSoC chipset, namely SPIB, SPI0 and SPI1.
- The SPIB controller from the MLSoC is used to connect the SPI flash, where the initial boot loader is present and the MLSoC boots after power on by reading this flash.
- 16Mbit Quad SPI flash IC with P/N W25Q16JWSNIQ TR is used as boot ROM. This IC is an 8-bit SPI with maximum clock rate of 133MHz.
- An additional 10-pin 100 Mils header is included for programming the SPI flash externally using an SPI programmer device. The same is used for analyzing the SPI signals as well.
- Once the MLSoC goes out of reset, it drives the SPB signals. Hence signals from the MLSoC and external programmer are connected to SPI via 6 bit 2:1 multiplexer IC with P/N TS3A27518ERTWR.
- Multiplexing functionality is controlled via the IN1 and IN2 pins, connected to a DIP switch P/N 219-3LPST. Alternatively, GPIOs can be used for control.

### Schematic
![image](https://github.com/user-attachments/assets/7c6062dd-7b93-412a-b752-0a58541cbd98)
