## Hello All. In this post, I will explain how to use SIM900 Arduino GPRS/GSM shield with Raspberry Pi3 to make calls or send messages.

### Prerequsites:
* Enable RPi serial interface
    ```
    sudo raspi-config
    ```
    Go Interfacing section and disable serial login and enable hardware serial.

* Disable or change bluetooth uart bus to use uart pins. Add dtoverlay settings to config file.
    ```
    sudo nano /boot/configs.txt
    ```
    Disable or change to miniuart.(Please add one of these-disabling is better)
    ```
    dtoverlay=pi3-miniuart-bt
    dtoverlay=pi3-disable-bt
    ```

* Update /boot/cmdline.txt file to use UART for shield. Delete **console=ttyS0/ttyAMA0...** or **console=ttyS0/ttyS0...** text.  
    Old
    ```
    dwc_otg.lpm_enable=0  console=tty1 root...
    ```

    New
    ```
    dwc_otg.lpm_enable=0  console=tty1 console=serial0,115200 root=PARTUUID...
    ```
    
* Connect RPi RX/TX to Shield RX/TX and enable HW Serial from Shield  
     <img src="../resources/SIM900.jpg" width="400"/>
* Run the source code
    ```linux
    sudo python3.5 SIM900.py
    ```
    {% gist hmenn/2dcca83b865c90dd2a12c5e78b59fe28 %}

