# TTGO-Mini-16MB-ESP32-WROVER-E
Notes on this besp32
lilygo ttgo mini32 16MB esp32 wrover
ttgo-t7-v1.5-mini32

https://github.com/LilyGO/TTGO-T7-Demo


Tried boards in arduinoide:

ttgo-t7-v1.4-mini32 and small stuff loads but it wont let me select 16MB of FLASH (4MB max)

ESP32 WROVER module with 16MB - just keeps rebooting


To upload code in ArduinoIDE:

Had to set Upload speed to 115200

Also had to set 115200 for Serial monitor

Changed partition scheem to 16MB, etc


For the SD card:
MOSI: 23
MISO: 19
SCK: 18
SS: 5

I had to flash a ArduinoIDE sketch on to the board before I coudl use esptool.py. If I didn't it gave an error "A fatal error occurred: Could not connect to an Espressif device on any of the 2 available serial port" OR the serial monitor was still on in ArduinoIDE

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


Tried adding a new board to ArduinIDE that coudl handle 16MB:
vi /Users/bdash/Library/Arduino15//packages/esp32/hardware/esp32/2.0.11/boards.txt

Add:

##############################################################
ttgo-t7-v15-mini32.name=TTGO T7 V1.5 Mini32 Ben
ttgo-t7-v15-mini32.bootloader.tool=esptool_py
ttgo-t7-v15-mini32.bootloader.tool.default=esptool_py
ttgo-t7-v15-mini32.upload.tool=esptool_py
ttgo-t7-v15-mini32.upload.tool.default=esptool_py
ttgo-t7-v15-mini32.upload.tool.network=esp_ota
ttgo-t7-v15-mini32.upload.maximum_size=1310720
ttgo-t7-v15-mini32.upload.maximum_data_size=327680
ttgo-t7-v15-mini32.upload.wait_for_upload_port=true
ttgo-t7-v15-mini32.upload.flags=
ttgo-t7-v15-mini32.upload.extra_flags=
ttgo-t7-v15-mini32.serial.disableDTR=true
ttgo-t7-v15-mini32.serial.disableRTS=true
ttgo-t7-v15-mini32.build.tarch=xtensa
ttgo-t7-v15-mini32.build.bootloader_addr=0x1000
ttgo-t7-v15-mini32.build.target=esp32
ttgo-t7-v15-mini32.build.mcu=esp32
ttgo-t7-v15-mini32.build.core=esp32
ttgo-t7-v15-mini32.build.variant=ttgo-t7-v15-mini32
ttgo-t7-v15-mini32.build.board=TTGO_T7_V15_Mini32
ttgo-t7-v15-mini32.build.f_cpu=240000000L
ttgo-t7-v15-mini32.build.flash_size=16MB
ttgo-t7-v15-mini32.build.flash_freq=40m
ttgo-t7-v15-mini32.build.flash_mode=dio
ttgo-t7-v15-mini32.build.boot=dio
ttgo-t7-v15-mini32.build.partitions=default_16MB
ttgo-t7-v15-mini32.build.defines=
ttgo-t7-v15-mini32.menu.PartitionScheme.default=Default 16MB with spiffs (1.2MB APP/1.5MB SPIFFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.default.build.partitions=default
ttgo-t7-v15-mini32.menu.PartitionScheme.defaultffat=Default 4MB with ffat (1.2MB APP/1.5MB FATFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.defaultffat.build.partitions=default_ffat
ttgo-t7-v15-mini32.menu.PartitionScheme.minimal=Minimal (1.3MB APP/700KB SPIFFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.minimal.build.partitions=minimal
ttgo-t7-v15-mini32.menu.PartitionScheme.no_ota=No OTA (2MB APP/2MB SPIFFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.no_ota.build.partitions=no_ota
ttgo-t7-v15-mini32.menu.PartitionScheme.no_ota.upload.maximum_size=2097152
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_3g=No OTA (1MB APP/3MB SPIFFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_3g.build.partitions=noota_3g
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_3g.upload.maximum_size=1048576
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_ffat=No OTA (2MB APP/2MB FATFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_ffat.build.partitions=noota_ffat
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_ffat.upload.maximum_size=2097152
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_3gffat=No OTA (1MB APP/3MB FATFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_3gffat.build.partitions=noota_3gffat
ttgo-t7-v15-mini32.menu.PartitionScheme.noota_3gffat.upload.maximum_size=1048576
ttgo-t7-v15-mini32.menu.PartitionScheme.huge_app=Huge APP (3MB No OTA/1MB SPIFFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.huge_app.build.partitions=huge_app
ttgo-t7-v15-mini32.menu.PartitionScheme.huge_app.upload.maximum_size=3145728
ttgo-t7-v15-mini32.menu.PartitionScheme.min_spiffs=Minimal SPIFFS (1.9MB APP with OTA/190KB SPIFFS)
ttgo-t7-v15-mini32.menu.PartitionScheme.min_spiffs.build.partitions=large_spiffs_16MB
ttgo-t7-v15-mini32.menu.PartitionScheme.min_spiffs.upload.maximum_size=4718592
ttgo-t7-v15-mini32.menu.CPUFreq.240=240MHz (WiFi/BT)
ttgo-t7-v15-mini32.menu.CPUFreq.240.build.f_cpu=240000000L
ttgo-t7-v15-mini32.menu.CPUFreq.160=160MHz (WiFi/BT)
ttgo-t7-v15-mini32.menu.CPUFreq.160.build.f_cpu=160000000L
ttgo-t7-v15-mini32.menu.CPUFreq.80=80MHz (WiFi/BT)
ttgo-t7-v15-mini32.menu.CPUFreq.80.build.f_cpu=80000000L
ttgo-t7-v15-mini32.menu.CPUFreq.40=40MHz (40MHz XTAL)
ttgo-t7-v15-mini32.menu.CPUFreq.40.build.f_cpu=40000000L
ttgo-t7-v15-mini32.menu.CPUFreq.26=26MHz (26MHz XTAL)
ttgo-t7-v15-mini32.menu.CPUFreq.26.build.f_cpu=26000000L
ttgo-t7-v15-mini32.menu.CPUFreq.20=20MHz (40MHz XTAL)
ttgo-t7-v15-mini32.menu.CPUFreq.20.build.f_cpu=20000000L
ttgo-t7-v15-mini32.menu.CPUFreq.13=13MHz (26MHz XTAL)
ttgo-t7-v15-mini32.menu.CPUFreq.13.build.f_cpu=13000000L
ttgo-t7-v15-mini32.menu.CPUFreq.10=10MHz (40MHz XTAL)
ttgo-t7-v15-mini32.menu.CPUFreq.10.build.f_cpu=10000000L
ttgo-t7-v15-mini32.menu.FlashMode.qio=QIO
ttgo-t7-v15-mini32.menu.FlashMode.qio.build.flash_mode=dio
ttgo-t7-v15-mini32.menu.FlashMode.qio.build.boot=qio
ttgo-t7-v15-mini32.menu.FlashMode.dio=DIO
ttgo-t7-v15-mini32.menu.FlashMode.dio.build.flash_mode=dio
ttgo-t7-v15-mini32.menu.FlashMode.dio.build.boot=dio
ttgo-t7-v15-mini32.menu.FlashMode.qout=QOUT
ttgo-t7-v15-mini32.menu.FlashMode.qout.build.flash_mode=dout
ttgo-t7-v15-mini32.menu.FlashMode.qout.build.boot=qout
ttgo-t7-v15-mini32.menu.FlashMode.dout=DOUT
ttgo-t7-v15-mini32.menu.FlashMode.dout.build.flash_mode=dout
ttgo-t7-v15-mini32.menu.FlashMode.dout.build.boot=dout
ttgo-t7-v15-mini32.menu.FlashFreq.80=80MHz
ttgo-t7-v15-mini32.menu.FlashFreq.80.build.flash_freq=80m
ttgo-t7-v15-mini32.menu.FlashFreq.40=40MHz
ttgo-t7-v15-mini32.menu.FlashFreq.40.build.flash_freq=40m
ttgo-t7-v15-mini32.menu.FlashSize.4M=4MB (32Mb)
ttgo-t7-v15-mini32.menu.FlashSize.4M.build.flash_size=4MB
ttgo-t7-v15-mini32.menu.FlashSize.16M=16MB (32Mb)
ttgo-t7-v15-mini32.menu.FlashSize.16M.build.flash_size=16MB
ttgo-t7-v15-mini32.menu.UploadSpeed.921600=921600
ttgo-t7-v15-mini32.menu.UploadSpeed.921600.upload.speed=921600
ttgo-t7-v15-mini32.menu.UploadSpeed.115200=115200
ttgo-t7-v15-mini32.menu.UploadSpeed.115200.upload.speed=115200
ttgo-t7-v15-mini32.menu.UploadSpeed.256000.windows=256000
ttgo-t7-v15-mini32.menu.UploadSpeed.256000.upload.speed=256000
ttgo-t7-v15-mini32.menu.UploadSpeed.230400.windows.upload.speed=256000
ttgo-t7-v15-mini32.menu.UploadSpeed.230400=230400
ttgo-t7-v15-mini32.menu.UploadSpeed.230400.upload.speed=230400
ttgo-t7-v15-mini32.menu.UploadSpeed.460800.linux=460800
ttgo-t7-v15-mini32.menu.UploadSpeed.460800.macosx=460800
ttgo-t7-v15-mini32.menu.UploadSpeed.460800.upload.speed=460800
ttgo-t7-v15-mini32.menu.UploadSpeed.512000.windows=512000
ttgo-t7-v15-mini32.menu.UploadSpeed.512000.upload.speed=512000
ttgo-t7-v15-mini32.menu.DebugLevel.none=None
ttgo-t7-v15-mini32.menu.DebugLevel.none.build.code_debug=0
ttgo-t7-v15-mini32.menu.DebugLevel.error=Error
ttgo-t7-v15-mini32.menu.DebugLevel.error.build.code_debug=1
ttgo-t7-v15-mini32.menu.DebugLevel.warn=Warn
ttgo-t7-v15-mini32.menu.DebugLevel.warn.build.code_debug=2
ttgo-t7-v15-mini32.menu.DebugLevel.info=Info
ttgo-t7-v15-mini32.menu.DebugLevel.info.build.code_debug=3
ttgo-t7-v15-mini32.menu.DebugLevel.debug=Debug
ttgo-t7-v15-mini32.menu.DebugLevel.debug.build.code_debug=4
ttgo-t7-v15-mini32.menu.DebugLevel.verbose=Verbose
ttgo-t7-v15-mini32.menu.DebugLevel.verbose.build.code_debug=5
ttgo-t7-v15-mini32.menu.EraseFlash.none=Disabled
ttgo-t7-v15-mini32.menu.EraseFlash.none.upload.erase_cmd=
ttgo-t7-v15-mini32.menu.EraseFlash.all=Enabled
ttgo-t7-v15-mini32.menu.EraseFlash.all.upload.erase_cmd=-e

##############################################################

Restart ArduinoIDE app


and :

cp ./variants/ttgo-t7-v14-mini32/pins_arduino.h /Users/bdash/Library/Arduino15/packages/esp32/hardware/esp32/2.0.11/cores/esp32/

