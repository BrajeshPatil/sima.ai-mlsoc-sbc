# UART: Hardware Architecture
![image](https://github.com/user-attachments/assets/5f25dbf4-0788-4409-9abb-8ac16746ff41)
The information related to UART is given below:

- The FT2232HL-REELIC is used as a USB-to-UART transceiver for Linux Boot (UART2) and Troot Boot (UARTB).  The VBUS voltage from the USB Type-C connector (P/N TYPE-C-31-M-12) is directly connected to the RESET pin of the FTDI.
- VCCIO for FT2232HL transceiver IC is provided with 1.8V on-board power supply to match the MLSoC IO voltage characteristics.
- Pair of LEDs are used for both Linux Boot ans Troot Boot to indicate the transmit state and receive state of the signal through UART.
- Alevel translator with P/N TXS0102DCUT is used to convert the MLSoC UART signals to 3.3V I/O level.
- The rest of three general purpose UARTs are connected to external header pins with Pitch as 100Mils and 4 POS Header pin. They have been level translated from 1.8V to 3.3V using P/N TXS0102DCUT.
- UART0 interfaces with the ESP8266ex WiFi module and can also be accessed externally via a header using the TMUX121NKGR multiplexer, controlled by a 219-3LPST DIP switch. Similarly, UART2 and UART3 connect to external headers via the same multiplexer. UART1 connects to the A9G module (TX-RX) through a 1.8V to 2.8V level translator.
- All UART pins on the connector have been ESD protected using Protection diodes with P/N ESDR0524SMUTAG.
