# System Clocks
Clocks are used in order to provide time synchronization to the circuit. The table given below contains all the Reference Clocks used:
### Table of Oscillator Frequencies and Specifications

| Item No. | Oscillator Frequency | Clock Source | Frequency Stability | Device | Interface |
|----------|----------------------|--------------|---------------------|--------|-----------|
| 1        | 33MHz                | Crystal      | 10ppm               | MLSoC  | MLSoC Reference Clock |
| 2        | 32.768kHz            | Crystal      | 20ppm               | MLSoC  | RTC Reference Clock |
| 3        | 156.25MHz            | Crystal      | 50ppm               | MLSoC  | Ethernet MAC Reference Clock |
| 4        | 25MHz                | Crystal      | 25ppm               | Ethernet Physical IC | Reference Clock for Ethernet Physical IC |

### Schematic
![image](https://github.com/user-attachments/assets/ae1b5566-3038-4a76-a841-de4a6a7bd417)

The Reference clock used for the Ethernet Physical IC is mention in the Gigabit Ethernet Section.
