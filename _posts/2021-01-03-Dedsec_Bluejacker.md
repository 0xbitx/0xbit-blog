

<h1 align="center"> DEDSEC_BLUEJACKER </h1>

## DESCRIPTION
DEDSEC_BLUEJACKER is a sophisticated Bluetooth jamming device/tool that uses an ESP32 NodeMCU and an nRF module. This tool can effectively disrupt Bluetooth communication, causing a Denial of Service (DoS) attack on various Bluetooth devices such as Bluetooth speakers, smartphones, IoT devices, and more. By jamming Bluetooth frequencies, DEDSEC_BLUEJACKER renders targeted devices non-functional. It can stop Bluetooth speakers from playing audio, prevent Bluetooth communication on smartphones, affect IoT devices that rely on Bluetooth for communication, and disrupt Bluetooth-dependent industrial equipment.

## requirements:
	
    ESP32-devkit v1 nodeMCU                     
    2x nRF24L01   
    2x 10UF 16v Capacitor
    Data usb cable 

## installation: 

    1. git clone https://github.com/0xbitx/DEDSEC_BLUEJACKER.git
    2. cd DEDSEC_BLUEJACKER
    3. pip install esptool
    4. ./esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 115200 write_flash 0x0 dedsec_bluejacker.hex

## WIRING DIAGRAM

<p align="center">
<img src="https://github.com/0xbitx/DEDSEC_BLUEJACKER/assets/74537225/73003e64-42d2-44f4-845f-d25747b03649" width" width="80%" height="80%">
</p>

## Pinout Configuration

Below are the pinout mappings from the ESP32 to the nRF24L01+ modules for both HSPI and VSPI configurations.

### HSPI Configuration

| 1st nRF24L01 module Pin | HSPI Pin (ESP32 devkit v1) | 10uf 16v capacitor |
|---------------|------------------|--------------------|
| VCC           | 3.3V             | (+) capacitor |
| GND           | GND              | (-) capacitor |
| CE            | GPIO 16          |
| CSN           | GPIO 15          |
| SCK           | GPIO 14          |
| MOSI          | GPIO 13          |
| MISO          | GPIO 12          |
| IRQ           | Not Connected    |

### VSPI Configuration

| 2nd nRF24L01 module Pin | VSPI Pin (ESP32 devkit v1) | 10uf 16v capacitor |
|---------------|------------------|--------------------|
| VCC           | 3.3V             | (+) capacitor |
| GND           | GND              | (-) capacitor |
| CE            | GPIO 22          |
| CSN           | GPIO 21          |
| SCK           | GPIO 18          |
| MOSI          | GPIO 23          |
| MISO          | GPIO 19          |
| IRQ           | Not Connected    |

## Support

If you find my work helpful and want to support me, consider making a donation. Your contribution will help me continue working on open-source projects.

**Bitcoin Address: `36ALguYpTgFF3RztL4h2uFb3cRMzQALAcm`**


<h1 align="center"> DISCLAIMER </h1>

<h4 align="center">I'm not responsible for anything you do with this program, so please only use it for good and educational purposes. </h4>

