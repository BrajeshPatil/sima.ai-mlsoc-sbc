# GSM and GPS Module
In order to track location of the drone and to add one more communication method through SMS, the GPS and GSM Module has been developed. These functionalities are designed using the A9G Ai-Thinker Module.

# GSM and GPS Module: Hardware Architecture
![image](https://github.com/user-attachments/assets/b8ee7618-d885-4119-9bd2-fa366d36fae2)
The block diagram above explains the GSM and GPS Module which we have designed.The A9G Ai Thinker IC is used for this purpose. The circuit has an in-built Micro-Sim, Microphone and antennas for GPRS and GPS. The Micro-Sim used is 78646-3001. 

VSIM, SIM_RST, SIM_CLK and SIM_DIO are connected to the equivalent pins on the A9G Ai Thinker. The I2C and SPK buses are provided to the user through 01x08 Connector. The Microphone Signal has two differential pins which are interfaced using the ICS_40720 IC. The UART1 chipset from the MLSoC is used provided to the A9G Ai Thinker after voltage translation from 1.8V to 4V. UART1_CTS and UART1_RTS pins are provided as test points for the user.

# GSM and GPS Module Schematic
![image](https://github.com/user-attachments/assets/fa179bfb-7888-4160-89f4-8aa69f3364e2)
