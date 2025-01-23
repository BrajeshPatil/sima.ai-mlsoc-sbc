# I2C Bus
This section discusses about the implementation of two I2C Buses in the design. I2C is an important communication protocol which can be used to communicate with sensors or other external devices through its two buses, a Clock Pin and a Data Pin.

### Hardware Architecture
![image](https://github.com/user-attachments/assets/933bdb28-e007-4592-9b6e-e3e70f1563f8)
- The MLSoC provides two I2C buses: I2C0 and I2C1, each with SDA (data) and SCK (clock) pins.
- MLSoC I2C operates on 1.8V logic, while most sensors use 3.3V logic.
- A voltage translator TXS0104EPWR (Quad Bit Voltage Translator) is used to convert 1.8V to 3.3V.
- Translation mapping:
    - 1.8V buses at A1, A2, A3, A4 → 3.3V buses at B1, B2, B3, B4.
- 4.7k ohm pull-up resistors are used on both sides of the voltage translator.
- The 3.3V I2C buses are connected to a 15-91-6082 C-Grid Connector, which also operates on 3.3V logic.
- Users can access the 3.3V I2C buses via the C-Grid Connector.

### Schematic
![image](https://github.com/user-attachments/assets/2d751dc0-59f9-4320-a4b0-d804f74d5ca4)
