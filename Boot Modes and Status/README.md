# Boot Modes and Status
This is a part of the MLSoC which contains the pins for the Boot modes and the System pins. The System pins can be used in order monitor the status of the SBC. So the four System pins have been connected to test points which can be easily accessed by the user to check system conditions.

<img src="https://github.com/user-attachments/assets/3afeb131-58c6-4900-becc-e6f373d05737" alt="Image description" width="250" />

There are four Boot Mode Pins present in the MLSoC. These pins along with the QSPI interface can be used to select the Boot Mode of the SBC. In order to provide control over selection of boot modes to the user we have connected these pins to DIP switches which can be used to pull-up or pull-down the pins.

<img src="https://github.com/user-attachments/assets/1586a36c-47fe-47b3-824c-d468ea589d87" alt="Image description" width="250" />
