# Pyghe - Custom 1090 MHz receiver! 

**Description** 
This is a printed circuit board used to receive 1090MHz signals, decode them, and send them to ForeFlight using the GL90 protocol. "Phyge" features a dual MCU design (ESP32-S3/STM32H7), with the STM32 being responsible for sensors, front-end control, and decoding. The Esp32's primary responsibility is transmitting the decoded data through WiFi to ForeFlight using the GL90 protocol. Additionally, the board features a Ublox M10 GPS, various status LEDs, and a BMP 581.
***
**Top View (3D)**
<img width="1846" height="900" alt="image 2" src="https://github.com/user-attachments/assets/020ed3ba-d867-4393-be22-cbc261fd8282" />

**Bottom View (3D)**
<img width="1848" height="903" alt="image 3" src="https://github.com/user-attachments/assets/b9e2b20b-25b1-42f0-a1eb-baca35bab58d" />

**Top View (2D)**
<img width="1602" height="872" alt="image 4" src="https://github.com/user-attachments/assets/2b8d719a-3ea8-4274-b57c-6ed47b6f33fe" />

**Bottom View (2D)**
<img width="1600" height="864" alt="image 5" src="https://github.com/user-attachments/assets/c30959f5-797a-4f72-85be-7092659f076b" />
***
**BOM**
| Manufacturer | Part Name | Cost | Size |
| :--- | :--- | :--- | :--- |
| MYOUNG(美阳) | 18650 | 1.338 | BATTERY-SMD_18650-1S-L77.1-W20.7-1 |
| YAGEO(国巨) | 100Ω | 0.021 | R0603 |
| EVERLIGHT(亿光) | GL | 0.02 | LED0603-RD |
| YAGEO(国巨) | 100nF | 0.004 | C0603 |
| TDK | 3pF | 0.017 | C0603 |
| FH(风华) | 200pF | 0.004 | C0603 |
| TDK | 330pF | 0.012 | C0603 |
| SAMSUNG(三星) | 1nF | 0.003 | C0603 |
| muRata(村田) | 100nF | 0.008 | C0603 |
| TDK | 10uF | 0.078 | C0603 |
| YAGEO(国巨) | 100nF | 0.002 | C0603 |
| SAMSUNG(三星) | 10uF | 0.007 | C0603 |
| SAMSUNG(三星) | 4.7uF | 0.01 | C0603 |
| SAMSUNG(三星) | 1uF | 0.006 | C0603 |
| YAGEO(国巨) | 2.2uF | 0.009 | C0603 |
| SAMSUNG(三星) | 18pF | 0.005 | C0603 |
| YAGEO(国巨) | 10nF | 0.009 | C0805 |
| SAMSUNG(三星) | 1uF | 0.012 | C0805 |
| YAGEO(国巨) | 330nF | 0.024 | C1206 |
| SAMSUNG(三星) | 10uF | 0.032 | C1206 |
| SAMSUNG(三星) | 22uF | 0.048 | C1206 |
| Wild Goose(威谷) | 0.5pF | 0.029 | SOD-923_L0.9-W0.6-LS1.0 |
| LRC(乐山无线电) | TVS | 0.016 | SOD-523_L1.2-W0.8-LS1.6-BI |
| BOOMELE(博穆精密) | 2.54-1*6PHeader-RA | 0.03 | HDR-TH_6P-P2.54-H-M-W10.0 |
| HRS(广濑) | U.FL-R-SMT-1(80) | 0.13 | RF-SMD_FRF05002-JSS103M |
| APV(爱普微) | 620nH | 0.039 | IND-SMD_L2.3-W1.7 |
| APV(爱普微) | 10nH | 0.038 | IND-SMD_L2.3-W1.7 |
| TDK | 27nH | 0.007 | L0402 |
| SHOU HAN(首韩) | 1.5uH | 0.156 | IND-SMD_L7.2-W6.6_GPSR0730 |
| 国星光电 | PWR | 0.013 | LED0805-R-RD |
| UNI-ROYAL(厚声) | 10Ω | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 1kΩ | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 10kΩ | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 150Ω | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 100kΩ | 0.001 | R0603 |
| YAGEO(国巨) | 1kΩ | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 33kΩ | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 12kΩ | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 28.7kΩ | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 47Ω | 0.001 | R0603 |
| UNI-ROYAL(厚声) | 10kΩ | 0.001 | R0603 |
| Tyohm(幸亚电阻) | 5.1kΩ | 0.006 | R0805 |
| PANASONIC(松下) | 4.7kΩ | 0.018 | R0805 |
| kinghelm(金航标) | KH-SMA-K513-G | 0.597 | ANT-TH_KH-SMA-K513-G |
| 韩国韩荣 | K2-1808SN-A4SW | 0.087 | KEY-SMD_4P-L4.2-W3.2-P2.20-LS5.1-TL |
| Mini-Circuits | PGA-103+ | 2.551 | PGA-103+ |
| TST(嘉硕) | TA0970A | 1.427 | FILTER-SMD_6P-L3.8-W3.8-BL |
| MICROCHIP(美国微芯) | MCP6566RT-E/OT | 0.568 | SOT-23-5_L2.9-W1.6-P0.95-LS2.8-BL |
| ADI(亚德诺) | AD8313ARMZ-REEL7 | 5.914 | MSOP-8_L3.0-W3.0-P0.65-LS5.0-BL |
| Mini-Circuits | 4uH | 4.243 | IND-SMD_4P-L3.8-W3.8 |
| U-BLOX | MAX-M10S-00B | 10.274 | SMD-18_L10.1-W9.7-P1.10-TL_SKG09F |
| Bosch(博世) | BMP581 | 2.403 | LGA-10_L2.0-W2.0-P0.50-TL_BMP581 |
| DIODES(美台) | AZ1117CH-3.3TRG1 | 0.075 | SOT-223-3_L6.5-W3.4-P2.30-LS7.0-BR |
| MPS(芯源) | MP2672 | N/A | QFN-18_L3.0-W2.0-P0.40-TL_MPQ2166GD-Z |
| G-Switch(品赞) | Main Switch | 0.34 | SW-TH_3P-P4.70_SS-12D06-G050 |
| ST(意法半导体) | STM32H723VGT6 | 6.325 | LQFP-100_L14.0-W14.0-P0.50-LS16.0-BL |
| ESPRESSIF(乐鑫) | ESP32-S3-WROOM-1U-N16 | 5.246 | WIRELM-SMD_ESP32-S3-WROOM-1U |
| HCTL(华灿天禄) | HC-TYPE-C-16P-01A-G | 0.139 | USB-C-SMD_G-SWITCH_GT-USB-7010EN |
| TAITIEN(泰艺电子) | 25MHz | 0.151 | CRYSTAL-SMD_4P-L3.2-W2.5-BL |
