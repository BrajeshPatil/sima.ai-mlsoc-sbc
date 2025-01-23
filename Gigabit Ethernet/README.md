# Gigabit Ethernet
This section explains the schematic design implementation of the Gigabit Ethernet using the DP83867 Ethernet PHY IC. This feature is added in our SBC so that the pilot can be able to communicate with other devices supporting Ethernet or get inbuilt access to the Internet and additional functionality can be added later as required.

### Hardware Architecture
![Hardware Layout](https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/ETHERNET_BLOCK.png)

The MLSoC provides 4 chipsets of Ethernet but the SBC is provided with one Gigabit Ethernet chipset. The Ethernet MAC is interfaced with the RJ45 Magjack connector with the help of the Ethernet PHY DP83867EIS IC.
Magnetic isolation to prevent signal form back routing is also taken care of while designing. Appropriate Crystal values were used for the oscillators of the Ethernet MAC and the Ethernet PHY. 156.25 MHz Crystal was used for the internal working of the Ethernet MAC.

### Schematic
<img src="https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/Ethernet_1.png" alt="Image description" width="400" />
We have used the 2 power supply mode of the IC. An 11kΩ bias resistor is used as per the datasheet. INT(44) and RESET N(43) are connected to MLSoC GPIOs for external user control.

<img src="https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-functionality/Ethernet_3.png" alt="Image description" width="250" />

The clock input is provided through a 25MHz crystal. The crystal load capacitance is calculated using ((CX1 x CX2) / (CX1 + CX2)) + Cstray. Resistance is 30 ohms and crystal load capacitance is 22pF. This crystal oscillator is connected to pins XO(14) and XI(15).

The Ethernet PHY is connected to MLSoC with the 4 pin mode. These 4 pins are SGMII_SON(36), SGMII_SOP(35), SGMII_SIN(28), SGMII_SIP(27). SGMII_SON and SGMII_SOP are used for the receiving signal and form a differential pair. They are connected to the ETH_0_RX_N and ETH_0_RX_P using a resistor divider network and 0.1µ F capacitors.

SGMII_SIN and SGMII_SIP form a differential pair and are used to transmit. Rhi = 4K and Rlo = 10K are used on pins 27,28,35,36.

The LED_0, LED_1 and LED_2 pins are used as strapping options to select particular modes.

### Power Sub-Section
<img src="https://github.com/user-attachments/assets/12ef914c-bd1b-4bb0-91ba-2e2e62cb4e41" alt="Image description" width="400" />

It is possible to operate the DP83867 using two or three power supplies. Although the two supply configuration requires slightly more power, it requires less space as compared to its counterpart. So we have used the three power supply configuration.

VDDA1P8 pin is left unconnected. We have connected 1µF and 0.1µF decoupling capacitors as close as possible to component VDD pins and 0.1µF capacitor closest to the pin. In our SBC we have used VDDIO as 1.8 V. The power required for this IC is 495 mW.

### Boot Strapping
<img src="https://github.com/user-attachments/assets/a2c76512-b62c-4fe8-a3c1-5f8329f63f92" alt="Image description" width="400" />

The DP83867 has multiple functional pins which provide strapping options which help the device work into specific modes. Values of these pins are sampled at power up or hard reset. Strap Configuration can be defined by two resistors Rhi and Rlo. Values of these resistors can be set in order to select one of the four modes. We have used SGMII ENABLE i.e. Mode 1 for LED_0.
