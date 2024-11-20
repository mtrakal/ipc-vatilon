# Vatilon PB1 (Asecam)

https://www.vatilon.com/productinfo/1634907.html

https://www.aliexpress.com/item/1005006826206612.html

```
telnet 10.0.0.35 2360
root:ipc@hs66
```

```
# cat /usr/app/product
product=IF56N
uboot=8
kernel=4
appfs=10889
ota_url=/fh8856/IF56N/IF56N.bin
```

```
# cat /usr/app/product
product=IF56N
uboot=8
kernel=4
appfs=10889
ota_url=/fh8856/IF56N/IF56N.bin
```

```
# ftpput 10.0.0.7 mtd0 /dev/mtd0
# ftpput 10.0.0.7 mtd1 /dev/mtd1
# ftpput 10.0.0.7 mtd2 /dev/mtd2
# ftpput 10.0.0.7 mtd3 /dev/mtd3
# ftpput 10.0.0.7 mtd4 /dev/mtd4
# ftpput 10.0.0.7 mtd5 /dev/mtd5
```

```
# mount
rootfs on / type rootfs (rw)
proc on /proc type proc (rw,nosuid,nodev,relatime)
sysfs on /sys type sysfs (rw,nosuid,nodev,relatime)
tmpfs on /dev type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,relatime)
tmpfs on /var type tmpfs (rw,relatime)
udev on /dev type tmpfs (rw,relatime)
devpts on /dev/pts type devpts (rw,relatime,mode=600)
/dev/mtdblock2 on /usr/app type squashfs (ro,relatime)
/dev/mtdblock3 on /tmp/etc/custom type jffs2 (rw,relatime)
/dev/mtdblock4 on /tmp/etc/config type jffs2 (rw,relatime)
```

```
# busybox
BusyBox v1.19.3 (2020-08-19 14:57:36 CST) multi-call binary.
Copyright (C) 1998-2011 Erik Andersen, Rob Landley, Denys Vlasenko
and others. Licensed under GPLv2.
See source distribution for full notice.

Usage: busybox [function] [arguments]...
   or: busybox --list[-full]
   or: function [arguments]...

        BusyBox is a multi-call binary that combines many common Unix
        utilities into a single executable.  Most people will create a
        link to busybox for each function they wish to use and BusyBox
        will act like whatever it was invoked as.

Currently defined functions:
        [, [[, ash, awk, bash, cat, chmod, cp, date, dd, df, dhcprelay, dmesg,
        dnsdomainname, du, dumpleases, echo, egrep, env, false, fdisk, fgrep,
        free, fsync, ftpget, ftpput, grep, gunzip, gzip, halt, hostname,
        hwclock, ifconfig, inetd, init, insmod, iostat, kill, killall, linuxrc,
        ln, login, ls, lsmod, lsusb, lzcat, lzma, mdev, mkdir, mkdosfs,
        mkfs.vfat, mknod, modprobe, mount, mpstat, mv, nanddump, nandwrite,
        netstat, ping, ping6, poweroff, ps, pwd, reboot, rm, rmmod, route, sed,
        sh, sleep, sync, tail, tar, telnetd, test, tftp, top, touch, true,
        udhcpc, udhcpd, umount, unlzma, usleep, wc, zcat
```

```
# cat /proc/filesystems
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   tmpfs
nodev   devtmpfs
nodev   debugfs
nodev   sockfs
nodev   usbfs
nodev   pipefs
nodev   anon_inodefs
nodev   rpc_pipefs
nodev   devpts
        squashfs
nodev   ramfs
        vfat
        msdos
nodev   nfs
nodev   nfs4
nodev   jffs2
nodev   mqueue
nodev   mtd_inodefs
```

```
# cat /proc/cpuinfo
Processor       : ARMv6-compatible processor rev 7 (v6l)
```

```
# cat /proc/devices
Character devices:
  1 mem
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  7 vcs
 10 misc
 13 input
 89 i2c
 90 mtd
128 ptm
136 pts
153 spi
180 usb
189 usb_device
252 vbus_ctl
253 fh_spi_slave_0
254 rtc

Block devices:
  1 ramdisk
259 blkext
 31 mtdblock
179 mmc
```

