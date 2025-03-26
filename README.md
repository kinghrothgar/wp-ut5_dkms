# Realtek r8152 DKMS

![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/awesometic/realtek-r8152-dkms?sort=semver&style=for-the-badge)

This driver forked from [awesometic/realtek-r8152-dkms](https://github.com/awesometic/realtek-r8152-dkms)

This provides WP-UT5 driver in DKMS way so that you can keep the latest driver even after the kernel upgrade.

## Compatibility

This driver supports [WisdPi USB 3.2 to 5GbE adapter (WP-UT5)](https://www.wisdpi.com/products/wisdpi-usb-3-2-5g-ethernet-adapter-wp-ut5-wired-lan-network-connection-for-mac-os-linux-windows-backward-compatible-on-5g-2-5g-1g-100mbps-ideal-for-gaming) and some other USB Ethernet chipsets.

> Refers to the official websites, you can check it at the bottom of this document

Chipset          | Interface   | Performance
:----------------|:-----------:|:----------------:
RTL8157          | USB 3.0     | 5 GbE
RTL8156 /B       | USB 3.0     | 2.5 GbE
RTL8153 /B/C/D/E | USB 3.0     | 10/100/1000 MbE
RTL8154 /B       | USB 2.0     | 10/100/1000 MbE
RTL8152B         | USB 2.0     | 10/100M

## Installation Scripts

There are 2 scripts (autorun.sh or dkms-install.sh) to install the driver module. `autorun.sh` installs the module for the  current kernel, while `dkms-install.sh` installs the module as a dkms, which will automatically build and install the module when a new kernel is installed.

### clone code

```
git clone https://github.com/wisdpi/wp-ut5_dkms.git

```
> If you use **Raspberry Pi OS**, please checkout the raspios branch
```
git clone -b raspios https://github.com/wisdpi/wp-ut5_dkms.git

```

### autorun.sh

Using the `autorun.sh` script that Realtek provides on their original driver package. This is **not installed as a DKMS**, only efforts to the current kernel.

Download or clone this repository and move to the extracted directory, then run the script.

```bash
sudo ./autorun.sh
```

### dkms-install.sh

This script is from aircrack-ng team. You can install the DKMS module by a simple command.

Download or clone this repository and move to the extracted directory, then run the script.

```bash
sudo ./dkms-install.sh
```

## Debian package build

This method is similar to the dkms-install.sh, but is a package instead. First install the needed dependancies:

```bash
sudo apt install devscripts debmake debhelper build-essential dkms dh-dkms
```

Then build the package:

```bash
dpkg-buildpackage -b -rfakeroot -us -uc
```

The `realtek-r8152-dkms_*.deb` will be located in the folder above where the command was run.

## LICENSE

GPL-2 on Realtek driver and the debian packaing.

## References

- [Realtek r8152 driver downloads](https://www.realtek.com/Download/List?cate_id=585)
