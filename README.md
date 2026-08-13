# Pyghe (1090 Mhz Reciever) 

<img width="1846" height="900" alt="Pyghe Top View" src="https://github.com/user-attachments/assets/020ed3ba-d867-4393-be22-cbc261fd8282" />
<img width="1848" height="903" alt="Pyghe Bottom View" src="https://github.com/user-attachments/assets/b9e2b20b-25b1-42f0-a1eb-baca35bab58d" />

<h4 align="center">
A custom dual-MCU 1090 MHz ADS-B receiver designed for ForeFlight!
</h4>

<div align="center">

![STM32H7](https://img.shields.io/badge/STM32H7-03234B?style=for-the-badge\&logo=stmicroelectronics\&logoColor=white)
![ESP32-S3](https://img.shields.io/badge/ESP32--S3-E7352C?style=for-the-badge\&logo=espressif\&logoColor=white)
![GPS](https://img.shields.io/badge/u--blox%20M10-0057B8?style=for-the-badge\&logoColor=white)
![JLCPCB](https://img.shields.io/badge/JLCPCB-C00000?style=for-the-badge\&logoColor=white)

</div>

<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#purpose">Purpose</a> •
  <a href="#pcb">PCB</a> •
  <a href="#signal-chain">RF Signal Chain</a> •
  <a href="#main-components">Main Components</a> •
  <a href="#communication">Communication</a> •
  <a href="#power-system">Power System</a> •
  <a href="#bom">BOM</a>
</p>

## Key Features

* **1090 MHz ADS-B Receiver** — Designed to receive and decode aircraft transponder broadcasts.
* **STM32H723VGT6** — Primary processing MCU responsible for sensor handling, RF front-end control, and ADS-B decoding.
* **ESP32-S3-WROOM-1U-N16** — Handles WiFi connectivity and transmission of decoded aircraft data to ForeFlight.
* **GL90 Protocol** — Sends decoded traffic information to ForeFlight over WiFi.
* **Mini-Circuits PGA-103+** — RF gain stage for the 1090 MHz receiver front-end.
* **TA0970A SAW Filter** — Provides filtering of the 1090 MHz RF signal.
* **AD8313** — RF logarithmic detector for signal-level measurement.
* **u-blox MAX-M10S** — GNSS receiver for position and timing information.
* **Bosch BMP581** — High-performance barometric pressure sensor for altitude and environmental data.
* **USB-C** — USB connectivity for power, programming, and debugging.
* **18650 Battery** — Integrated single-cell Li-ion battery power.
* **Status LEDs** — Visual feedback for power, system state, and operation.
* **Dual-MCU Architecture** — Separates real-time RF/processing tasks from wireless networking.

## Purpose

Pyghe is a compact 1090 MHz ADS-B receiver designed to provide aircraft traffic information to **ForeFlight**.

The board uses a dual-MCU architecture to divide the workload between the **STM32H723** and **ESP32-S3**.

The STM32 is responsible for the lower-level hardware and real-time processing, including the RF front-end, sensors, signal processing, and ADS-B decoding. Once aircraft data has been decoded, it is passed to the ESP32-S3.

The ESP32-S3 provides the wireless networking layer and transmits the decoded traffic information to ForeFlight using the **GL90 protocol**.

This architecture keeps the timing-sensitive RF and decoding workload isolated from the networking stack while still providing convenient WiFi connectivity.

## PCB

Pyghe is designed as a compact custom PCB integrating the complete RF receiver chain, two microcontrollers, GNSS, environmental sensing, battery management, and wireless connectivity.

The board includes a dedicated RF path for 1090 MHz operation with an external antenna connection through an SMA connector.

### Top View

<img width="1846" height="900" alt="Pyghe Top View" src="https://github.com/user-attachments/assets/020ed3ba-d867-4393-be22-cbc261fd8282" />

### Bottom View

<img width="1848" height="903" alt="Pyghe Bottom View" src="https://github.com/user-attachments/assets/b9e2b20b-25b1-42f0-a1eb-baca35bab58d" />

## RF Signal Chain

Pyghe's receiver front-end is designed around the **1090 MHz ADS-B frequency**.

The incoming RF signal passes through a dedicated filtering and amplification chain before being processed by the STM32.

### RF Front-End

**SMA Antenna → RF Filter → PGA-103+ LNA → RF Detection / Processing → STM32**

Key RF components include:

| Component          | Function                             |
| ------------------ | ------------------------------------ |
| **KH-SMA-K513-G**  | External antenna connector           |
| **TA0970A**        | 1090 MHz RF filter                   |
| **PGA-103+**       | Low-noise RF amplifier               |
| **AD8313**         | RF logarithmic detector              |
| **MCP6566RT-E/OT** | High-speed comparator                |
| **STM32H723VGT6**  | Signal processing and ADS-B decoding |

The RF section is kept physically concentrated on the PCB to minimize unwanted parasitics and interference at 1090 MHz.

## Main Components

| Category          | Component                 | Description                                                        |
| ----------------- | ------------------------- | ------------------------------------------------------------------ |
| Main MCU          | **STM32H723VGT6**         | STM32H7 high-performance MCU for RF control, sensors, and decoding |
| Wireless MCU      | **ESP32-S3-WROOM-1U-N16** | WiFi-enabled MCU for ForeFlight connectivity                       |
| RF Amplifier      | **PGA-103+**              | Mini-Circuits RF gain block                                        |
| RF Filter         | **TA0970A**               | 1090 MHz RF filter                                                 |
| RF Detector       | **AD8313ARMZ-REEL7**      | RF logarithmic detector                                            |
| Comparator        | **MCP6566RT-E/OT**        | High-speed comparator                                              |
| GNSS              | **MAX-M10S-00B**          | u-blox M10 GNSS receiver                                           |
| Barometer         | **BMP581**                | Bosch high-performance pressure sensor                             |
| Battery Charger   | **MP2672**                | Single-cell Li-ion battery management                              |
| 3.3V Regulator    | **AZ1117CH-3.3TRG1**      | 3.3V LDO regulator                                                 |
| Antenna Connector | **KH-SMA-K513-G**         | SMA RF antenna connector                                           |
| RF Connector      | **U.FL-R-SMT-1(80)**      | U.FL RF connector                                                  |
| USB               | **HC-TYPE-C-16P-01A-G**   | USB Type-C connector                                               |
| Main Crystal      | **25 MHz**                | System oscillator                                                  |
| Battery           | **18650**                 | Single-cell Li-ion battery                                         |
| Pressure Sensor   | **BMP581**                | Barometric altitude / pressure sensing                             |
| GNSS Antenna / RF | **U.FL**                  | Compact RF connection for GNSS                                     |
| Status LEDs       | **0603 / 0805 LEDs**      | Power and system status indication                                 |

## Dual-MCU Architecture

Pyghe separates the system into two processing domains.

### STM32H723

The STM32H723 is responsible for the hardware-intensive portion of the receiver:

* 1090 MHz RF front-end control
* RF signal processing
* ADS-B decoding
* GNSS communication
* BMP581 pressure sensing
* System monitoring
* Communication with the ESP32-S3

### ESP32-S3

The ESP32-S3 acts as the wireless communications processor:

* WiFi connectivity
* Communication with ForeFlight
* GL90 protocol transmission
* Receiving decoded aircraft data from the STM32
* Wireless network management

This separation allows the STM32 to focus on deterministic real-time processing while the ESP32 handles the less deterministic networking workload.

## Communication

### ForeFlight / GL90

Decoded ADS-B traffic is transferred to the ESP32-S3 and transmitted over WiFi using the **GL90 protocol**, allowing the receiver to act as an external traffic source for ForeFlight.

### STM32 ↔ ESP32

The two MCUs communicate through a dedicated digital interface, allowing the STM32 to send decoded aircraft information and system data to the ESP32-S3.

### GNSS

The **u-blox MAX-M10S** provides GNSS position and timing data to the system.

### USB-C

USB-C provides a convenient interface for:

* Programming
* Firmware development
* Debugging
* Power input

## Sensors

### u-blox MAX-M10S

The integrated M10 GNSS receiver provides:

* Latitude / longitude
* Altitude
* Ground speed
* Heading
* Time synchronization
* GNSS positioning

### Bosch BMP581

The BMP581 provides high-resolution barometric pressure measurements for determining pressure altitude and monitoring environmental conditions.

## Power System

Pyghe uses an integrated **single-cell 18650 Li-ion battery**.

The power architecture includes:

* 18650 battery input
* Battery management / charging
* 3.3V regulation
* Power switching
* USB-C power input
* Dedicated power status indication

The **AZ1117CH-3.3** provides the primary 3.3V regulated rail used by the digital electronics.

## BOM

The board uses a mixture of RF-specific components, high-performance microcontrollers, GNSS hardware, sensors, and standard passive components.

### Major Components

| Manufacturer   | Part                  | Cost (USD) | Package / Size |
| -------------- | --------------------- | ---------: | -------------- |
| ST             | STM32H723VGT6         |     $6.325 | LQFP-100       |
| Espressif      | ESP32-S3-WROOM-1U-N16 |     $5.246 | Module         |
| u-blox         | MAX-M10S-00B          |    $10.274 | SMD            |
| Analog Devices | AD8313ARMZ-REEL7      |     $5.914 | MSOP-8         |
| Mini-Circuits  | PGA-103+              |     $2.551 | RF Gain Block  |
| Mini-Circuits  | 4 µH                  |     $4.243 | SMD            |
| Bosch          | BMP581                |     $2.403 | LGA-10         |
| TST            | TA0970A               |     $1.427 | RF Filter      |
| Microchip      | MCP6566RT-E/OT        |     $0.568 | SOT-23-5       |
| u-blox / RF    | U.FL-R-SMT-1(80)      |     $0.130 | RF Connector   |
| Kinghelm       | KH-SMA-K513-G         |     $0.597 | SMA            |
| MPS            | MP2672                |        N/A | QFN-18         |
| Diodes Inc.    | AZ1117CH-3.3TRG1      |     $0.075 | SOT-223        |
| HCTL           | HC-TYPE-C-16P-01A-G   |     $0.139 | USB-C          |
| Taitien        | 25 MHz Crystal        |     $0.151 | SMD            |
| Myoung         | 18650                 |     $1.338 | Battery        |

The complete BOM contains the remaining passive components, inductors, LEDs, switches, connectors, capacitors, resistors, and protection components.

## RF Components

The receiver front-end contains several components specifically selected for operation around the 1090 MHz ADS-B band.

| Component            | Purpose                      |
| -------------------- | ---------------------------- |
| **TA0970A**          | RF filtering                 |
| **PGA-103+**         | RF amplification             |
| **AD8313**           | RF signal-level detection    |
| **MCP6566**          | High-speed signal comparison |
| **KH-SMA-K513-G**    | External antenna interface   |
| **U.FL-R-SMT-1(80)** | Compact RF interconnect      |

## Status & Controls

The board includes dedicated user-interface hardware for system feedback and control:

* Power LED
* System status LEDs
* Main power switch
* User / control button
* USB-C interface

## Sponsors

<div align="center">

## Proudly Sponsored By

<table>
  <tr>
    <td align="center" width="50%">
      <a href="https://jlcpcb.com" target="_blank">
        <img src="https://github.com/user-attachments/assets/c9b44859-d24b-48ba-b1d5-8fd29674d73d" alt="JLCPCB" width="400"/>
      </a>
    </td>
    <td align="center" width="50%">
      <a href="https://oshwlab.com/explore" target="_blank" rel="noopener noreferrer">
        <img src="https://github.com/user-attachments/assets/232753ed-b258-49bf-9159-06be05e877c1" alt="OSHWLab" width="400"/>
      </a>
    </td>
  </tr>
</table>

This project is made possible by the generous support of **JLCPCB** and **OSHWLab**. Their commitment to the open hardware community and maker ecosystem enables innovative projects like this to come to life.

</div>
