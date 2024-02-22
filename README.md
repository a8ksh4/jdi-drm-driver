# JDI Memory LCD Kernel Driver

DRM kernel driver for 2.7" 400x240 JDI memory LCD panel.  This is an adaptation of the Sharp driver from Ardangelo.  This version does not work yet. TBD!!

## Cleaning old drivers

We will use "jdi-drm" as the module name.

The `bbqX0kbd` driver has been renamed to `beepy-kbd`, and `sharp` to `sharp-drm`.

Driver packages will detect if one of these old modules is installed and cancel installation of the package.

Remove the following files:

* `/lib/modules/<uname>/extra/bbqX0kbd.ko*`
* `/lib/modules/<uname>/extra/sharp.ko*`
* `/lib/modules/<uname>/extra/sharp-drm.ko*`
* `/boot/overlays/i2c-bbqX0kbd.dtbo`
* `/boot/overlays/sharp.dtbo`
* ... what else??

Rebuild the module list:

* `depmod -a`

Remove the following lines from `/boot/config.txt`:

* `dtoverlay=bbqX0kbd,irq_pin=4`
* `dtoverlay=sharp`

Remove the following lines from `/etc/modules`:

* `bbqX0kbd`
* `sharp`

## Installation

Install the Linux kernel headers

	sudo apt-get install raspberrypi-kernel-headers


To build, install, and enable the kernel module:

    make
    sudo make install

To remove:

    sudo make uninstall


## [Original fbdev module readme with pinouts and build instructions](https://github.com/w4ilun/Sharp-Memory-LCD-Kernel-Driver/blob/master/README.md)

## References

Original SPI and GPIO kernel driver and the modified JDI version:

	https://github.com/w4ilun/Sharp-Memory-LCD-Kernel-Driver
 	https://github.com/a8ksh4/JDI-LCD-Kernel-Driver
  

Datasheets:

	Sharp: https://www.sharpsde.com/fileadmin/products/Displays/2016_SDE_App_Note_for_Memory_LCD_programming_V1.3.pdf
 	JDI: 
