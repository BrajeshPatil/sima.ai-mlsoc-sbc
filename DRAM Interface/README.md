# DRAM Interface
4x 32-bit LPDDR4 chipsets with P/N MT53E1G32D2FW-046 IT:B from Micron are mounted on the MLSoC Evaluation Board. These DRAM modules provide high-speed, low-power memory, essential for storing and accessing large datasets efficiently. The LPDDR4 memory is crucial for applications such as data buffering, real-time processing, and running memory-intensive tasks, ensuring optimal performance for embedded systems.

### Hardware Architecture
<img src="https://github.com/user-attachments/assets/e35a634b-2489-4b89-8ce9-24cc76cec4df" width="500" >

Features of the LPDDR4 Implementation in the MLSoC:
- Each LPDDR4 chipset is of 4GB density. Each chip has operating frequency 1866MHz clock rate, which is same as that of MLSoC memory controller operating frequency.
- All signals are of LVSTL IO standard.
- Power requirement of each LPDDR4 IC is as follows:
  - VDD1 = 1.8V
  - VDD2 = 1.1V
  - VDDQ = 1.1V
- LPDDR4 chipset requires power sequencing:
  - VDD1 must ramp at the same time or earlier than VDD2.
  - VDD2 must ramp at the same time or earlier than VDDQ.
  - VDD1must be greater than VDD2 and VDD2 must be greater than (VDDQ - 200mV).
- 4 individual DRAM controllers are present in the MLSoC, hence for command/address, control, and data signals, point to point routing topology is used between MLSoC and LPDDR4 chipset.
- The ZQ calibration pins are connected to VDDQ through 240 ±-1% resistor.
- LPDDR4 chipset command or address ODT control signals, ODT_CA_A,ODT_CA_B are pulled to VDD2 for enabling on-die termination.

### Implementation of LPDDR4
Following are the reasons for selecting the aforementioned LPDDR4 device:
- Selected LPDDR4 supports 32 Bit IO channels.
- Industrial grade LPDDR4 parts are readily available.
- Available at a cost effective price.
- LPDDR4 IC from Micron has been tested successfully.

### Schematic
<img src="https://raw.githubusercontent.com/BrajeshPatil/sima.ai_mlsoc_sbc/main/images/hardware-design/DRAM_LPDDR4_SCH_1.png" />
