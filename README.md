# ESP32 Deploy Tool

**!!WARNNING!! IN DEVELOPMENT**

ESP32 merged binaries generator for publication or continuos integration. This code is based of [CanAirIO deploy tool](https://github.com/kike-canaries/canairio_firmware/blob/master/build) but it is for general purpose.

This tool is for PlatformIO projects, and you need its PlatformIO core or CLI installed in your system.

## TODO

- [x] Auto detection of env for build
- [x] Version and Revision definition via Pio ini or env variables
- [x] Support list of flavors to build via env variable
- [x] Binaries merged ouput only for ESP32 for now
- [ ] Core auto dectection [issue](https://github.com/hpsaturn/esp32-deploy-tool/issues/1) (for ESP32/C3/S3/S2).

## Usage

Fist install **deploy** command in your ~/bin directory, change it to executable, and run it like this possible examples:

Build all flavors:

```bash
deploy build
```

Build installer package:

```bash
deploy installer
```

Build and installer:

```bash
deploy all
```

This tool admit the next environment variables for override defaults:

```bash
FIRMVER (firmware version, i.e 0.2.0. Defautl from pio ini)
FIRMREV (firmware version, i.e 920. Defautl from pio ini)

FIRNAME (firmare name, default basename directory)
FLAVORS (valid pio env values for building)
MCUTYPE (valid ESP32 mcu type: ESP32, ESP32C3, ESP32S2, ESP32S3)
```

override settings examples:

```bash
FIRMVER=0.3.2 FIRMREV=999 deploy build
FIRMVER=0.3.2 FIRMREV=999 FLAVORS="ICENAV_BOARD TDECK_ESP32S3" deploy all
MCUTYPE=ESP32S2 build all
```

### Full Example

Run the next commands for see a complete execution of this tool. For instance here in a random ESP32 PlatformIO project:

```bash
git clone https://github.com/jgauchia/IceNav-v3.git icenav
cd icenav
FLAVORS="TDECK_ESP32S3 ICENAV_BOARD" deploy all
```

(These flavors options are optional. If you don't specefic nothing, deploy could try to build all PlatformIO envs on the .ini file)

**Output**:

```bash
***********************************************
** Building TDECK_ESP32S3
***********************************************

 PASSED TDECK_ESP32S3 !

***********************************************
** Building ICENAV_BOARD
***********************************************

 PASSED ICENAV_BOARD !


Generating merge binary for ICENAV_BOARD_v0.2.2rev86_merged.bin
esptool.py v4.5.1
Wrote 0x276690 bytes to file ICENAV_BOARD/ICENAV_BOARD_v0.2.2rev86_merged.bin, ready to flash to offset 0x0
4c7dc9b8edfdfca9c3d6bbc275a45a59  ICENAV_BOARD/ICENAV_BOARD_v0.2.2rev86_merged.bin

Generating merge binary for TDECK_ESP32S3_v0.2.2rev86_merged.bin
esptool.py v4.5.1
Wrote 0x25a510 bytes to file TDECK_ESP32S3/TDECK_ESP32S3_v0.2.2rev86_merged.bin, ready to flash to offset 0x0
f56b665c88ee006cb9ef13d97a82ed77  TDECK_ESP32S3/TDECK_ESP32S3_v0.2.2rev86_merged.bin

packing release:
  adding: ICENAV_BOARD_v0.2.2rev86_merged.bin (deflated 45%)
  adding: TDECK_ESP32S3_v0.2.2rev86_merged.bin (deflated 45%)

2.7M	icenav_v0.2.2rev86.zip


```
