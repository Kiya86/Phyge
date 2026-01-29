# Pyghe - Custom 1090 MHz receiver! 

**Top View**
<img width="1846" height="900" alt="image 2" src="https://github.com/user-attachments/assets/020ed3ba-d867-4393-be22-cbc261fd8282" />

**Bottom View**
<img width="1848" height="903" alt="image 3" src="https://github.com/user-attachments/assets/b9e2b20b-25b1-42f0-a1eb-baca35bab58d" />

**Description** 
This is a printed circuit board used to receive 1090MHz signals, decode them, and send them to ForeFlight using the GL90 protocol. "Phyge" features a dual mcu design (Esp32 S3/STM 32 H7), with the STM32 being responsible for sensors, front-end control, and decoding. The Esp32's primary responsibility is transmitting the decoded data through WiFi to ForeFlight using the GL90 protocol. Additionally, the board features a Ublox M10 GPS, various status LEDs, and a BMP 581.




