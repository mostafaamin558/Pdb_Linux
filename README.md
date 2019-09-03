IoT-LAB Linux Kernel
====================

The board is a Variscite [VAR-SOM-AM35](http://www.variscite.com/products/system-on-module-som/cortex-a8/var-som-am35-cpu-ti-am3517-am3505) without graphic support.

Board support
-------------

  * board support based on am3517evm board from Variscite with kernel 2.6.32 
  * disable USB autosuspend as A8 open nodes may be powered off
  * use NAND ECC 'BCH8' to be able to modify U-boot bch8 options
  * Add a kernel config to toggle NAND read-only/read-write mode
  * add HIDRAW support for SAMRv21 open nodes

> Network card cannot read ethernet address from eeprom. Instead we read it from kernel boot parameter (eg. eth=ETHADDR)

System requirements
-------------------

For Ubuntu and Debian Linux distributions

    $ sudo apt-get install libncurses5-dev

Modify Kernel config
--------------------

Copy defconfig file and edit it with menuconfig 

    $ cp arch/arm/configs/var-som-am35_defconfig .config
    $ make ARCH=arm menuconfig

Create a new defconfig file and update the old one

    $ make ARCH=arm savedefconfig
    $ cp defconfig arch/arm/configs/var-som-am35_defconfig

