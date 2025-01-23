# SPI Bus
Serial peripheral interface (SPI) allows synchronous serial communication (full duplex or half duplex) with continuous streaming of data communicated between the controller and one or more peripheral devices. The dual embedded SPI controllers allow the MLSoC to communicate with external sensors, ADCs, flash memory, and other low data-rate peripherals. We have more two SPI controllers present in the MLSoC. These are SPI0 and SPI1. The following are the features of these controllers:
  - 8-bit operation
  - Four Slave Selects
  - Dual Master/Slave operation
  - 25 MHz SDR operation

### Hardware Architecture
<img src="https://github.com/user-attachments/assets/b18118c5-215a-4848-9190-a3415c54e1a6" alt="Image description" width="500" />

- SPI0 and SPI1 are the two SPI interfaces present in the MLSoC.
- Since we are already using one Quad SPI with QSPI Flash Memory, what we need to do is connect the SPI0 and SPI1 to connectors. Thus, the SPI0 and SPI1 are connected to an external 20 POS header connector with P/N 70246-2001.
- To connect to the header, the voltage must first be translated from 1.8V to 3.3V. An 8-bit level translator, TXS0108EPWR, is used for this purpose.
- Since we have more number of SPI pins, we’ll be connecting the other pins to 4bit Level Translators with P/N TXS0104EPWR.

### Schematic
![image](https://github.com/user-attachments/assets/fd821908-e835-4490-b8ef-d6771ea92e52)
