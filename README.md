# RetroPie Setup for GPi Case

These steps assume you have built the case already.

1. Download and flash [RetroPie](https://retropie.org.uk/download/) onto SD Card.
2. Leave SD Card mounted, then copy over `config.txt` from this repo.
3. Download the [GPi-Case drivers](http://download.retroflag.com/), copy the overlays into `overlays/` on the SD card.
4. (Optional) Enable SSH: Create an empty file called `ssh` on the root of the SD card
5. (Optional) Enable Wifi: Create a `wpa_supplicant.conf` file on the root of the SD card.

    ```properties
    country=US
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    network={
        ssid="<SSID>"
        psk="<WiFi Password>"
    }
    ```

6. Eject the SD card from host
7. Insert SD card into GPi and boot the first time.
  This first boot will take a couple of minutes and is needed to expand the filesystem to support the roms.
8. After the first boot, copy roms to the unit.

    ```shell
    rsync -Hav --progress --recursive roms/ pi@retropie.localdomain:/home/pi/RetroPie/roms/
    ```

9. (Optional) SSH into the unit and configure [safe shutdown](https://github.com/RetroFlag/retroflag-picase).
10. (Optional) SSH into the unit and [customize the startup splash screen & other things](https://github.com/kloptops/retropie_stuff/blob/master/README.md).
