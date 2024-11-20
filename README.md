# Vatilon IPC cameras

I have some cameras from aliexpress, so I was interested what they use "inside".

## Useful links

- [Firmware analysis](https://book.hacktricks.xyz/hardware-physical-access/firmware-analysis)
- [analyzing-firmware-and-extracting-filesystem](https://redfoxsec.com/blog/analyzing-firmware-and-extracting-filesystem/)
- [Hacking asecam part 1](https://www.reddit.com/r/hardwarehacking/comments/1cuu1wf/hacking_an_asecam_ip_camera_part_1/)
- [Hacking asecam part 2](https://www.reddit.com/r/hardwarehacking/comments/1cuui2p/hacking_an_asecam_ip_camera_part_2/)

## OpenIPC
Vatilon boards uses inside fullhan chips: https://openipc.org/cameras/vendors/fullhan

## Vatilon website

- Software for update FW: https://www.vatilon.com/xflrjxz > Batch tools
- Firmware: https://www.vatilon.com/ipcrjxz

## How to bridge WSL2 on windows (I uses windows, but linux tools)
Bridge for WLS2:
https://develmonk.com/2021/06/05/easiest-wsl2-bridge-network-without-hyper-v-virtual-network-manager/
sudo ip addr flush dev eth0
sudo ip addr add 10.0.0.7/24 dev eth0
sudo ip link set eth0 up
sudo ip route add default via 10.0.0.254 dev eth0

## Downlad data from cam
- run tftpd server on pc / or ftp server
- login to camera (`root:ipc@hs66`)

```
tftp -l /dev/mtd0 -r mtd0 -p 10.0.0.7
tftp -l /dev/mtd1 -r mtd1 -p 10.0.0.7
tftp -l /dev/mtd2 -r mtd2 -p 10.0.0.7
tftp -l /dev/mtd3 -r mtd3 -p 10.0.0.7
tftp -l /dev/mtd4 -r mtd4 -p 10.0.0.7
tftp -l /dev/mtd5 -r mtd5 -p 10.0.0.7
```
or
```
ftpput 10.0.0.7 mtd0 /dev/mtd0
ftpput 10.0.0.7 mtd1 /dev/mtd1
ftpput 10.0.0.7 mtd2 /dev/mtd2
ftpput 10.0.0.7 mtd3 /dev/mtd3
ftpput 10.0.0.7 mtd4 /dev/mtd4
ftpput 10.0.0.7 mtd5 /dev/mtd5
```
---
# Instal jefferson (jffs2 extraxtor)
```
sudo apt install python3-pip
sudo apt-get install pipx
pipx install jefferson
pipx ensurepath
```

Info about single cameras in folders.


-----------------------------
Vatilon PB4 (jieuno)
https://www.vatilon.com/productinfo/1634883.html

Device Type: PB4
Serial Number: B5E615C45C1C1851
Uboot Version: uboot-2016-15
Kernel Version: linux-4.9-11
Software Version: V1.13.23-20240524