```
# cat /proc/kmsg
<5>[    0.000000] Linux version 3.0.8 (appollo@Trusty) (gcc version 5.5.0 (b220190606) ) #1 Tue Jul 26 18:06:43 CST 2022
<4>[    0.000000] CPU: ARMv6-compatible processor [410fb767] revision 7 (ARMv7), cr=00c5387d
<4>[    0.000000] CPU: VIPT nonaliasing data cache, VIPT nonaliasing instruction cache
<4>[    0.000000] Machine: FH8852
<4>[    0.000000] Memory policy: ECC disabled, Data cache writeback
<7>[    0.000000] On node 0 totalpages: 9216
<7>[    0.000000] free_area_init_node: node 0, pgdat c04d1f7c, node_mem_map c04f1000
<7>[    0.000000]   Normal zone: 72 pages used for memmap
<7>[    0.000000]   Normal zone: 0 pages reserved
<7>[    0.000000]   Normal zone: 9144 pages, LIFO batch:1
<7>[    0.000000] pcpu-alloc: s0 r0 d32768 u32768 alloc=1*32768
<7>[    0.000000] pcpu-alloc: [0] 0
<4>[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 9144
<5>[    0.000000] Kernel command line: mem=36M console=ttyS0,115200 root=/dev/mtdblock2 rootfstype=squashfs mtdparts=spi_flash:320K(uboot),2560K(kernel),4096K(appfs),832K(custom),320K(config),64K(data)
<6>[    0.000000] PID hash table entries: 256 (order: -2, 1024 bytes)
<6>[    0.000000] Dentry cache hash table entries: 8192 (order: 3, 32768 bytes)
<6>[    0.000000] Inode-cache hash table entries: 4096 (order: 2, 16384 bytes)
<6>[    0.000000] Memory: 36MB = 36MB total
<5>[    0.000000] Memory: 31424k/31424k available, 5440k reserved, 0K highmem
<5>[    0.000000] Virtual kernel memory layout:
<5>[    0.000000]     vector  : 0xffff0000 - 0xffff1000   (   4 kB)
<5>[    0.000000]     fixmap  : 0xfff00000 - 0xfffe0000   ( 896 kB)
<5>[    0.000000]     DMA     : 0xffc00000 - 0xffe00000   (   2 MB)
<5>[    0.000000]     vmalloc : 0xc2800000 - 0xfe000000   ( 952 MB)
<5>[    0.000000]     lowmem  : 0xc0000000 - 0xc2400000   (  36 MB)
<5>[    0.000000]     modules : 0xbf000000 - 0xc0000000   (  16 MB)
<5>[    0.000000]       .init : 0xc0008000 - 0xc00e5000   ( 884 kB)
<5>[    0.000000]       .text : 0xc00e5000 - 0xc04ae000   (3876 kB)
<5>[    0.000000]       .data : 0xc04ae000 - 0xc04d2600   ( 146 kB)
<5>[    0.000000]        .bss : 0xc04d2624 - 0xc04f07f8   ( 121 kB)
<6>[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
<6>[    0.000000] NR_IRQS:128
<6>[    0.000000] timer mult: 0xa0000000, timer shift: 0x1b
<6>[    0.000000] sched_clock: 32 bits at 50MHz, resolution 20ns, wraps every 85899ms
<6>[    0.000000] Console: colour dummy device 80x30
<6>[    0.000000] console [ttyS0] enabled
<6>[    0.176985] Calibrating delay loop... 597.60 BogoMIPS (lpj=2988032)
<6>[    0.240009] pid_max: default: 32768 minimum: 301
<6>[    0.244624] Mount-cache hash table entries: 512
<6>[    0.249343] CPU: Testing write buffer coherency: ok
<6>[    0.254486] devtmpfs: initialized
<6>[    0.259713] NET: Registered protocol family 16
<6>[    0.264219] FH8856 board init
<6>[    0.331929] bio: create slab <bio-0> at 0
<6>[    0.333730] cannot get dmac0_hclk
<6>[    0.338507] fh_dmac fh_dmac.0: FH DMA Controller, 6 channels
<6>[    0.344291] usbcore: registered new interface driver usbfs
<6>[    0.348049] usbcore: registered new interface driver hub
<6>[    0.353243] usbcore: registered new device driver usb
<6>[    0.361209] cfg80211: Calling CRDA to update world regulatory domain
<6>[    0.366632] Switching to clocksource fh_clocksource
<6>[    0.370064] Switched to NOHz mode on CPU #0
<6>[    0.408404] NET: Registered protocol family 2
<6>[    0.410100] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.417132] TCP established hash table entries: 2048 (order: 2, 16384 bytes)
<6>[    0.423850] TCP bind hash table entries: 2048 (order: 1, 8192 bytes)
<6>[    0.430118] TCP: Hash tables configured (established 2048 bind 2048)
<6>[    0.436343] TCP reno registered
<6>[    0.439464] UDP hash table entries: 256 (order: 0, 4096 bytes)
<6>[    0.445297] UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
<6>[    0.451847] NET: Registered protocol family 1
<6>[    0.456294] RPC: Registered named UNIX socket transport module.
<6>[    0.461715] RPC: Registered udp transport module.
<6>[    0.466322] RPC: Registered tcp transport module.
<6>[    0.471020] RPC: Registered tcp NFSv4.1 backchannel transport module.
<6>[    1.895922] squashfs: version 4.0 (2009/01/31) Phillip Lougher
<6>[    1.917614] JFFS2 version 2.2. (NAND) © 2001-2006 Red Hat, Inc.
<6>[    1.930206] msgmni has been set to 61
<6>[    1.940993] NET: Registered protocol family 38
<6>[    1.942625] io scheduler noop registered (default)
<4>[    1.957132] fh_pwm_probe: clk_rate: 50000000
<6>[    1.963176] PWM driver, Number: 8, IO base addr: 0xc3070000
<6>[    1.975211] ttyS.0: ttyS0 at MMIO 0xf0700000 (irq = 30) is a ttyS
<7>[    1.983427] fh serial probe done
<6>[    1.983515] ttyS.1: ttyS1 at MMIO 0xf0800000 (irq = 31) is a ttyS
<7>[    1.995569] fh serial probe done
<6>[    2.005588] brd: module loaded
<6>[    2.042260] CLK misc driver init successfully
<4>[    2.075515] m25p80 spi0.0: found BY25Q64AS, expected m25p80
<3>[    2.078508] m25p80 spi0.0: set_qe : 235  default not support multi wire..
<6>[    2.085966] m25p80 spi0.0: BY25Q64AS (8192 Kbytes)
<4>[    2.091167] DEBUG-CMDLINE-PART: parsing <320K(uboot),2560K(kernel),4096K(appfs),832K(custom),320K(config),64K(data)>
<4>[    2.102669] DEBUG-CMDLINE-PART: partition 5: name <data>, offset ffffffff, size 10000, mask flags 0
<4>[    2.112548] DEBUG-CMDLINE-PART: partition 4: name <config>, offset ffffffff, size 50000, mask flags 0
<4>[    2.122618] DEBUG-CMDLINE-PART: partition 3: name <custom>, offset ffffffff, size d0000, mask flags 0
<4>[    2.132690] DEBUG-CMDLINE-PART: partition 2: name <appfs>, offset ffffffff, size 400000, mask flags 0
<4>[    2.142765] DEBUG-CMDLINE-PART: partition 1: name <kernel>, offset ffffffff, size 280000, mask flags 0
<4>[    2.152934] DEBUG-CMDLINE-PART: partition 0: name <uboot>, offset ffffffff, size 50000, mask flags 0
<4>[    2.162913] DEBUG-CMDLINE-PART: mtdid=<spi_flash> num_parts=<6>
<5>[    2.169360] 6 cmdlinepart partitions found on MTD device spi_flash
<5>[    2.176137] Creating 6 MTD partitions on "spi_flash":
<5>[    2.181660] 0x000000000000-0x000000050000 : "uboot"
<5>[    2.206846] 0x000000050000-0x0000002d0000 : "kernel"
<5>[    2.227795] 0x0000002d0000-0x0000006d0000 : "appfs"
<5>[    2.248690] 0x0000006d0000-0x0000007a0000 : "custom"
<5>[    2.269910] 0x0000007a0000-0x0000007f0000 : "config"
<5>[    2.290223] 0x0000007f0000-0x000000800000 : "data"
<6>[    2.343404] console [netcon0] enabled
<6>[    2.344288] netconsole: network logging started
<7>[    2.349229] Module fh_common_port init
<3>[    2.381596] resource: start=e0700000, len=00100000
<3>[    2.383779] base=0xc3200000 (after adjust)
<6>[    2.388286] fh_otg_driver_probe: mapped PA 0xe0700000 to VA 0xc3200000
<4>[    2.495294] Core Release: 4.00a
<4>[    2.495615] Setting default values for core params
<3>[    2.700393] dma_enable :1
<3>[    2.700416] dma_desc_enable :1
<4>[    2.903041] Using Descriptor DMA mode
<4>[    2.903929] Periodic Transfer Interrupt Enhancement - disabled
<4>[    2.910322] Multiprocessor Interrupt Enhancement - disabled
<4>[    2.916380] OTG VER PARAM: 0, OTG VER FLAG: 0
<3>[    2.921158] FH OTG HCD INIT (c1059780)
<3>[    2.925222] hcd regs before base(c3200000)
<6>[    2.929747] fh_otg fh_otg: FH OTG Controller
<7>[    2.934408] drivers/usb/core/inode.c: creating file 'devices'
<7>[    2.934444] drivers/usb/core/inode.c: creating file '001'
<6>[    2.934474] fh_otg fh_otg: new USB bus registered, assigned bus number 1
<6>[    2.941755] fh_otg fh_otg: irq 27, io mem 0x00000000
<4>[    2.947106] Init: Power Port (0)
<7>[    2.950698] usb usb1: default language 0x0409
<7>[    2.950753] usb usb1: udev 1, busnum 1, minor = 0
<6>[    2.950773] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
<6>[    2.958010] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    2.965938] usb usb1: Product: FH OTG Controller
<6>[    2.970965] usb usb1: Manufacturer: Linux 3.0.8 fh_otg_hcd
<6>[    2.976920] usb usb1: SerialNumber: fh_otg
<7>[    2.986296] usb usb1: usb_probe_device
<7>[    2.986327] usb usb1: configuration #1 chosen from 1 choice
<7>[    2.986390] usb usb1: adding 1-0:1.0 (config #1, interface 0)
<7>[    2.987086] hub 1-0:1.0: usb_probe_interface
<7>[    2.987113] hub 1-0:1.0: usb_probe_interface - got id
<6>[    2.987130] hub 1-0:1.0: USB hub found
<6>[    2.988134] hub 1-0:1.0: 1 port detected
<7>[    2.992442] hub 1-0:1.0: standalone hub
<7>[    2.992460] hub 1-0:1.0: ganged power switching
<7>[    2.992475] hub 1-0:1.0: individual port over-current protection
<7>[    2.992492] hub 1-0:1.0: Single TT
<7>[    2.992508] hub 1-0:1.0: TT requires at most 8 FS bit times (666 ns)
<7>[    2.992527] hub 1-0:1.0: power on to power good time: 2ms
<7>[    2.992568] hub 1-0:1.0: local power source is good
<7>[    2.992589] hub 1-0:1.0: enabling power on all ports
<7>[    2.999693] drivers/usb/core/inode.c: creating file '001'
<6>[    3.001872] i2c /dev entries driver
<6>[    3.006986] I2C driver:
<6>[    3.007000]       platform registration...
<6>[    3.010552]       Clock: 50000khz, Standard-mode HCNT:LCNT = 212:249
<6>[    3.017101]       tx fifo depth: 16, rx fifo depth: 16
<6>[    3.030053]       I2C - (dev. name: fh_i2c - id: 0, IRQ #11
<6>[    3.030065]               IO base addr: 0xc30a0000)
<6>[    3.036769] I2C driver:
<6>[    3.036777]       platform registration...
<6>[    3.043409]       Clock: 50000khz, Standard-mode HCNT:LCNT = 212:249
<6>[    3.049994]       tx fifo depth: 16, rx fifo depth: 16
<6>[    3.074592]       I2C - (dev. name: fh_i2c - id: 1, IRQ #12
<6>[    3.074604]               IO base addr: 0xc30a8000)
<7>[    3.089737] hub 1-0:1.0: state 7 ports 1 chg 0000 evt 0000
<6>[    3.108758] card0 disconnected!
<6>[    3.123820] TCP cubic registered
<6>[    3.124238] NET: Registered protocol family 17
<6>[    3.129141] lib80211: common routines for IEEE802.11 drivers
<7>[    3.135321] lib80211_crypt: registered algorithm 'NULL'
<5>[    3.135344] Registering the dns_resolver key type
<6>[    3.140473] VFP support v0.3: implementor 41 architecture 1 part 20 variant b rev 5
<6>[    3.188209] GMAC driver:
<6>[    3.188223]       platform registration...
<4>[    3.191903]       using random MAC address: 6a:63:6f:8a:b4:b8
<4>[    3.200928] fh_gmac fh_gmac.0: eth0: mixed HW and IP checksum settings.
<4>[    3.205056] fh_gmac fh_gmac.0: eth0: mixed no checksumming and other settings.
<6>[    3.213170]       eth0 - (dev. name: fh_gmac - id: 0, IRQ #15
<6>[    3.213183]               IO base addr: 0xc30c8000)
<3>[    3.250922] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
<6>[    3.286469] aes driver registered
<6>[    3.290551] Freeing init memory: 884K
<6>[    4.527351] Video Memory Manager
<7>[    4.527397] media_mem_parse_cmdline: s=anonymous,0,0xa2400000,90M.
<7>[    4.527418] media_mem_parse_cmdline: i=4.
<7>[    4.527438] vmm:anonymous,a2400000,5a00000.
<4>[    4.609203] load rtthread_arc_human_detect.bin at 0xa7f00000, set ring buffer at 0xa7e00000 with size 0x10000
<6>[    4.609277] get irq offset: 0
<6>[    4.612293] chn0 dev nr: 252
<6>[    4.626494] VBus loaded: 255 in blocks, 255 out blocks
<6>[    4.626515] VBUS driver loaded.
<6>[    4.626532] VBUS load rtthread_arc_human_detect.bin for rtvbus
<4>[    5.043130] firmware: rtthread_arc_human_detect.bin loaded
<4>[    5.043257] firmware: rtthread_arc_human_detect.bin started
<6>[    5.043271] ARC is running.
<4>[    5.105497] media_process: module license 'Proprietary' taints kernel.
<4>[    5.105524] Disabling lock debugging due to kernel taint
<5>[    5.143020] [MEDIA]media_process_module_init 276: media process init success!!
<4>[    5.180110] module->phys_addr=0xe8400000  module->virt_addr=0xc3400000

<6>[    5.180141]       isp - (dev. name: ispp - IRQ #7
<6>[    5.180149]               IO base addr: 0xc3400000)
<4>[    5.180213] module->phys_addr=0xe8500000  module->virt_addr=0xc3600000

<6>[    5.180235]       isp - (dev. name: ispf - IRQ #8
<6>[    5.180243]               IO base addr: 0xc3600000)
<4>[    5.180256]
<4>[    5.180261]       stat buffer size: 68KBytes
<5>[    5.277639] [VPU]vpu_module_init 727: vpu init success!!
<7>[    5.415049] [ENC]pae_cpu_reset 40: [PAE]---RESET PAE---
<7>[    5.449623] [ENC]pae_load_firmware 34: START LOAD ENC FIRMWARE V2 ...
<7>[    5.449727] [ENC]pae_load_firmware 37: LOAD ENC FIRMWARE FINISH!
<5>[    5.449746] [ENC]pae_module_init 327: PAE init success!
<5>[    5.847559] [HEVC]hevc_module_init 226: HEVC init success!
<5>[    5.916375] [JPEG]jpeg_module_init 190: JPEG init success!
<4>[    5.949427] ACW_VBUS version:             V1.2.0(g25ecbbe)
<7>[    5.961614] [VPU]vpu_parse_cmdline 349: VPU Revc Command: vi_2560_1440
<7>[    5.961655] [VPU]vpu_parse_cmdline 638: set command success! (vi)
<7>[    5.961953] [VPU]vpu_parse_cmdline 349: VPU Revc Command: cap_0_3840_2160
<7>[    5.961992] [VPU]vpu_parse_cmdline 638: set command success! (cap)
<7>[    5.962266] [VPU]vpu_parse_cmdline 349: VPU Revc Command: cap_1_800_576
<7>[    5.962304] [VPU]vpu_parse_cmdline 638: set command success! (cap)
<7>[    5.962571] [VPU]vpu_parse_cmdline 349: VPU Revc Command: support4k_on
<7>[    5.962610] [VPU]vpu_parse_cmdline 638: set command success! (support4k)
<7>[    5.962878] [VPU]vpu_parse_cmdline 349: VPU Revc Command: buf_0_2
<7>[    5.962915] [VPU]vpu_parse_cmdline 638: set command success! (buf)
<7>[    5.963206] [VPU]vpu_parse_cmdline 349: VPU Revc Command: buf_1_2
<7>[    5.963242] [VPU]vpu_parse_cmdline 638: set command success! (buf)
<7>[    5.963512] [VPU]vpu_parse_cmdline 349: VPU Revc Command: sublimit_off
<7>[    5.963553] [VPU]vpu_parse_cmdline 638: set command success! (sublimit)
<7>[    5.965081] [ENC]pae_parse_cmdline 217: ENC Revc Command: stm_2621440
<7>[    5.965129] [ENC]pae_parse_cmdline 635: set command success! (stm)
<7>[    5.965412] [HEVC]hevc_parse_cmdline 146: ENC Revc Command: stm_2621440
<7>[    5.965457] [HEVC]hevc_parse_cmdline 494: set command success! (stm)
<7>[    5.965734] [HEVC]hevc_parse_cmdline 146: ENC Revc Command: usebfrm_0
<7>[    5.965777] [HEVC]hevc_parse_cmdline 494: set command success! (usebfrm)
<7>[    5.966050] [JPEG]jpeg_parse_cmdline 183: JPEG Revc Command: mem_1_131072
<7>[    5.966086] [JPEG]jpeg_parse_cmdline 270: set command success! (mem)
<7>[    5.966352] [JPEG]jpeg_parse_cmdline 183: JPEG Revc Command: mjpg_0_0
<7>[    5.966383] [JPEG]jpeg_parse_cmdline 270: set command success! (mjpg)
<6>[    7.646960] gmac_rmii: probed
<6>[    7.647291] eth0: PHY ID 937c4024 at 0 IRQ -1 (0:00) active
<4>[    7.648264] fh_gmac fh_gmac.0: eth0: mixed HW and IP checksum settings.
<4>[    7.648290] fh_gmac fh_gmac.0: eth0: mixed no checksumming and other settings.
<6>[    9.640020] PHY: 0:00 - Link is Up - 100/Full
<4>[   11.741511] set period: 0x1f4
<4>[   11.741530] set duty: 0x0
<4>[   11.741540] set phase: 0x0
<4>[   11.741549] set delay: 0x0
<4>[   11.741559] set ctrl: 0x1
<4>[   11.741569] set pulses: 0x0
<4>[   11.741589] set pwm 7, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<7>[   11.813885] [MEDIA]fh_media_open 111: media_process open success.
<7>[   11.814262] [ENC]pae_enc_isr 3285: [PAE]---PAE RUN!!---
<7>[   11.829911] [ENC]pae_open 69: pae open success!
<7>[   11.836868] [HEVC]hevc_open 42: hevc open success!
<7>[   11.838340] [JPEG]jpeg_open 35: jpeg open success.
<7>[   11.838565] [VPU]vpu_open 544: vpu open success.
<7>[   11.838859] remap_pfn_range start~end: 0x401ab000 0x401d8000, pyh:0xa2400 , nocached.
<7>[   11.852147] remap_pfn_range start~end: 0x40725000 0x41f86000, pyh:0xa242d , nocached.
<7>[   11.853188] remap_pfn_range start~end: 0x42030000 0x42182000, pyh:0xa3c8e , nocached.
<7>[   11.853666] remap_pfn_range start~end: 0x4219e000 0x42539000, pyh:0xa3de0 , nocached.
<7>[   11.855302] remap_pfn_range start~end: 0x40412000 0x40468000, pyh:0xa417b , nocached.
<7>[   11.909881] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 1 0x0 0 0
<7>[   11.909913] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 5 0x0 0 0
<7>[   11.909977] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 2 0x0 0 0
<7>[   11.912595] remap_pfn_range start~end: 0x42539000 0x441d0000, pyh:0xa41e0 , nocached.
<7>[   11.942389] remap_pfn_range start~end: 0x441d0000 0x45cbc000, pyh:0xa5e77 , nocached.
<7>[   11.942748] remap_pfn_range start~end: 0x45db9000 0x45f62000, pyh:0xa7963 , nocached.
<4>[   12.148401] set period: 0x1f4
<4>[   12.148429] set duty: 0x0
<4>[   12.148439] set phase: 0x0
<4>[   12.148448] set delay: 0x0
<4>[   12.148459] set ctrl: 0x1
<4>[   12.148469] set pulses: 0x0
<4>[   12.148491] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<7>[   13.085223] [VPU]vpu_disable 2734: wait vpu stop...
<7>[   13.085248] [VPU]vpu_disable 2745: vpu stop!
<7>[   13.259746] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 19 0x0 0 0
<7>[   13.260884] remap_pfn_range start~end: 0x400b1000 0x400b2000, pyh:0xa7b0c , nocached.
<7>[   13.261021] remap_pfn_range start~end: 0x401d9000 0x401df000, pyh:0xa7b0d , nocached.
<7>[   13.321835] remap_pfn_range start~end: 0x404ab000 0x404ac000, pyh:0xa7b13 , nocached.
<7>[   13.321989] remap_pfn_range start~end: 0x405f0000 0x405f8000, pyh:0xa7b14 , nocached.
<7>[   13.419809] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 20 0x0 0 0
<7>[   13.420995] remap_pfn_range start~end: 0x400f1000 0x400f2000, pyh:0xa7b1c , nocached.
<7>[   13.421172] remap_pfn_range start~end: 0x401df000 0x401e5000, pyh:0xa7b1d , nocached.
<7>[   13.455228] remap_pfn_range start~end: 0x404ac000 0x404ad000, pyh:0xa7b23 , nocached.
<7>[   13.455401] remap_pfn_range start~end: 0x405f8000 0x40600000, pyh:0xa7b24 , nocached.
<6>[   13.462604] get fd: 23, prio: 20
<7>[   13.465867] remap_pfn_range start~end: 0x41f90000 0x41ff3000, pyh:0xa7b2c , nocached.
<7>[   13.466574] remap_pfn_range start~end: 0x404ad000 0x404df000, pyh:0xa7b8f , nocached.
<7>[   13.787135] remap_pfn_range start~end: 0x41ff3000 0x42025000, pyh:0xa7bc1 , nocached.
<7>[   14.061880] remap_pfn_range start~end: 0x45cbc000 0x45db4000, pyh:0xa7bf3 , nocached.
<4>[   14.127256] [wdt] set topval: 5set period: 0x1f4
<4>[   16.355536] set duty: 0x1a9
<4>[   16.355554] set phase: 0x0
<4>[   16.355563] set delay: 0x0
<4>[   16.355573] set ctrl: 0x1
<4>[   16.355583] set pulses: 0x0
<4>[   16.355605] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[   23.357328] set period: 0x1f4
<4>[   23.357351] set duty: 0x0
<4>[   23.357361] set phase: 0x0
<4>[   23.357370] set delay: 0x0
<4>[   23.357383] set ctrl: 0x1
<4>[   23.357393] set pulses: 0x0
<4>[   23.357419] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[   27.560485] set period: 0x1f4
<4>[   27.560509] set duty: 0x1a9
<4>[   27.560519] set phase: 0x0
<4>[   27.560528] set delay: 0x0
<4>[   27.560538] set ctrl: 0x1
<4>[   27.560549] set pulses: 0x0
<4>[   27.560571] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[   34.562265] set period: 0x1f4
<4>[   34.562289] set duty: 0x0
<4>[   34.562301] set phase: 0x0
<4>[   34.562310] set delay: 0x0
<4>[   34.562320] set ctrl: 0x1
<4>[   34.562330] set pulses: 0x0
<4>[   34.562352] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[   38.765219] set period: 0x1f4
<4>[   38.765243] set duty: 0x1a9
<4>[   38.765253] set phase: 0x0
<4>[   38.765261] set delay: 0x0
<4>[   38.765271] set ctrl: 0x1
<4>[   38.765282] set pulses: 0x0
<4>[   38.765304] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[   45.767063] set period: 0x1f4
<4>[   45.767090] set duty: 0x0
<4>[   45.767100] set phase: 0x0
<4>[   45.767109] set delay: 0x0
<4>[   45.767120] set ctrl: 0x1
<4>[   45.767131] set pulses: 0x0
<4>[   45.767156] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[   49.970099] set period: 0x1f4
<4>[   49.970122] set duty: 0x1a9
<4>[   49.970132] set phase: 0x0
<4>[   49.970141] set delay: 0x0
<4>[   49.970151] set ctrl: 0x1
<4>[   49.970161] set pulses: 0x0
<4>[   49.970184] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 1496.191978] set period: 0x1f4
<4>[ 1496.192001] set duty: 0x0
<4>[ 1496.192010] set phase: 0x0
<4>[ 1496.192019] set delay: 0x0
<4>[ 1496.192029] set ctrl: 0x1
<4>[ 1496.192040] set pulses: 0x0
<4>[ 1496.192061] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 1500.394961] set period: 0x1f4
<4>[ 1500.394982] set duty: 0x1a9
<4>[ 1500.394992] set phase: 0x0
<4>[ 1500.395000] set delay: 0x0
<4>[ 1500.395011] set ctrl: 0x1
<4>[ 1500.395021] set pulses: 0x0
<4>[ 1500.395041] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 1506.396407] set period: 0x1f4
<4>[ 1506.396429] set duty: 0x0
<4>[ 1506.396438] set phase: 0x0
<4>[ 1506.396447] set delay: 0x0
<4>[ 1506.396457] set ctrl: 0x1
<4>[ 1506.396467] set pulses: 0x0
<4>[ 1506.396490] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 1510.599298] set period: 0x1f4
<4>[ 1510.599318] set duty: 0x1a9
<4>[ 1510.599328] set phase: 0x0
<4>[ 1510.599337] set delay: 0x0
<4>[ 1510.599347] set ctrl: 0x1
<4>[ 1510.599357] set pulses: 0x0
<4>[ 1510.599379] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 1517.600758] set period: 0x1f4
<4>[ 1517.600779] set duty: 0x0
<4>[ 1517.600789] set phase: 0x0
<4>[ 1517.600798] set delay: 0x0
<4>[ 1517.600808] set ctrl: 0x1
<4>[ 1517.600818] set pulses: 0x0
<4>[ 1517.600839] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 1521.804697] set period: 0x1f4
<4>[ 1521.804719] set duty: 0x1a9
<4>[ 1521.804729] set phase: 0x0
<4>[ 1521.804737] set delay: 0x0
<4>[ 1521.804748] set ctrl: 0x1
<4>[ 1521.804758] set pulses: 0x0
<4>[ 1521.804780] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 1527.809295] set period: 0x1f4
<4>[ 1527.809316] set duty: 0x0
<4>[ 1527.809326] set phase: 0x0
<4>[ 1527.809334] set delay: 0x0
<4>[ 1527.809344] set ctrl: 0x1
<4>[ 1527.809354] set pulses: 0x0
<4>[ 1527.809376] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 1532.012383] set period: 0x1f4
<4>[ 1532.012407] set duty: 0x1a9
<4>[ 1532.012417] set phase: 0x0
<4>[ 1532.012425] set delay: 0x0
<4>[ 1532.012436] set ctrl: 0x1
<4>[ 1532.012447] set pulses: 0x0
<4>[ 1532.012469] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 2979.221291] set period: 0x1f4
<4>[ 2979.221318] set duty: 0x0
<4>[ 2979.221329] set phase: 0x0
<4>[ 2979.221339] set delay: 0x0
<4>[ 2979.221350] set ctrl: 0x1
<4>[ 2979.221361] set pulses: 0x0
<4>[ 2979.221386] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 2983.424206] set period: 0x1f4
<4>[ 2983.424229] set duty: 0x1a9
<4>[ 2983.424239] set phase: 0x0
<4>[ 2983.424248] set delay: 0x0
<4>[ 2983.424258] set ctrl: 0x1
<4>[ 2983.424268] set pulses: 0x0
<4>[ 2983.424290] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 2989.425842] set period: 0x1f4
<4>[ 2989.425873] set duty: 0x0
<4>[ 2989.425885] set phase: 0x0
<4>[ 2989.425894] set delay: 0x0
<4>[ 2989.425906] set ctrl: 0x1
<4>[ 2989.425917] set pulses: 0x0
<4>[ 2989.425939] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 2993.629161] set period: 0x1f4
<4>[ 2993.629184] set duty: 0x1a9
<4>[ 2993.629195] set phase: 0x0
<4>[ 2993.629204] set delay: 0x0
<4>[ 2993.629214] set ctrl: 0x1
<4>[ 2993.629225] set pulses: 0x0
<4>[ 2993.629249] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 3000.631021] set period: 0x1f4
<4>[ 3000.631044] set duty: 0x0
<4>[ 3000.631054] set phase: 0x0
<4>[ 3000.631063] set delay: 0x0
<4>[ 3000.631074] set ctrl: 0x1
<4>[ 3000.631084] set pulses: 0x0
<4>[ 3000.631106] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 3004.834007] set period: 0x1f4
<4>[ 3004.834031] set duty: 0x1a9
<4>[ 3004.834041] set phase: 0x0
<4>[ 3004.834050] set delay: 0x0
<4>[ 3004.834060] set ctrl: 0x1
<4>[ 3004.834070] set pulses: 0x0
<4>[ 3004.834093] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 3010.835830] set period: 0x1f4
<4>[ 3010.835858] set duty: 0x0
<4>[ 3010.835867] set phase: 0x0
<4>[ 3010.835876] set delay: 0x0
<4>[ 3010.835886] set ctrl: 0x1
<4>[ 3010.835897] set pulses: 0x0
<4>[ 3010.835921] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 3015.038842] set period: 0x1f4
<4>[ 3015.038865] set duty: 0x1a9
<4>[ 3015.038875] set phase: 0x0
<4>[ 3015.038884] set delay: 0x0
<4>[ 3015.038895] set ctrl: 0x1
<4>[ 3015.038905] set pulses: 0x0
<4>[ 3015.038928] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 4461.242943] set period: 0x1f4
<4>[ 4461.242970] set duty: 0x0
<4>[ 4461.242980] set phase: 0x0
<4>[ 4461.242989] set delay: 0x0
<4>[ 4461.243000] set ctrl: 0x1
<4>[ 4461.243011] set pulses: 0x0
<4>[ 4461.243034] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 4465.445918] set period: 0x1f4
<4>[ 4465.445942] set duty: 0x1a9
<4>[ 4465.445953] set phase: 0x0
<4>[ 4465.445962] set delay: 0x0
<4>[ 4465.445972] set ctrl: 0x1
<4>[ 4465.445983] set pulses: 0x0
<4>[ 4465.446007] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 4472.448212] set period: 0x1f4
<4>[ 4472.448236] set duty: 0x0
<4>[ 4472.448245] set phase: 0x0
<4>[ 4472.448254] set delay: 0x0
<4>[ 4472.448265] set ctrl: 0x1
<4>[ 4472.448275] set pulses: 0x0
<4>[ 4472.448298] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 4476.652340] set period: 0x1f4
<4>[ 4476.652359] set duty: 0x1a9
<4>[ 4476.652369] set phase: 0x0
<4>[ 4476.652378] set delay: 0x0
<4>[ 4476.652388] set ctrl: 0x1
<4>[ 4476.652398] set pulses: 0x0
<4>[ 4476.652418] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 4482.655166] set period: 0x1f4
<4>[ 4482.655189] set duty: 0x0
<4>[ 4482.655198] set phase: 0x0
<4>[ 4482.655207] set delay: 0x0
<4>[ 4482.655218] set ctrl: 0x1
<4>[ 4482.655228] set pulses: 0x0
<4>[ 4482.655250] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 4486.860052] set period: 0x1f4
<4>[ 4486.860071] set duty: 0x1a9
<4>[ 4486.860080] set phase: 0x0
<4>[ 4486.860089] set delay: 0x0
<4>[ 4486.860099] set ctrl: 0x1
<4>[ 4486.860109] set pulses: 0x0
<4>[ 4486.860130] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 4493.861548] set period: 0x1f4
<4>[ 4493.861570] set duty: 0x0
<4>[ 4493.861580] set phase: 0x0
<4>[ 4493.861588] set delay: 0x0
<4>[ 4493.861599] set ctrl: 0x1
<4>[ 4493.861609] set pulses: 0x0
<4>[ 4493.861630] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 4498.064370] set period: 0x1f4
<4>[ 4498.064389] set duty: 0x1a9
<4>[ 4498.064398] set phase: 0x0
<4>[ 4498.064407] set delay: 0x0
<4>[ 4498.064417] set ctrl: 0x1
<4>[ 4498.064426] set pulses: 0x0
<4>[ 4498.064447] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 5944.287146] set period: 0x1f4
<4>[ 5944.287172] set duty: 0x0
<4>[ 5944.287182] set phase: 0x0
<4>[ 5944.287192] set delay: 0x0
<4>[ 5944.287202] set ctrl: 0x1
<4>[ 5944.287214] set pulses: 0x0
<4>[ 5944.287238] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 5948.490178] set period: 0x1f4
<4>[ 5948.490200] set duty: 0x1a9
<4>[ 5948.490211] set phase: 0x0
<4>[ 5948.490220] set delay: 0x0
<4>[ 5948.490230] set ctrl: 0x1
<4>[ 5948.490241] set pulses: 0x0
<4>[ 5948.490264] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 5955.492744] set period: 0x1f4
<4>[ 5955.492770] set duty: 0x0
<4>[ 5955.492780] set phase: 0x0
<4>[ 5955.492789] set delay: 0x0
<4>[ 5955.492801] set ctrl: 0x1
<4>[ 5955.492812] set pulses: 0x0
<4>[ 5955.492835] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 5959.695853] set period: 0x1f4
<4>[ 5959.695880] set duty: 0x1a9
<4>[ 5959.695890] set phase: 0x0
<4>[ 5959.695899] set delay: 0x0
<4>[ 5959.695909] set ctrl: 0x1
<4>[ 5959.695920] set pulses: 0x0
<4>[ 5959.695943] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 5965.697513] set period: 0x1f4
<4>[ 5965.697536] set duty: 0x0
<4>[ 5965.697547] set phase: 0x0
<4>[ 5965.697556] set delay: 0x0
<4>[ 5965.697568] set ctrl: 0x1
<4>[ 5965.697579] set pulses: 0x0
<4>[ 5965.697604] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 5969.900617] set period: 0x1f4
<4>[ 5969.900639] set duty: 0x1a9
<4>[ 5969.900651] set phase: 0x0
<4>[ 5969.900659] set delay: 0x0
<4>[ 5969.900670] set ctrl: 0x1
<4>[ 5969.900681] set pulses: 0x0
<4>[ 5969.900704] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 5976.902422] set period: 0x1f4
<4>[ 5976.902448] set duty: 0x0
<4>[ 5976.902459] set phase: 0x0
<4>[ 5976.902468] set delay: 0x0
<4>[ 5976.902479] set ctrl: 0x1
<4>[ 5976.902490] set pulses: 0x0
<4>[ 5976.902513] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[ 5981.105552] set period: 0x1f4
<4>[ 5981.105577] set duty: 0x1a9
<4>[ 5981.105589] set phase: 0x0
<4>[ 5981.105598] set delay: 0x0
<4>[ 5981.105608] set ctrl: 0x1
<4>[ 5981.105618] set pulses: 0x0
<4>[ 5981.105640] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
```

