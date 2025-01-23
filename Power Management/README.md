# Power Management
###Power Input and Supply

The power section of this Single Board Computer (SBC) is designed to support multiple input options for versatility and efficiency. Below are the key features of the power input design:

Input Connectors
XT60 Connector: A robust input option suitable for high-current applications.
USB Type-C Connector: A modern and widely used connector for both data and power delivery.

USB PD Protocol
The power delivery system leverages the USB Power Delivery (USB PD) protocol to achieve higher power requirements, supporting up to 20V at 5A (100W). This enables the SBC to handle high-performance applications while maintaining efficient power utilization.

###Key Components
Communication Lines: The USB PD protocol relies on the CC1 and CC2 lines for communication. These lines establish a standardized negotiation process for voltage and current levels, ensuring compatibility and safety.

Current Setting Lines: The CC1 and CC2 lines also play a crucial role in setting the appropriate current levels, adhering to the USB PD specifications.

PD Controller: The SBC uses the CYPD3177-24LQXQ by Infineon as the USB PD controller.
