# PicoPiKBD
PicoPiKBD is a drop-in PCB replacement for the KROM Kernel 100% keyboard.
Building the firmware requires the [Pico SDK](https://github.com/raspberrypi/pico-sdk).
The goal of this project is to release an open-source PCB that reuses most of the original PCB's components and fully supports PC RGB ([RGB .NET](https://github.com/DarthAffe/RGB.NET)/[ArtemisRGB](https://artemis-rgb.com)) and keep the original functions of the keyboard:
- [ ] Toggleable 6/N-Key rollover
- [ ] Media controls
- [ ] Built-in PC RGB control
- [ ] Windows key lock
- [ ] Arrow keys to WASD and vice versa

<sup><sub>*Checked boxes indicate current project status</sub></sup>
## How to use (placeholder until PCB is done and fully working)
1. Load the Pico in boot-mode (pressing the small button on startup) and copy the firmware file (KernelPicoPiRGB.uf2) onto it.
2. Restart the Pico and open the Config-tool. Configure the amount of leds (set channels to 0 if unused) and if needed the used pins.
3. Restart the Pico

The HID-endpoint is usable with default drivers on windows, if you want to use the Bulk-endpoint (better performance for higher amounts of leds) you need to install the libusb driver for it using Zadig (https://zadig.akeo.ie/).
libusb-win32 works best for me, but the others should work too.

If you're using linux you'll likely need to run applications using this device as root. This can be prevented by changing the read/write permissions of the PicoPi-Device by adding a new udev-rule (for example `85-rgbnet.rules`) in your udev rules directory (most likely something like `/etc/udev/rules.d` containing this single line:   
`SUBSYSTEMS=="usb", ATTRS{idVendor}=="1209", ATTRS{idProduct}=="2812", MODE="666"`
