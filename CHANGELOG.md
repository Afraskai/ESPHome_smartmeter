# Changelog

## [1.1.0] - 2026-10-04

Verified against **ESPHome 2026.9.1**: the previous configuration built unchanged
and was flashed and tested on the device (SML reception, OLED pages, web UI, OTA).
Both language variants of this release compile cleanly (ESP-IDF toolchain,
RAM 32.9 %, flash 52.4 %).

### Added
- `WiFi Qualitaet` text sensor: plain-language WiFi rating in 5 levels with the
  raw dBm value in brackets (e.g. `schwach (-78 dBm)`). Shows up in the ESPHome
  web UI and in Home Assistant. It is fed by the `wifi_signal` sensor, which is
  now marked `internal` and therefore no longer appears as its own entity.

### Notes
- Since ESPHome 2026.7.0, ESP32 builds default to the native `esp-idf` toolchain.
  `framework: type: arduino` keeps working, but the `platformio` toolchain is
  deprecated and will be removed in 2027.2.0.

## [1.0.0] - 2026-06-20

ESPHome 2026.3.0+ changed the web_server default from v1 (embedded UI) to v2/v3
(CDN-based JS architecture). The previous config without an explicit `version:`
silently inherited the new architecture, but the CDN-loaded frontend JS did not
render sensor values correctly on this device.

### Fixed
- Web UI blank after ESPHome upgrade (v2/v3 require `version:` to be set
  explicitly, or `local: true` for embedded assets) → added `version: 3`

## [0.1.0] - 2026-XX-XX
### Added
- Initial release: ISKRA SML reader with ESP32-C3 OLED + BPW40 photodiode
- SML sensors (power, grid import total, grid export total)
- OLED display with page rotation (CURR / IMPORT / EXPORT)
- Blue LED blink on data reception
- Display auto-off after 5 minutes
- WiFi, OTA, API, web_server support
- 3D-printable case (STL files)
- English & German READMEs
