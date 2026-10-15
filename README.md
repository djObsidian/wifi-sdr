# WiFi SDR

List of known WiFi IC's with raw IQ samples available, aka SDR capabilities, projects around these IC's

## IC

Known chipsets grouped by manufacturer

### ESP32

<table><tbody><tr><td><strong>Chip</strong></td><td><strong>Sample rate, max</strong></td><td><strong>Analog bandwidth</strong></td><td><strong>Frequency range</strong></td><td><strong>Max realtime output sample rate</strong></td><td><strong>Source</strong></td></tr><tr><td>ESP32</td><td>80 MS/s</td><td>?</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-S2</td><td>80 MS/s</td><td>60 MHz</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-S3</td><td>80 MS/s</td><td>69 MHz</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td><p><i>32 MS/s, Octal SPI2</i></p><p>80 MS/s, 100 MHz bitbang</p></td><td><p><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></p><p><a href="https://github.com/h0m3us3r/eSpDR">h0m3us3r/eSpDR</a></p></td></tr><tr><td>ESP32-S31</td><td>80 MS/s</td><td>54 MHz</td><td>2400–2483.5 MHz</td><td><p>31.25 MS/s, Gigabit Ethernet</p><p>15 MS/s, USB HS</p></td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C2</td><td>80 MS/s</td><td>20 MHz</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C3</td><td>80 MS/s</td><td>62 MHz</td><td><p>1842–2209 MHz</p><p>2400–2483.5 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C5</td><td>80 MS/s</td><td>48 MHz</td><td><p>2400–2483.5 MHz</p><p>5150–5895 MHz</p></td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C6</td><td>80 MS/s</td><td>54 MHz</td><td>2400–2483.5 MHz</td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr><tr><td>ESP32-C61</td><td>80 MS/s</td><td>54 MHz</td><td>2400–2483.5 MHz</td><td>❓</td><td><a href="https://github.com/ESPARGOS/esp-sdr">ESPARGOS/esp-sdr</a></td></tr></tbody></table>

Max realtime output sample rate calculated as interface bandwidth divided by 32 bit (raw adc iq frame width). As IQ occupies only 20 bit this can be improved in theory.

❓ - not calculated

_Italic_ \- not proven

All radios have 10 bit I and Q samples.

### Mediatek

<table><tbody><tr><td><strong>Device</strong></td><td><strong>Sample rate, max</strong></td><td><strong>Resolution</strong></td><td><strong>Analog bandwidth</strong></td><td><strong>Frequency range</strong></td><td><strong>Output interface</strong></td><td><strong>MIMO</strong></td><td><strong>Chipset</strong></td><td><strong>Source</strong></td></tr><tr><td>W1700K</td><td>320 MS/s</td><td>14 bit</td><td>20–320 MHz</td><td><p>2081-2748 MHz</p><p>4647-7509 MHz</p><p>4707-7576 MHz</p></td><td>10G Ethernet</td><td>4x4</td><td>MT7996</td><td><a href="https://github.com/h0m3us3r/w1700k-sdr">h0m3us3r/w1700k-sdr</a></td></tr><tr><td><p>Comfast CF-951AX/CF-953AX</p><p>(or any with this chipset)</p></td><td>40 MS/s</td><td>14 bit</td><td>40 MHz</td><td>2156-2610 MHz</td><td>USB 3.0</td><td>2x2</td><td><p>MT7961</p><p>MT7921AU</p></td><td><a href="https://github.com/luigifcruz/BirriaSDR">luigifcruz/BirriaSDR</a></td></tr></tbody></table>

MIMO is not currently tested

### Realtek

<table><tbody><tr><td><strong>Device</strong></td><td><strong>Sample rate, max</strong></td><td><strong>Resolution</strong></td><td><strong>Analog bandwidth</strong></td><td><strong>Frequency range</strong></td><td><strong>Output interface</strong></td><td><strong>MIMO</strong></td><td><strong>Chipset</strong></td><td><strong>Source</strong></td></tr><tr><td>RTL8922 based card</td><td>160 MS/s</td><td>?</td><td>160 MHz</td><td><p>2312–2382 MHz</p><p>2412–2484 MHz</p><p>2500–2515 MHz</p><p>4900–7115 MHz</p></td><td>PCI-e 3.0 x1</td><td>2x2</td><td>RTL8922&nbsp;</td><td><a href="https://github.com/plaingca/rtl8922-sdr">plaingca/rtl8922-sdr</a></td></tr></tbody></table>