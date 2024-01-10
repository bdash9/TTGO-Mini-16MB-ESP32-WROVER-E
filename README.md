# TTGO-Mini-16MB-ESP32-WROVER-E
Notes on this besp32
lilygo ttgo mini32 16MB esp32 wrover


https://github.com/LilyGO/TTGO-T7-Demo


Tried boards in arduinoide:

ttgo-t7-v1.5-mini32

To upload code in ArduinoIDE:

Had to set Upload speed to 115200

Also had to set 115200 for Serial monitor

Changed partition scheem to 16MB, etc


For the SD card:
MOSI: 23
MISO: 19
SCK: 18
SS: 5

esptool.py write_flash --flash_size detect 0x00 retro-go_1.39-pre-dirty_odroid-go.img

Info:
$  esptool.py chip_id
Detecting chip type... ESP32
Chip is ESP32-D0WD-V3 (revision v3.1)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: 08:3a:8d:23:ae:94
Uploading stub...
Running stub...
Stub running...
Warning: ESP32 has no Chip ID. Reading MAC instead.
MAC: 08:3a:8d:23:ae:94

![Image 1-9-24 at 7 17 PM](https://github.com/bdash9/TTGO-Mini-16MB-ESP32-WROVER-E/assets/5065324/2fe30e21-540f-46e8-9c64-f9e11764bd5a)



