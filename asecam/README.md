# Asecam

```
uboot-2010-8
linux-3.0.8-4
FW: V1.08.89-20220801
```

Motion detect, human detect in settings.

```
# cat /usr/app/product
product=IF56N
uboot=8
kernel=4
appfs=10889
ota_url=/fh8856/IF56N/IF56N.bin
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
BogoMIPS        : 597.60
Features        : swp half thumb fastmult vfp edsp java
CPU implementer : 0x41
CPU architecture: 7
CPU variant     : 0x0
CPU part        : 0xb76
CPU revision    : 7

Hardware        : FH8852
Revision        : 0000
Serial          : 0000000000000000
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
<6>[    0.176982] Calibrating delay loop... 597.60 BogoMIPS (lpj=2988032)
<6>[    0.240009] pid_max: default: 32768 minimum: 301
<6>[    0.244625] Mount-cache hash table entries: 512
<6>[    0.249345] CPU: Testing write buffer coherency: ok
<6>[    0.254482] devtmpfs: initialized
<6>[    0.259707] NET: Registered protocol family 16
<6>[    0.264201] FH8856 board init
<6>[    0.331984] bio: create slab <bio-0> at 0
<6>[    0.333785] cannot get dmac0_hclk
<6>[    0.338564] fh_dmac fh_dmac.0: FH DMA Controller, 6 channels
<6>[    0.344332] usbcore: registered new interface driver usbfs
<6>[    0.348099] usbcore: registered new interface driver hub
<6>[    0.353298] usbcore: registered new device driver usb
<6>[    0.361269] cfg80211: Calling CRDA to update world regulatory domain
<6>[    0.366689] Switching to clocksource fh_clocksource
<6>[    0.370061] Switched to NOHz mode on CPU #0
<6>[    0.408545] NET: Registered protocol family 2
<6>[    0.410241] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.417267] TCP established hash table entries: 2048 (order: 2, 16384 bytes)
<6>[    0.423988] TCP bind hash table entries: 2048 (order: 1, 8192 bytes)
<6>[    0.430257] TCP: Hash tables configured (established 2048 bind 2048)
<6>[    0.436483] TCP reno registered
<6>[    0.439606] UDP hash table entries: 256 (order: 0, 4096 bytes)
<6>[    0.445439] UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
<6>[    0.451988] NET: Registered protocol family 1
<6>[    0.456430] RPC: Registered named UNIX socket transport module.
<6>[    0.461855] RPC: Registered udp transport module.
<6>[    0.466464] RPC: Registered tcp transport module.
<6>[    0.471160] RPC: Registered tcp NFSv4.1 backchannel transport module.
<6>[    1.895938] squashfs: version 4.0 (2009/01/31) Phillip Lougher
<6>[    1.917666] JFFS2 version 2.2. (NAND) © 2001-2006 Red Hat, Inc.
<6>[    1.930267] msgmni has been set to 61
<6>[    1.941052] NET: Registered protocol family 38
<6>[    1.942686] io scheduler noop registered (default)
<4>[    1.957140] fh_pwm_probe: clk_rate: 50000000
<6>[    1.963183] PWM driver, Number: 8, IO base addr: 0xc3070000
<6>[    1.975100] ttyS.0: ttyS0 at MMIO 0xf0700000 (irq = 30) is a ttyS
<7>[    1.983314] fh serial probe done
<6>[    1.983401] ttyS.1: ttyS1 at MMIO 0xf0800000 (irq = 31) is a ttyS
<7>[    1.995448] fh serial probe done
<6>[    2.005406] brd: module loaded
<6>[    2.041897] CLK misc driver init successfully
<4>[    2.075286] m25p80 spi0.0: found BY25Q64AS, expected m25p80
<3>[    2.078279] m25p80 spi0.0: set_qe : 235  default not support multi wire..
<6>[    2.085737] m25p80 spi0.0: BY25Q64AS (8192 Kbytes)
<4>[    2.090939] DEBUG-CMDLINE-PART: parsing <320K(uboot),2560K(kernel),4096K(appfs),832K(custom),320K(config),64K(data)>
<4>[    2.102440] DEBUG-CMDLINE-PART: partition 5: name <data>, offset ffffffff, size 10000, mask flags 0
<4>[    2.112319] DEBUG-CMDLINE-PART: partition 4: name <config>, offset ffffffff, size 50000, mask flags 0
<4>[    2.122390] DEBUG-CMDLINE-PART: partition 3: name <custom>, offset ffffffff, size d0000, mask flags 0
<4>[    2.132463] DEBUG-CMDLINE-PART: partition 2: name <appfs>, offset ffffffff, size 400000, mask flags 0
<4>[    2.142536] DEBUG-CMDLINE-PART: partition 1: name <kernel>, offset ffffffff, size 280000, mask flags 0
<4>[    2.152707] DEBUG-CMDLINE-PART: partition 0: name <uboot>, offset ffffffff, size 50000, mask flags 0
<4>[    2.162684] DEBUG-CMDLINE-PART: mtdid=<spi_flash> num_parts=<6>
<5>[    2.169132] 6 cmdlinepart partitions found on MTD device spi_flash
<5>[    2.175910] Creating 6 MTD partitions on "spi_flash":
<5>[    2.181431] 0x000000000000-0x000000050000 : "uboot"
<5>[    2.206621] 0x000000050000-0x0000002d0000 : "kernel"
<5>[    2.227716] 0x0000002d0000-0x0000006d0000 : "appfs"
<5>[    2.248661] 0x0000006d0000-0x0000007a0000 : "custom"
<5>[    2.269928] 0x0000007a0000-0x0000007f0000 : "config"
<5>[    2.290283] 0x0000007f0000-0x000000800000 : "data"
<6>[    2.343711] console [netcon0] enabled
<6>[    2.344595] netconsole: network logging started
<7>[    2.349536] Module fh_common_port init
<3>[    2.381657] resource: start=e0700000, len=00100000
<3>[    2.383839] base=0xc3200000 (after adjust)
<6>[    2.388346] fh_otg_driver_probe: mapped PA 0xe0700000 to VA 0xc3200000
<4>[    2.495361] Core Release: 4.00a
<4>[    2.495681] Setting default values for core params
<3>[    2.700447] dma_enable :1
<3>[    2.700471] dma_desc_enable :1
<4>[    2.903082] Using Descriptor DMA mode
<4>[    2.903970] Periodic Transfer Interrupt Enhancement - disabled
<4>[    2.910362] Multiprocessor Interrupt Enhancement - disabled
<4>[    2.916421] OTG VER PARAM: 0, OTG VER FLAG: 0
<3>[    2.921199] FH OTG HCD INIT (c1054980)
<3>[    2.925263] hcd regs before base(c3200000)
<6>[    2.929789] fh_otg fh_otg: FH OTG Controller
<7>[    2.934452] drivers/usb/core/inode.c: creating file 'devices'
<7>[    2.934486] drivers/usb/core/inode.c: creating file '001'
<6>[    2.934517] fh_otg fh_otg: new USB bus registered, assigned bus number 1
<6>[    2.941796] fh_otg fh_otg: irq 27, io mem 0x00000000
<4>[    2.947146] Init: Power Port (0)
<7>[    2.950738] usb usb1: default language 0x0409
<7>[    2.950791] usb usb1: udev 1, busnum 1, minor = 0
<6>[    2.950812] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
<6>[    2.958051] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    2.965979] usb usb1: Product: FH OTG Controller
<6>[    2.971004] usb usb1: Manufacturer: Linux 3.0.8 fh_otg_hcd
<6>[    2.976960] usb usb1: SerialNumber: fh_otg
<7>[    2.986313] usb usb1: usb_probe_device
<7>[    2.986344] usb usb1: configuration #1 chosen from 1 choice
<7>[    2.986405] usb usb1: adding 1-0:1.0 (config #1, interface 0)
<7>[    2.987103] hub 1-0:1.0: usb_probe_interface
<7>[    2.987131] hub 1-0:1.0: usb_probe_interface - got id
<6>[    2.987149] hub 1-0:1.0: USB hub found
<6>[    2.988153] hub 1-0:1.0: 1 port detected
<7>[    2.992460] hub 1-0:1.0: standalone hub
<7>[    2.992481] hub 1-0:1.0: ganged power switching
<7>[    2.992496] hub 1-0:1.0: individual port over-current protection
<7>[    2.992513] hub 1-0:1.0: Single TT
<7>[    2.992530] hub 1-0:1.0: TT requires at most 8 FS bit times (666 ns)
<7>[    2.992549] hub 1-0:1.0: power on to power good time: 2ms
<7>[    2.992591] hub 1-0:1.0: local power source is good
<7>[    2.992611] hub 1-0:1.0: enabling power on all ports
<7>[    2.999730] drivers/usb/core/inode.c: creating file '001'
<6>[    3.000403] i2c /dev entries driver
<6>[    3.007046] I2C driver:
<6>[    3.007059]       platform registration...
<6>[    3.010612]       Clock: 50000khz, Standard-mode HCNT:LCNT = 212:249
<6>[    3.017160]       tx fifo depth: 16, rx fifo depth: 16
<6>[    3.030129]       I2C - (dev. name: fh_i2c - id: 0, IRQ #11
<6>[    3.030141]               IO base addr: 0xc30a0000)
<6>[    3.036843] I2C driver:
<6>[    3.036850]       platform registration...
<6>[    3.043482]       Clock: 50000khz, Standard-mode HCNT:LCNT = 212:249
<6>[    3.050070]       tx fifo depth: 16, rx fifo depth: 16
<6>[    3.074741]       I2C - (dev. name: fh_i2c - id: 1, IRQ #12
<6>[    3.074753]               IO base addr: 0xc30a8000)
<7>[    3.089846] hub 1-0:1.0: state 7 ports 1 chg 0000 evt 0000
<6>[    3.109048] card0 disconnected!
<6>[    3.124023] TCP cubic registered
<6>[    3.124441] NET: Registered protocol family 17
<6>[    3.129346] lib80211: common routines for IEEE802.11 drivers
<7>[    3.135524] lib80211_crypt: registered algorithm 'NULL'
<5>[    3.135546] Registering the dns_resolver key type
<6>[    3.140677] VFP support v0.3: implementor 41 architecture 1 part 20 variant b rev 5
<6>[    3.188244] GMAC driver:
<6>[    3.188258]       platform registration...
<4>[    3.191939]       using random MAC address: 9a:83:c1:7c:d1:df
<4>[    3.201002] fh_gmac fh_gmac.0: eth0: mixed HW and IP checksum settings.
<4>[    3.205130] fh_gmac fh_gmac.0: eth0: mixed no checksumming and other settings.
<6>[    3.213241]       eth0 - (dev. name: fh_gmac - id: 0, IRQ #15
<6>[    3.213255]               IO base addr: 0xc30c8000)
<3>[    3.250913] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
<6>[    3.286484] aes driver registered
<6>[    3.290567] Freeing init memory: 884K
<6>[    4.508656] Video Memory Manager
<7>[    4.508702] media_mem_parse_cmdline: s=anonymous,0,0xa2400000,90M.
<7>[    4.508722] media_mem_parse_cmdline: i=4.
<7>[    4.508742] vmm:anonymous,a2400000,5a00000.
<4>[    4.589488] load rtthread_arc_human_detect.bin at 0xa7f00000, set ring buffer at 0xa7e00000 with size 0x10000
<6>[    4.589561] get irq offset: 0
<6>[    4.592094] chn0 dev nr: 252
<6>[    4.606234] VBus loaded: 255 in blocks, 255 out blocks
<6>[    4.606255] VBUS driver loaded.
<6>[    4.606270] VBUS load rtthread_arc_human_detect.bin for rtvbus
<4>[    5.028135] firmware: rtthread_arc_human_detect.bin loaded
<4>[    5.028263] firmware: rtthread_arc_human_detect.bin started
<6>[    5.028277] ARC is running.
<4>[    5.085536] media_process: module license 'Proprietary' taints kernel.
<4>[    5.085561] Disabling lock debugging due to kernel taint
<5>[    5.125916] [MEDIA]media_process_module_init 276: media process init success!!
<4>[    5.160154] module->phys_addr=0xe8400000  module->virt_addr=0xc3400000
<6>[    5.160186]       isp - (dev. name: ispp - IRQ #7
<6>[    5.160194]               IO base addr: 0xc3400000)
<4>[    5.160258] module->phys_addr=0xe8500000  module->virt_addr=0xc3600000
<6>[    5.160280]       isp - (dev. name: ispf - IRQ #8
<6>[    5.160289]               IO base addr: 0xc3600000)
<4>[    5.160302]
<4>[    5.160306]       stat buffer size: 68KBytes
<5>[    5.269820] [VPU]vpu_module_init 727: vpu init success!!
<7>[    5.401337] [ENC]pae_cpu_reset 40: [PAE]---RESET PAE---
<7>[    5.439691] [ENC]pae_load_firmware 34: START LOAD ENC FIRMWARE V2 ...
<7>[    5.439789] [ENC]pae_load_firmware 37: LOAD ENC FIRMWARE FINISH!
<5>[    5.439809] [ENC]pae_module_init 327: PAE init success!
<5>[    5.837935] [HEVC]hevc_module_init 226: HEVC init success!
<5>[    5.906445] [JPEG]jpeg_module_init 190: JPEG init success!
<4>[    5.939434] ACW_VBUS version:             V1.2.0(g25ecbbe)
<7>[    5.951693] [VPU]vpu_parse_cmdline 349: VPU Revc Command: vi_2560_1440
<7>[    5.951734] [VPU]vpu_parse_cmdline 638: set command success! (vi)
<7>[    5.952040] [VPU]vpu_parse_cmdline 349: VPU Revc Command: cap_0_3840_2160
<7>[    5.952079] [VPU]vpu_parse_cmdline 638: set command success! (cap)
<7>[    5.952355] [VPU]vpu_parse_cmdline 349: VPU Revc Command: cap_1_800_576
<7>[    5.952393] [VPU]vpu_parse_cmdline 638: set command success! (cap)
<7>[    5.952668] [VPU]vpu_parse_cmdline 349: VPU Revc Command: support4k_on
<7>[    5.952707] [VPU]vpu_parse_cmdline 638: set command success! (support4k)
<7>[    5.952979] [VPU]vpu_parse_cmdline 349: VPU Revc Command: buf_0_2
<7>[    5.953015] [VPU]vpu_parse_cmdline 638: set command success! (buf)
<7>[    5.953314] [VPU]vpu_parse_cmdline 349: VPU Revc Command: buf_1_2
<7>[    5.953350] [VPU]vpu_parse_cmdline 638: set command success! (buf)
<7>[    5.953629] [VPU]vpu_parse_cmdline 349: VPU Revc Command: sublimit_off
<7>[    5.953667] [VPU]vpu_parse_cmdline 638: set command success! (sublimit)
<7>[    5.955228] [ENC]pae_parse_cmdline 217: ENC Revc Command: stm_2621440
<7>[    5.955275] [ENC]pae_parse_cmdline 635: set command success! (stm)
<7>[    5.955559] [HEVC]hevc_parse_cmdline 146: ENC Revc Command: stm_2621440
<7>[    5.955601] [HEVC]hevc_parse_cmdline 494: set command success! (stm)
<7>[    5.955880] [HEVC]hevc_parse_cmdline 146: ENC Revc Command: usebfrm_0
<7>[    5.955922] [HEVC]hevc_parse_cmdline 494: set command success! (usebfrm)
<7>[    5.956203] [JPEG]jpeg_parse_cmdline 183: JPEG Revc Command: mem_1_131072
<7>[    5.956239] [JPEG]jpeg_parse_cmdline 270: set command success! (mem)
<7>[    5.956512] [JPEG]jpeg_parse_cmdline 183: JPEG Revc Command: mjpg_0_0
<7>[    5.956545] [JPEG]jpeg_parse_cmdline 270: set command success! (mjpg)
<6>[    7.637056] gmac_rmii: probed
<6>[    7.637387] eth0: PHY ID 937c4024 at 0 IRQ -1 (0:00) active
<4>[    7.638366] fh_gmac fh_gmac.0: eth0: mixed HW and IP checksum settings.
<4>[    7.638394] fh_gmac fh_gmac.0: eth0: mixed no checksumming and other settings.
<6>[    9.630091] PHY: 0:00 - Link is Up - 100/Full
<4>[   11.831619] set period: 0x1f4
<4>[   11.831639] set duty: 0x0
<4>[   11.831648] set phase: 0x0
<4>[   11.831656] set delay: 0x0
<4>[   11.831667] set ctrl: 0x1
<4>[   11.831676] set pulses: 0x0
<4>[   11.831697] set pwm 7, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<7>[   11.905610] [MEDIA]fh_media_open 111: media_process open success.
<7>[   11.905986] [ENC]pae_enc_isr 3285: [PAE]---PAE RUN!!---
<7>[   11.919771] [ENC]pae_open 69: pae open success!
<7>[   11.928410] [HEVC]hevc_open 42: hevc open success!
<7>[   11.929791] [JPEG]jpeg_open 35: jpeg open success.
<7>[   11.930018] [VPU]vpu_open 544: vpu open success.
<7>[   11.930316] remap_pfn_range start~end: 0x407fc000 0x40829000, pyh:0xa2400 , nocached.
<7>[   11.933511] remap_pfn_range start~end: 0x40915000 0x42176000, pyh:0xa242d , nocached.
<7>[   11.934576] remap_pfn_range start~end: 0x421c3000 0x42315000, pyh:0xa3c8e , nocached.
<7>[   11.935051] remap_pfn_range start~end: 0x42344000 0x426df000, pyh:0xa3de0 , nocached.
<7>[   11.939893] remap_pfn_range start~end: 0x4275b000 0x427b1000, pyh:0xa417b , nocached.
<7>[   11.981647] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 1 0x0 0 0
<7>[   11.981679] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 5 0x0 0 0
<7>[   11.981746] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 2 0x0 0 0
<7>[   11.984366] remap_pfn_range start~end: 0x427c9000 0x44460000, pyh:0xa41e0 , nocached.
<7>[   12.022399] remap_pfn_range start~end: 0x44460000 0x45f4c000, pyh:0xa5e77 , nocached.
<7>[   12.022747] remap_pfn_range start~end: 0x45fe1000 0x4618a000, pyh:0xa7963 , nocached.
<4>[   12.240730] set period: 0x1f4
<4>[   12.240758] set duty: 0x0
<4>[   12.240769] set phase: 0x0
<4>[   12.240778] set delay: 0x0
<4>[   12.240788] set ctrl: 0x1
<4>[   12.240802] set pulses: 0x0
<4>[   12.240823] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<7>[   13.289907] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 19 0x0 0 0
<7>[   13.291133] remap_pfn_range start~end: 0x400e3000 0x400e4000, pyh:0xa7b0c , nocached.
<7>[   13.291286] remap_pfn_range start~end: 0x4010e000 0x40114000, pyh:0xa7b0d , nocached.
<7>[   13.399839] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 20 0x0 0 0
<7>[   13.400878] remap_pfn_range start~end: 0x40064000 0x40065000, pyh:0xa7b13 , nocached.
<7>[   13.401033] remap_pfn_range start~end: 0x40086000 0x4008c000, pyh:0xa7b14 , nocached.
<6>[   13.410059] get fd: 19, prio: 20
<7>[   13.413392] remap_pfn_range start~end: 0x405a9000 0x4060c000, pyh:0xa7b1a , nocached.
<7>[   13.414104] remap_pfn_range start~end: 0x4073f000 0x40771000, pyh:0xa7b7d , nocached.
<7>[   13.731019] remap_pfn_range start~end: 0x40829000 0x4085b000, pyh:0xa7baf , nocached.
<7>[   14.013088] remap_pfn_range start~end: 0x48778000 0x48870000, pyh:0xa7be1 , nocached.
<4>[   14.062679] [wdt] set topval: 5set period: 0x1f4
<4>[   17.509281] set duty: 0x1a9
<4>[   17.509299] set phase: 0x0
<4>[   17.509308] set delay: 0x0
<4>[   17.509318] set ctrl: 0x1
<4>[   17.509328] set pulses: 0x0
<4>[   17.509349] set pwm 3, enable: 0x88, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[55199.050000] set period: 0x1f4
<4>[55199.050021] set duty: 0x0
<4>[55199.050031] set phase: 0x0
<4>[55199.050039] set delay: 0x0
<4>[55199.050050] set ctrl: 0x1
<4>[55199.050060] set pulses: 0x0
<4>[55199.050081] set pwm 3, enable: 0x88, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<7>[57557.651844] remap_pfn_range start~end: 0x4017c000 0x4019c000, pyh:0xa7cd9 , nocached.
<7>[57557.651970] [MEDIA]check_dst_chan 455: [unlegality chan]:chan 16 0x0 0 0
```