```
# cat /proc/meminfo
MemTotal:          32308 kB
MemFree:           12832 kB
Buffers:             192 kB
Cached:             8232 kB
SwapCached:            0 kB
Active:             4624 kB
Inactive:           7684 kB
Active(anon):       3896 kB
Inactive(anon):     4644 kB
Active(file):        728 kB
Inactive(file):     3040 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:          3904 kB
Mapped:             3000 kB
Shmem:              4656 kB
Slab:               3432 kB
SReclaimable:        412 kB
SUnreclaim:         3020 kB
KernelStack:         728 kB
PageTables:          456 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:       16152 kB
Committed_AS:      52964 kB
VmallocTotal:     974848 kB
VmallocUsed:       38476 kB
VmallocChunk:     916472 kB
```

```
# cat /proc/mounts
rootfs / rootfs rw 0 0
proc /proc proc rw,nosuid,nodev,relatime 0 0
sysfs /sys sysfs rw,nosuid,nodev,relatime 0 0
tmpfs /dev tmpfs rw,relatime 0 0
tmpfs /tmp tmpfs rw,relatime 0 0
tmpfs /var tmpfs rw,relatime 0 0
udev /dev tmpfs rw,relatime 0 0
devpts /dev/pts devpts rw,relatime,mode=600 0 0
/dev/mtdblock2 /usr/app squashfs ro,relatime 0 0
/dev/mtdblock3 /tmp/etc/custom jffs2 rw,relatime 0 0
/dev/mtdblock4 /tmp/etc/config jffs2 rw,relatime 0 0
```

