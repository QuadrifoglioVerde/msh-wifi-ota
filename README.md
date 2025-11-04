**Compiled Meshtastic Wi-Fi OTA Firmware**

Potrebna tooly jsou: **esptool, espota, meshtastic**<br>
k sehnani jako exe nebo pythoni verze (nicmene pythoni verze espota.py mi nechodila, cert vi proc)

## Navod:
Zjistime pozici OTA FW v pameti a verzi ESP32, treba zde: https://github.com/meshtastic/firmware/tree/master/variants
najdeme svoje zarizeni a v nem platformio.ini, pokud obsahuje "board_build.partitions = default_8MB.csv" tak je zacatek OTA na 0x340000, jinak 0x260000.

Nahradime OTA v zarizeni (port a nazev.bin nahradte vlastnim!):<br>
**esptool.exe -b 115200 -p COM5 write_flash 0x340000 esp32s3.bin**

Restartujeme zarizeni do OTA rezimu:<br>
**meshtastic --host IP.ADRESA --reboot-ota**

Nahrajeme FW:<br>
**espota.exe -i IP.ADRESA -f firmware-*-update.bin** (VYBRAT verzi -update, jinak to bricknete!)

Puvodni navod:<br>
https://blog.antsu.net/guide-how-to-enable-wi-fi-ota-updates-on-esp32-based-meshtastic-boards/
