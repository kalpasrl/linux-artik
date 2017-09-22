# Linux Kernel for ARTIK KITRA710
## Contents
1. [Introduction](#1-introduction)
2. [Build guide](#2-build-guide)
3. [Update guide](#3-update-guide)

## 1. Introduction
This 'linux-artik' repository is linux kernel source for Kitra710 based on Samsung artik710 SoC
produced by [RushUp](https://www.rushup.tech/).
The kernel in this branch is based on linux-4.1.15 version with changes and integration
developed by [KALPA SRL](http://www.kalpa.it).

---
## 2. Build guide
In order to easily compile binaries you need Docker since we provide a
[docker](https://www.docker.com/) cross-compile-ready environment.

## 2.1 Launch Docker
Move to the kernel folder ("./linux-artik") and launch:
```
../Docker/run.sh
```

## 2.2 Configure and build the kernel

+ Configure
```
cd source
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- -j 4  menuconfig
```

+ Build
```
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- -j 4
```

## 2.3 Compile dts

```
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- -j 4 dtbs
```


## 3. Update Guide

+ Copy compiled binaries into your board.
```
scp arch/arm64/boot/Image root@{YOUR_BOARD_IP}:/root
scp arch/arm64/boot/dts/nexell/*.dtb root@{YOUR_BOARD_IP}:/root
scp usr/modules.img root@{YOUR_BOARD_IP}:/root
```

+ On your board
```
mount -o remount,rw /boot
cp /root/Image /boot
cp /root/*.dtb /boot
dd if=/root/modules.img of=/dev/mmcblk0p2
sync
reboot
```
