# ESP32 Deploy Tool

**!!WARNNING!! IN DEVELOPMENT**

ESP32 merged binaries generator for publication or continuos integration. This code is based of [CanAirIO deploy tool](https://github.com/kike-canaries/canairio_firmware/blob/master/build) but it is for general purpose.

This tool is for PlatformIO projects, and you need its PlatformIO core or CLI installed in your system.

## TODO

- [x] Auto detection of env for build
- [x] Version and Revision definition via Pio ini or env variables
- [x] Support list of flavors to build via env variable
- [x] Binaries merged ouput only for ESP32 for now
- [ ] Auto dectection of CORE type (ESP32/C3/S3/S2)

## Usage

Install **deploy** command in your bin directory. Here some examples:

```bash
deploy build
deploy installer
FIRMVER=0.3.2 FIRMREV=999 deploy build
FIRMVER=0.3.2 FIRMREV=999 FLAVORS="ICENAV_BOARD TDECK_ESP32S3" deploy all
```
