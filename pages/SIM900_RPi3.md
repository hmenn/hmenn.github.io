## Hello All. In this post, I will explain how to use SIM900 Arduino GPRS/GSM shield with Raspberry Pi3 to make calls or send messages.

### Prerequsites:
* Enable RPi serial interface
    ```
    sudo raspi-config
    ```
    Go Interfacing section and enable Serial.

* Disable or change bluetooth uart bus to use uart pins. Add dtoverlay settings to config file.
    ```
    sudo nano /boot/configs.txt
    ```
    Disable or change to miniuart.(Please add one of these)
    ```
    dtoverlay=pi3-miniuart-bt
    dtoverlay=pi3-disable-bt
    ```

* Update /boot/cmdline.txt file to use UART for shield. Delete ttyS0/ttyAMA0 text.
    ```
    dwc_otg.lpm_enable=0  console=tty1 console=serial0,115200 root=PARTUUID=2d6ee0c4-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles enable_uart=1
    ```
* Connect RPi RX/TX to Shield RX/TX and enable HW Serial from Shield  
     <img src="../resources/SIM900.jpg" width="400"/>
* Run the source code
    ```linux
    sudo python3.5 SIM900.py
    ```
    {% gist hmenn/2dcca83b865c90dd2a12c5e78b59fe28 %}