```
# cat /proc/meminfo
MemTotal:          32308 kB
MemFree:           11816 kB
Buffers:             488 kB
Cached:             9600 kB
SwapCached:            0 kB
Active:             4228 kB
Inactive:           9060 kB
Active(anon):       3212 kB
Inactive(anon):     4644 kB
Active(file):       1016 kB
Inactive(file):     4416 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:          3220 kB
Mapped:             3424 kB
Shmem:              4656 kB
Slab:               3496 kB
SReclaimable:        452 kB
SUnreclaim:         3044 kB
KernelStack:         696 kB
PageTables:          468 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:       16152 kB
Committed_AS:      51048 kB
VmallocTotal:     974848 kB
VmallocUsed:       36564 kB
VmallocChunk:     924028 kB
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
0xc30c6000-0xc30c8000    8192 fh_ioremap+0x30/0x58 [isp] ioremap
0xc30c8000-0xc30cd000   20480 fh_gmac_probe+0x100/0x370 ioremap
0xc30ce000-0xc30d0000    8192 fh_ioremap+0x30/0x58 [isp] ioremap
0xc30d0000-0xc30d5000   20480 fh_aes_probe+0xdc/0x2fc ioremap
0xc30d5000-0xc30e6000   69632 xz_dec_lzma2_create+0x64/0x8c pages=16 vmalloc
0xc30f8000-0xc30fc000   16384 0xbf0690a8 ioremap
0xc3100000-0xc3111000   69632 0xbf00e0e4 ioremap
0xc3111000-0xc318c000  503808 firmware_loading_store+0x150/0x1c4
0xc31f6000-0xc31f8000    8192 hevc_chn_mem_init+0x6ac/0xb7c [hevc] ioremap
0xc31f8000-0xc31fd000   20480 fullhan_init_vdi+0x24/0xdc [hevc] ioremap
0xc31fe000-0xc3200000    8192 hevc_chn_mem_init+0x6ac/0xb7c [hevc] ioremap
0xc3200000-0xc3301000 1052672 fh_otg_driver_probe+0x178/0x8c8 ioremap
0xc3304000-0xc3307000   12288 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3308000-0xc3310000   32768 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3310000-0xc3319000   36864 0xbf08c130 ioremap
0xc332c000-0xc332f000   12288 hevc_chn_mem_init+0x704/0xb7c [hevc] ioremap
0xc3330000-0xc333c000   49152 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3340000-0xc3361000  135168 0xbf08c1d4 ioremap
0xc3400000-0xc3501000 1052672 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3580000-0xc35ae000  188416 vpu_sys_mem_init+0x54/0x408 [vpu] ioremap
0xc35b0000-0xc35b9000   36864 hevc_chn_mem_init+0x824/0xb7c [hevc] ioremap
0xc3600000-0xc3701000 1052672 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3720000-0xc3732000   73728 hevc_chn_mem_init+0x704/0xb7c [hevc] ioremap
0xc3738000-0xc373f000   28672 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3740000-0xc3761000  135168 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3780000-0xc37d7000  356352 hevc_sys_mem_init+0x54/0x2f4 [hevc] ioremap
0xc37e0000-0xc37f2000   73728 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3800000-0xc3953000 1388544 vpu_set_chn_mem+0x114/0x688 [vpu] ioremap
0xc3960000-0xc3972000   73728 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3980000-0xc39d5000  348160 vdi_init+0xb0/0x3c0 [hevc] ioremap
0xc39e0000-0xc3a00000  131072 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3a00000-0xc3a9c000  638976 fh_ioremap+0x30/0x58 [isp] ioremap
0xc3bb0000-0xc3bb9000   36864 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3bf0000-0xc3bf9000   36864 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3c00000-0xc3e81000 2625536 media_stream_buff_malloc+0x8c/0xd0 [media_process] ioremap
0xc3e90000-0xc3e9f000   61440 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc3fc0000-0xc3fe1000  135168 vdi_allocate_dma_memory_ex+0x68/0xd8 [hevc] ioremap
0xc4000000-0xc5862000 25567232 vpu_set_chn_mem+0x114/0x688 [vpu] ioremap
0xc5900000-0xc597c000  507904 hevc_chn_mem_init+0x824/0xb7c [hevc] ioremap
0xc5980000-0xc59a1000  135168 jpeg_mem_query+0x11c/0x1b0 [jpeg] ioremap
```

