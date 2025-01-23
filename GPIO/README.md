# GPIO
The MLSoC supports 32 GPIO for various I/O operations. An ESD protection is added for all the GPIO signals. Following is the list of GPIOs and there use cases:
  - GPIO[7:0] are connected to an external connector with P/N M20-7810645R. The I/O logic is 1.8V, so these GPIOs pass through a level translator, P/N TXS0108EPWR. The connector has a max current rating of 3A. These GPIO pins can also be used for interrupting the APU. GPIO[8] enables the level translator, P/N NVT4857UKAZ, used in the SDIO interface.
  - GPIO[16:9], GPIO[18] and GPIO[28:24] are connected to a 26-pin external connector with P/N 2-1761603-9. No level translator is used with these GPIO pins.
  - GPIO[19] and GPIO[20] are used in interfacing with the Ethernet Transceiver. GPIO[23:21] are used for interfacing with the ESP8266ex WiFi Module.
  - GPIO[29] is connected with a LED for testing purposes.
  - GPIO[30] and GPIO[31] are used to software switch the multiplexer with P/N TS3A27518ERTWR used in QSPI flash.

### Schematic
<img src="https://github.com/user-attachments/assets/b865f17b-eec6-42e1-bfd3-f766c22dafa2" alt="Image 1" width="400"/>
<img src="https://github.com/user-attachments/assets/dfc1dbc6-b625-4b61-baae-3a3627bd9107" alt="Image 2" width="400"/>