```
# cat /proc/mtd
dev:    size   erasesize  name
mtd0: 00050000 00001000 "uboot"
mtd1: 00280000 00001000 "kernel"
mtd2: 00400000 00001000 "appfs"
mtd3: 000d0000 00001000 "custom"
mtd4: 00050000 00001000 "config"
mtd5: 00010000 00001000 "data"
```

```
# cat /proc/partitions
major minor  #blocks  name

  31        0        320 mtdblock0
  31        1       2560 mtdblock1
  31        2       4096 mtdblock2
  31        3        832 mtdblock3
  31        4        320 mtdblock4
  31        5         64 mtdblock5
```

```
# cat /proc/version
Linux version 3.0.8 (appollo@Trusty) (gcc version 5.5.0 (b220190606) ) #1 Tue Jul 26 18:06:43 CST 2022
```

```
# cat /proc/vmallocinfo
0xbf000000-0xbf003000   12288 module_alloc_update_bounds+0x14/0x64 pages=2 vmalloc
0xbf006000-0xbf00e000   32768 module_alloc_update_bounds+0x14/0x64 pages=7 vmalloc
0xbf013000-0xbf038000  151552 module_alloc_update_bounds+0x14/0x64 pages=36 vmalloc
0xbf041000-0xbf04d000   49152 module_alloc_update_bounds+0x14/0x64 pages=11 vmalloc
0xbf051000-0xbf069000   98304 module_alloc_update_bounds+0x14/0x64 pages=23 vmalloc
0xbf06f000-0xbf08c000  118784 module_alloc_update_bounds+0x14/0x64 pages=28 vmalloc
0xbf092000-0xbf0f4000  401408 module_alloc_update_bounds+0x14/0x64 pages=97 vmalloc
0xbf0fe000-0xbf10e000   65536 module_alloc_update_bounds+0x14/0x64 pages=15 vmalloc
0xbf112000-0xbf114000    8192 module_alloc_update_bounds+0x14/0x64 pages=1 vmalloc
0xc2804000-0xc2806000    8192 fh_dma_probe+0x78/0x604 ioremap
0xc300f000-0xc3052000  274432 jffs2_zlib_init+0x1c/0xb4 pages=66 vmalloc
0xc3052000-0xc305e000   49152 jffs2_zlib_init+0x50/0xb4 pages=11 vmalloc
0xc305e000-0xc3060000    8192 0xbf00e11c ioremap
0xc3060000-0xc3065000   20480 fh_gpio_probe+0xc0/0x214 ioremap
0xc3066000-0xc3068000    8192 0xbf0380a0 ioremap
0xc3068000-0xc306d000   20480 fh_gpio_probe+0xc0/0x214 ioremap
0xc306e000-0xc3070000    8192 0xbf0380c0 ioremap
0xc3070000-0xc3075000   20480 fh_pwm_probe+0x9c/0x34c ioremap
0xc3078000-0xc307d000   20480 fh_sadc_probe+0xc8/0x1f8 ioremap
0xc307e000-0xc3080000    8192 0xbf08c190 ioremap
0xc3080000-0xc3085000   20480 fh_efuse_probe+0xac/0x148 ioremap
0xc3086000-0xc3088000    8192 0xbf08c218 ioremap
0xc3088000-0xc308d000   20480 fh_spi_probe+0x130/0x684 ioremap
0xc3090000-0xc3095000   20480 fh_spi_probe+0x130/0x684 ioremap
0xc3096000-0xc3098000    8192 0xbf10e07c ioremap
0xc3098000-0xc309d000   20480 fh_spi_slave_probe+0x16c/0x500 ioremap
0xc30a0000-0xc30a5000   20480 fh_i2c_probe+0x16c/0x364 ioremap
0xc30a8000-0xc30ad000   20480 fh_i2c_probe+0x16c/0x364 ioremap
0xc30ae000-0xc30b0000    8192 pae_sys_mem_init+0x78/0x324 [enc] ioremap
0xc30b0000-0xc30b5000   20480 devm_ioremap_nocache+0x40/0x7c ioremap
0xc30b6000-0xc30b8000    8192 pae_sys_mem_init+0xd8/0x324 [enc] ioremap
0xc30b8000-0xc30bd000   20480 fh_mci_probe+0x214/0x470 ioremap
0xc30be000-0xc30c0000    8192 pae_sys_mem_init+0x11c/0x324 [enc] ioremap
0xc30c0000-0xc30c5000   20480 fh_mci_probe+0x214/0x470 ioremap
0xc30c8000-0xc30cd000   20480 fh_gmac_probe+0x100/0x370 ioremap
0xc30d0000-0xc30d5000   20480 fh_aes_probe+0xdc/0x2fc ioremap
0xc30d5000-0xc30e6000   69632 xz_dec_lzma2_create+0x64/0x8c pages=16 vmalloc
0xc30f8000-0xc30fc000   16384 0xbf0690a8 ioremap
0xc3100000-0xc3111000   69632 0xbf00e0e4 ioremap
0xc3111000-0xc318c000  503808 firmware_loading_store+0x150/0x1c4
0xc31f6000-0xc31f8000    8192 fh_ioremap+0x30/0x58 [isp] ioremap
0xc31f8000-0xc31fd000   20480 fullhan_init_vdi+0x24/0xdc [hevc] ioremap
0xc31fe000-0xc3200000    8192 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3200000-0xc3301000 1052672 fh_otg_driver_probe+0x178/0x8c8 ioremap
0xc3302000-0xc3304000    8192 hevc_chn_mem_init+0x6ac/0xb7c [hevc] ioremap
0xc3310000-0xc3319000   36864 0xbf08c130 ioremap
0xc332c000-0xc332f000   12288 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3330000-0xc3338000   32768 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3340000-0xc3361000  135168 0xbf08c1d4 ioremap
0xc3362000-0xc3364000    8192 hevc_chn_mem_init+0x6ac/0xb7c [hevc] ioremap
0xc3364000-0xc3367000   12288 hevc_chn_mem_init+0x704/0xb7c [hevc] ioremap
0xc3368000-0xc336f000   28672 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3400000-0xc3501000 1052672 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3580000-0xc35ae000  188416 vpu_sys_mem_init+0x54/0x408 [vpu] ioremap
0xc35b0000-0xc35b9000   36864 hevc_chn_mem_init+0x824/0xb7c [hevc] ioremap
0xc35f0000-0xc35f9000   36864 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3600000-0xc3701000 1052672 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3710000-0xc3719000   36864 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3720000-0xc3732000   73728 hevc_chn_mem_init+0x704/0xb7c [hevc] ioremap
0xc3740000-0xc3761000  135168 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3770000-0xc377f000   61440 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3780000-0xc37d7000  356352 hevc_sys_mem_init+0x54/0x2f4 [hevc] ioremap
0xc3800000-0xc3953000 1388544 vpu_set_chn_mem+0x114/0x688 [vpu] ioremap
0xc3980000-0xc39d5000  348160 vdi_init+0xb0/0x3c0 [hevc] ioremap
0xc3b00000-0xc3b9c000  638976 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3bc0000-0xc3be1000  135168 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3c00000-0xc3e81000 2625536 media_stream_buff_malloc+0x8c/0xd0 [media_process] ioremap
0xc4000000-0xc5862000 25567232 vpu_set_chn_mem+0x114/0x688 [vpu] ioremap
0xc5b80000-0xc5bfc000  507904 hevc_chn_mem_init+0x824/0xb7c [hevc] ioremap
0xc5c00000-0xc5c83000  536576 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc5d00000-0xc5d83000  536576 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc5e00000-0xc5e47000  290816 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc6000000-0xc6102000 1056768 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
```

