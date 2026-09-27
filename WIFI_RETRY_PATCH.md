# AP + secondary Wi-Fi reliability patch

This update keeps the PS4 access point active while the ESP32-S2 joins an
optional 2.4 GHz Wi-Fi network.

Changes:

- Forces concurrent AP + station mode when both options are enabled.
- Disables Wi-Fi sleep for a more reliable station connection.
- Retries an unavailable secondary network every 30 seconds.
- Shows station connection status, LAN IP address, and signal level on the
  System Information page.
- Fixes configuration-editor assignments for hostname, USB wait, and sleep
  time.

Configure the secondary SSID and password through `Config Editor`; do not
commit local credentials to this repository. The ESP32-S2 only supports
2.4 GHz Wi-Fi.

The public branch uses DHCP by default. A private deployment may set
`USE_STATIC_WIFI_IP` and the static IP, gateway, subnet, and DNS constants.

Build target used for validation:

`esp32:esp32:esp32s2` with ESP32 Arduino core 2.0.14, all USB-on-boot options
disabled, and the default 4 MB SPIFFS partition scheme.