```
# cat /proc/vmstat
nr_free_pages 2954
nr_inactive_anon 1161
nr_active_anon 803
nr_inactive_file 1104
nr_active_file 254
nr_unevictable 0
nr_mlock 0
nr_anon_pages 805
nr_mapped 856
nr_file_pages 2522
nr_dirty 0
nr_writeback 0
nr_slab_reclaimable 113
nr_slab_unreclaimable 761
nr_page_table_pages 117
nr_kernel_stack 87
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
nr_dirty_threshold 862
nr_dirty_background_threshold 431
pgpgin 3042
pgpgout 0
pswpin 0
pswpout 0
pgalloc_normal 909956
pgalloc_movable 0
pgfree 912912
pgactivate 580
pgdeactivate 99
pgfault 817215
pgmajfault 56
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
tar cf - / | ftpput 10.0.1.1 root.tar -
tar cf - /usr/ | ftpput 10.0.1.1 usr.tar -
tar cf - /proc/ | ftpput 10.0.1.1 proc.tar -
```

-----

```
sudo binwalk -Me --run-as=root mtd1
sudo binwalk -Me --run-as=root mtd2
sudo binwalk -Me --run-as=root mtd3
sudo binwalk -Me --run-as=root mtd4
sudo binwalk -Me --run-as=root mtd5
```