```
# cat /proc/vmstat
nr_free_pages 3209
nr_inactive_anon 1161
nr_active_anon 974
nr_inactive_file 760
nr_active_file 182
nr_unevictable 0
nr_mlock 0
nr_anon_pages 976
nr_mapped 750
nr_file_pages 2106
nr_dirty 0
nr_writeback 0
nr_slab_reclaimable 102
nr_slab_unreclaimable 756
nr_page_table_pages 112
nr_kernel_stack 91
nr_unstable 0
nr_bounce 0
nr_vmscan_write 0
nr_writeback_temp 0
nr_isolated_anon 0
nr_isolated_file 0
nr_shmem 1164
nr_dirtied 0
nr_written 0
nr_anon_transparent_hugepages 0
nr_dirty_threshold 830
nr_dirty_background_threshold 415
pgpgin 2736
pgpgout 0
pswpin 0
pswpout 0
pgalloc_normal 112705
pgalloc_movable 0
pgfree 115917
pgactivate 446
pgdeactivate 94
pgfault 119155
pgmajfault 8
pgrefill_normal 0
pgrefill_movable 0
pgsteal_normal 0
pgsteal_movable 0
pgscan_kswapd_normal 0
pgscan_kswapd_movable 0
pgscan_direct_normal 0
pgscan_direct_movable 0
pginodesteal 0
slabs_scanned 1536
kswapd_steal 0
kswapd_inodesteal 0
kswapd_low_wmark_hit_quickly 0
kswapd_high_wmark_hit_quickly 0
kswapd_skip_congestion_wait 0
pageoutrun 0
allocstall 0
pgrotated 6
unevictable_pgs_culled 0
unevictable_pgs_scanned 0
unevictable_pgs_rescued 0
unevictable_pgs_mlocked 0
unevictable_pgs_munlocked 0
unevictable_pgs_cleared 0
unevictable_pgs_stranded 0
unevictable_pgs_mlockfreed 0
```

```
tar cf - / | ftpput 10.0.0.7 root.tar -
tar cf - /usr/ | ftpput 10.0.0.7 usr.tar -
tar cf - /proc/ | ftpput 10.0.0.7 proc.tar -
``` 

---
On PC:

```
sudo binwalk -Me --run-as=root mtd1
sudo binwalk -Me --run-as=root mtd2
sudo binwalk -Me --run-as=root mtd3
sudo binwalk -Me --run-as=root mtd4
sudo binwalk -Me --run-as=root mtd5
```
 