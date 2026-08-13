# Pyghe (1090 Mhz Reciever) 

<img width="1846" height="900" alt="Pyghe Top View" src="https://github.com/user-attachments/assets/020ed3ba-d867-4393-be22-cbc261fd8282" />
<img width="1848" height="903" alt="Pyghe Bottom View" src="https://github.com/user-attachments/assets/b9e2b20b-25b1-42f0-a1eb-baca35bab58d" />

<h4 align="center">
A custom dual-MCU 1090 MHz ADS-B receiver designed for ForeFlight!
</h4>

<div align="center">

![STM32H7](https://img.shields.io/badge/STM32H7-03234B?style=for-the-badge\&logo=stmicroelectronics\&logoColor=white)
![ESP32-S3](https://img.shields.io/badge/ESP32--S3-E7352C?style=for-the-badge\&logo=espressif\&logoColor=white)
![JLCPCB](https://img.shields.io/badge/JLCPCB-C00000?style=for-the-badge\&logoColor=white)

</div>

<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#purpose">Purpose</a> •
  <a href="#pcb">PCB</a> •
  <a href="#signal-chain">RF Signal Chain</a> •
  <a href="#main-components">Main Components</a> •
  <a href="#communication">Communication</a> •
  <a href="#bom">BOM</a> •
  <a href="#sponsors">Sponsors</a> 
</p>

## Features

* **1090 MHz Front End (ADS-B Receiver)** —Uses two sets of amplifiers and filters to receive and decode aircraft transponder data. PGA-103 is used as the gain stage, while the TA0970A serves as the SAW filter. Additionally, an AD8313 is included for signal level measurement
* **STM32H723VGT6** —Handles all of the sensors, RF control and decoding of data 
* **ESP32-S3-WROOM-1U-N16** —Handles the WiFi and transmission of decoded aircraft data to ForeFlight 
* **GL90 Protocol** —Sends decoded traffic information to ForeFlight over WiFi
* **MAX-M10S** —A GPS is included for positioning of the device 
* **BMP581** —A barometric pressure sensor for altitude data in case a user requires it
* **18650 Battery System** —Integrated two Li-ion batteries and a charging circuit 

## Purpose

Pyghe is a 1090 MHz ADS-B receiver that is meant to provide aircraft traffic information to ForeFlight using the GL90 protocol. The board uses a dual MCU architecture to divide the workload. The STM32 handles the sensors, RF front end, and data decoding, which the ESP32 then transmits over WIFI to ForeFlight. 

### Top View

<img width="1846" height="900" alt="Pyghe Top View" src="https://github.com/user-attachments/assets/020ed3ba-d867-4393-be22-cbc261fd8282" />

### Bottom View

<img width="1848" height="903" alt="Pyghe Bottom View" src="https://github.com/user-attachments/assets/b9e2b20b-25b1-42f0-a1eb-baca35bab58d" />

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
