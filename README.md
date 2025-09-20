# ESP32 Deploy Tool

**!!WARNNING!! IN DEVELOPMENT**

ESP32 merged binaries generator for publication or continuos integration. This code is based of [CanAirIO deploy tool](https://github.com/kike-canaries/canairio_firmware/blob/master/build) but it is for general purpose.

This tool is for PlatformIO projects, and you need its PlatformIO core or CLI installed in your system.

## TODO

- [x] Auto detection of env for build
- [x] Version and Revision definition via Pio ini or env variables
- [x] Support list of flavors to build via env variable
- [x] Binaries merged ouput only for ESP32 for now
- [ ] Auto dectection of CORE type (ESP32/C3/S3/S2). Issue #1

## Usage

Install **deploy** command in your bin directory. Here some examples:

```bash
deploy build
deploy installer
FIRMVER=0.3.2 FIRMREV=999 deploy build
FIRMVER=0.3.2 FIRMREV=999 FLAVORS="ICENAV_BOARD TDECK_ESP32S3" deploy all
```

### Full Example

Run the next commands for see a complete execution of this tool:

```bash
git clone https://github.com/jgauchia/IceNav-v3.git icenav
cd icenav
FLAVORS="TDECK_ESP32S3 ICENAV_BOARD" deploy all
```

Output:

```bash
***********************************************
** Building TDECK_ESP32S3
***********************************************

 PASSED TDECK_ESP32S3 !

***********************************************
** Building ICENAV_BOARD
***********************************************

 PASSED ICENAV_BOARD !


Generating merge binary for ESP32S3_N16R8_v0.2.2rev86_merged.bin
esptool.py v4.5.1
Wrote 0x252800 bytes to file ESP32S3_N16R8/ESP32S3_N16R8_v0.2.2rev86_merged.bin, ready to flash to offset 0x0
2fb5546060e93851d9defc780bbde689  ESP32S3_N16R8/ESP32S3_N16R8_v0.2.2rev86_merged.bin

Generating merge binary for ICENAV_BOARD_v0.2.2rev86_merged.bin
esptool.py v4.5.1
Wrote 0x276690 bytes to file ICENAV_BOARD/ICENAV_BOARD_v0.2.2rev86_merged.bin, ready to flash to offset 0x0
6ab3b517a92cab09049de548ddb20902  ICENAV_BOARD/ICENAV_BOARD_v0.2.2rev86_merged.bin

Generating merge binary for TDECK_ESP32S3_v0.2.2rev86_merged.bin
esptool.py v4.5.1
Wrote 0x25a510 bytes to file TDECK_ESP32S3/TDECK_ESP32S3_v0.2.2rev86_merged.bin, ready to flash to offset 0x0
a8d0d52ff7d3630ba8237df87b39abd4  TDECK_ESP32S3/TDECK_ESP32S3_v0.2.2rev86_merged.bin

packing release:
  adding: ESP32S3_N16R8_v0.2.2rev86_merged.bin (deflated 45%)
  adding: ICENAV_BOARD_v0.2.2rev86_merged.bin (deflated 45%)
  adding: TDECK_ESP32S3_v0.2.2rev86_merged.bin (deflated 45%)

4.0M	icenav_v0.2.2rev86.zip

```