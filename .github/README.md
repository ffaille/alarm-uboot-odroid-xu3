This repository hosts a fork of the official [alarm/uboot-odroid-xu3 PKGBUILD](https://github.com/archlinuxarm/PKGBUILDs/tree/master/alarm/uboot-odroid-xu3). It allows you to build the uboot-odroid-xu3 package which provides the bootloader for the ODROID XU3/XU4/HC1/HC2/MC1 (v2020.01 from Hardkernel).

The goal of this project is to offer an up-to-date version while remaining as close as possible to the productions of the official maintainer. Maybe this code can be pushed into the official repository later...

Tested with XU4 only (don't have XU3/HC1/HC2/MC1). Seems to work fine. Feedback is welcome.

## Usage
* sudo pacman -S base-devel git
* git clone https://github.com/ffaille/alarm-uboot-odroid-xu3.git
* cd alarm-uboot-odroid-xu3
* makepkg --syncdeps --noconfirm --log
* sudo pacman -U ./uboot-odroid-xu3-2020.01-1-armv7h.pkg.tar.xz
* sudo reboot