# WiFi SDR

AI-assisted reverse engineering opens a door into a new world of radio experimentation: familiar Wi-Fi hardware can become something far more interesting when we look beyond its documented features.

This repository tracks Wi-Fi chipsets that expose raw in-phase and quadrature (IQ) samples through undocumented, diagnostic, or test modes, making SDR experiments possible on everyday hardware. It collects the available evidence, practical limits, and projects built around these capabilities. A capture mode is a starting point; continuous streaming, usable bandwidth, and tuning range depend on the implementation.

[Chipsets](#ic) · [Projects](#projects) · [Contributing](CONTRIBUTING.md) · [Data conventions](docs/CONVENTIONS.md)

## IC

Known chipsets grouped by manufacturer. RF frequencies and bandwidths are expressed in **MHz**; sample rates are expressed in **MS/s**. See the linked sources for implementation details.

### ESP32

Espressif’s family of Wi-Fi microcontrollers, popular in embedded and hobbyist projects.

<table><tbody><tr><td><strong>Chip</strong></td><td><strong>Sample rate RX, max</strong></td><td><strong>Analog bandwidth</strong></td><td><strong>Frequency range</strong></td><td><strong>Max realtime output sample rate</strong></td><td><strong>Source</strong></td></tr><tr><td>ESP32</td><td>80 MS/s</td><td>?</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-S2</td><td>80 MS/s</td><td>60 MHz</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-S3</td><td>80 MS/s</td><td>69 MHz</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td><p><i>32 MS/s, Octal SPI2</i></p><p>80 MS/s, 100 MHz bitbang</p></td><td><p><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></p><p><a href="https://github.com/h0m3us3r/eSpDR">h0m3us3r/eSpDR</a></p><p><a href="https://github.com/whstudio123/esp32-iq-tx">whstudio123/esp32-iq-tx</a></p></td></tr><tr><td>ESP32-S31</td><td>80 MS/s</td><td>54 MHz</td><td>2400–2483.5 MHz</td><td>40 MS/s, Gigabit Ethernet (8 bit)<br>20 MS/s, Gigabit Ethernet (10 bit)<br>20 MS/s, USB HS (8 bit)</td><td><p><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></p><p><a href="https://github.com/whstudio123/esp32-iq-tx">whstudio123/esp32-iq-tx</a></p><p><a href="https://github.com/ESPARGOS/SoapyESPSDR#capabilities-and-limitations">SoapyESPSDR</a></p><p><a href="https://github.com/alphafox02/s31-sdr#s31-sdr">s31-sdr</a></p></td></tr><tr><td>ESP32-C2</td><td>80 MS/s</td><td>20 MHz</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C3</td><td>80 MS/s</td><td>62 MHz</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C5</td><td>80 MS/s</td><td>48 MHz</td><td><p>2400–2483.5 MHz</p><p>5150–5895 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C6</td><td>80 MS/s</td><td>54 MHz</td><td>2400–2483.5 MHz</td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C61</td><td>80 MS/s</td><td>54 MHz</td><td>2400–2483.5 MHz</td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr></tbody></table>

> **Notes**
> 
> *   All radios provide 10-bit I and Q samples.
> *   Interface-based estimates divide link bandwidth by the 32-bit IQ frame width.
> *   The ESP32-S31 Function-CoreBoard rates are firmware-specific. SoapyESPSDR documents 8-bit streaming over Gigabit Ethernet and high-speed USB. The VITA-49 firmware reports one gap of five packets over 8.5 hours at 20 MS/s with 10-bit IQ.
> *   ❓ — not calculated; _italic_ — not proven.

### MediaTek

MediaTek (MTK) supplies Wi-Fi chipsets for routers and wireless adapters.

<table><tbody><tr><td><strong>Device</strong></td><td><strong>Chipset</strong></td><td><strong>Sample rate RX, max</strong></td><td><strong>Resolution</strong></td><td><strong>Analog bandwidth</strong></td><td><strong>Frequency range</strong></td><td><strong>Output interface</strong></td><td><strong>Simultaneous IQ channels</strong></td><td><strong>Source</strong></td></tr><tr><td>Gemtek W1700K</td><td>MT7996 with MT7976 and two MT7977</td><td>320 MS/s</td><td>14 bit</td><td>20–320 MHz</td><td><p>2081–2748 MHz</p><p>4647–7509 MHz</p><p>4707–7576 MHz</p></td><td>10G Ethernet</td><td>One</td><td><a href="https://github.com/h0m3us3r/w1700k-sdr">h0m3us3r/w1700k-sdr</a></td></tr><tr><td>COMFAST USB adapter</td><td>MT7961 / MT7921AU with MT7972</td><td>40 MS/s</td><td>14 bit</td><td>40 MHz</td><td>2156–2610 MHz</td><td>USB 3.0</td><td>One</td><td><a href="https://github.com/luigifcruz/BirriaSDR">luigifcruz/BirriaSDR</a></td></tr><tr><td>AX1800 USB adapter (0e8d:7961, model unspecified)</td><td>MT7921AU / MT7961</td><td>80.0032 MS/s</td><td>14 bit</td><td>Unknown</td><td>Unknown</td><td>USB</td><td>Unknown</td><td><a href="https://github.com/MtkWifiRev/Mtk79ICAP#features">Mtk79ICAP</a></td></tr><tr><td>OpenWrt One</td><td>MT7981B with MT7976</td><td>40 MS/s</td><td>14 bit</td><td>20 MHz</td><td><p>2401-2483 MHz</p><p>5170–5260 MHz</p></td><td>2.5G Ethernet</td><td>One</td><td><a href="https://github.com/alphafox02/openwrt-one-sdr">alphafox02/openwrt-one-sdr</a></td></tr></tbody></table>

> **Note:** Bandwidth values are nominal filter settings. BirriaSDR reports an approximately 36 MHz measured passband.
>
> Mtk79ICAP documents capture in the 2400 and 5000 MHz bands with a modified Linux driver and patched firmware. Its continuous 80.0032 MS/s mode requires dense IQ enabled.

#### Tools

[MtkICAPtool](https://github.com/MtkWifiRev/MtkICAPtool)

[MtkCSIdump](https://github.com/MtkWifiRev/MtkCSIdump)

### Realtek

Realtek (RTK) supplies Wi-Fi chipsets for PC wireless cards and adapters.

<table><tbody><tr><td><strong>Device</strong></td><td><strong>Chipset</strong></td><td><strong>Sample rate RX, max</strong></td><td><strong>Resolution</strong></td><td><strong>Analog bandwidth</strong></td><td><strong>Frequency range</strong></td><td><strong>Output interface</strong></td><td><strong>Simultaneous IQ channels</strong></td><td><strong>Source</strong></td></tr><tr><td>RTL8922AE-based card</td><td>RTL8922AE</td><td>160 MS/s</td><td>8 bit</td><td>Unknown</td><td><p>2312–2382 MHz</p><p>2412–2484 MHz</p><p>2500–2515 MHz</p><p>4900–7115 MHz</p></td><td>PCIe</td><td>One</td><td><a href="https://github.com/plaingca/rtl8922-sdr">plaingca/rtl8922-sdr</a></td></tr><tr><td>ASUS USB-AC54_B1</td><td>RTL8822BU</td><td>40 MS/s</td><td>12 bit</td><td>20 MHz (at 20 BW)</td><td><p>2412–2472 MHz</p><p>2484 MHz</p><p>5160–5885 MHz</p></td><td>USB 3</td><td>One</td><td><a href="https://github.com/djObsidian/ac54_sdr">djObsidian/ac54_sdr</a></td></tr><tr><td>RTL8812BU USB adapter (0bda:b812)</td><td>RTL8822B</td><td>80 MS/s (burst)</td><td>12 bit</td><td>Unknown</td><td>Unknown</td><td>USB 2 / USB 3</td><td>Two (USB 3)</td><td><a href="https://github.com/snokvist/wifi-sdr#what-works">snokvist/wifi-sdr</a></td></tr><tr><td>RTL8812CU USB adapter (0bda:c812)</td><td>RTL8822C</td><td>40 MS/s (burst)</td><td>12 bit</td><td>Unknown</td><td>Unknown</td><td>USB 2</td><td>Two</td><td><a href="https://github.com/snokvist/wifi-sdr#what-works">snokvist/wifi-sdr</a></td></tr><tr><td>RTL8812EU USB adapter (0bda:a81a)</td><td>RTL8822E</td><td>40 MS/s (burst)</td><td>Unknown</td><td>Unknown</td><td>Unknown</td><td>USB 2</td><td>Two</td><td><a href="https://github.com/snokvist/wifi-sdr#what-works">snokvist/wifi-sdr</a></td></tr></tbody></table>

> **Note:** The RTL8922AE captures diagnostic IQ after digital processing. Its 8-bit value refers to captured precision.
>
> For the three USB adapters listed by `snokvist/wifi-sdr`, the maximum rates shown are for the project's burst capture path. Upstream reports continuous IQ at 40 MS/s over USB 3 on the RTL8812BU adapter and at 5 MS/s over USB 2 on all three. The tested RTL8812EU board has a front end for the 5000 MHz band only.

### Broadcom

<table><tbody><tr><td><strong>Device</strong></td><td><strong>Chipset</strong></td><td><strong>Sample rate RX, max</strong></td><td><strong>Resolution</strong></td><td><strong>Analog bandwidth</strong></td><td><strong>Frequency range</strong></td><td><strong>Output interface</strong></td><td><strong>Simultaneous IQ channels</strong></td><td><strong>Source</strong></td></tr><tr><td>Broadcom/Cypress WiFi chips</td><td>various, see source</td><td>N/A</td><td>N/A</td><td>Unknown</td><td>2.4 and 5 GHz bands</td><td>SDIO, SPI</td><td>Unknown</td><td><p><a href="https://github.com/seemoo-lab/nexmon">seemoo-lab/nexmon</a></p><p><a href="https://github.com/seemoo-lab/mobisys2018_nexmon_software_defined_radio">seemoo-lab/mobisys2018_nexmon_software_defined_radio</a></p></td></tr></tbody></table>

> **Note:** Nexmon is firmware patching framework for Broadcom/Cypress WiFi chipsets which supports various devices and has arbitrary IQ signals transmission proven. However, exact RF characteristics are not provided and require further investigation

## Projects

Applications built around Wi-Fi chipsets' IQ access.

| Project | Chipset | What it does |
| --- | --- | --- |
| [C5VRX](https://github.com/Twotoz/C5VRX) | ESP32-C5 | Analog FPV video reception around 5800 MHz using the Wi-Fi radio's diagnostic IQ path. BitScrambler demodulation feeds PAL/NTSC composite video through a passive resistor DAC on a Seeed Studio XIAO ESP32-C5. |
| [ESPSoup](https://github.com/pit711/espsoup-firmware) | ESP32-C5 | Signal scanner and analyzer for 2.4 and 5 GHz bands, supports Live spectrum view, BLE advertising, Wi-Fi 802.11b/g/a, Zigbee, Microwave oven, Drone Remote ID, ELRS |
| [FPVGate C5MK](https://github.com/LouisHitchcock/FPVGateC5MK#why-c5mk) | ESP32-C5 | FPV lap timer receiver that derives channel power from raw IQ. It retunes between frequencies for up to eight pilots and can present eight RotorHazard nodes over USB. |
| [wsdr-studio](https://github.com/snokvist/wsdr-studio#wsdr-studio) | RTL8822B / RTL8822C / RTL8822E | Linux desktop spectrum and waterfall viewer with raw IQ recording in SigMF. Recording requires a continuous capture mode. |
| [ESP32 SDR Handheld Scanner](https://github.com/doctormord/ESP32-SDR-Handheld-scanner-with-LCD#how-it-works) | ESP32 / ESP32-S3 | Handheld analyzer that draws a 2400 MHz band waterfall from diagnostic IQ on the LILYGO TTGO T-Display and Guition JC3248W535. Capture timing depends on the board. |
| [ESP-SDR Source for SDR++](https://github.com/z2labs/sdrpp-esp-sdr-source#esp-sdr-source-for-sdr-esp32-s3) | ESP32-S3 | SDR++ source module that streams decimated IQ over USB at up to 0.25 MS/s. Its wideband display uses spectra computed on the chip. |

## Contributing

Have a chipset, measurement, correction, or project to add? Start with [CONTRIBUTING.md](CONTRIBUTING.md) and the [data conventions](docs/CONVENTIONS.md). Claims need primary evidence; unknowns are welcome when clearly labeled. Reviewers use the [review guide](docs/REVIEWING.md), and automated contributors and reviewers follow [AGENTS.md](AGENTS.md).
