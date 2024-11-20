# Jieuno

```
uboot-2016-15
linux-4.9-11
FW: V1.11.78-20231108
```

Motion detect, human detect, alarm In, timing snapshot

```
# cat /usr/app/product
product=PB
uboot=15
kernel=11
appfs=11178
ota_url=/fh8856v200/PB/PB.bin
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
devpts on /dev/pts type devpts (rw,relatime,mode=600,ptmxmode=000)
/dev/mtdblock2 on /usr/app type squashfs (ro,relatime)
/dev/mtdblock3 on /tmp/etc/custom type jffs2 (rw,relatime)
/dev/mtdblock4 on /tmp/etc/config type jffs2 (rw,relatime)
```

```
# busybox
BusyBox v1.26.2 (2021-09-16 10:54:41 CST) multi-call binary.
BusyBox is copyrighted by many authors between 1998-2015.
Licensed under GPLv2. See source distribution for detailed
copyright notices.

Usage: busybox [function [arguments]...]
   or: busybox --list
   or: function [arguments]...

        BusyBox is a multi-call binary that combines many common Unix
        utilities into a single executable.  Most people will create a
        link to busybox for each function they wish to use and BusyBox
        will act like whatever it was invoked as.

Currently defined functions:
        [, [[, ash, awk, bash, cat, chmod, cp, date, dd, df, dhcprelay, dmesg,
        du, dumpleases, echo, egrep, env, false, fdisk, fgrep, free, fsync,
        ftpget, ftpput, grep, gunzip, gzip, halt, hostname, hwclock, ifconfig,
        inetd, init, insmod, iostat, kill, killall, linuxrc, ln, login, ls,
        lsmod, lsusb, lzcat, lzma, mdev, mkdir, mkdosfs, mkfs.vfat, mknod,
        modprobe, mount, mpstat, mv, netstat, ping, ping6, poweroff, ps, pwd,
        reboot, rm, rmmod, route, sed, sh, sleep, sync, tail, tar, telnetd,
        test, tftp, top, touch, true, udhcpc, udhcpd, umount, unlzma, usleep,
        wc, zcat
```

```
# cat /proc/filesystems
nodev   sysfs
nodev   rootfs
nodev   ramfs
nodev   bdev
nodev   proc
nodev   tmpfs
nodev   configfs
nodev   debugfs
nodev   sockfs
nodev   pipefs
nodev   rpc_pipefs
nodev   devpts
        squashfs
        vfat
nodev   nfs
nodev   jffs2
nodev   mqueue
```

```
# cat /proc/cpuinfo
processor       : 0
model name      : ARMv6-compatible processor rev 7 (v6l)
BogoMIPS        : 2.00
Features        : half thumb fastmult vfp edsp java tls
CPU implementer : 0x41
CPU architecture: 7
CPU variant     : 0x0
CPU part        : 0xb76
CPU revision    : 7

Hardware        : FH8856V200
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
180 usb
189 usb_device
254 gpiochip

Block devices:
259 blkext
 31 mtdblock
179 mmc
```

```
# cat /proc/kmsg
<6>[    0.000000] Booting Linux on physical CPU 0x0
<5>[    0.000000] Linux version 4.9.129 (wilbur@Fossa) (gcc version 6.5.0 (arm_multilib_uclibc_20200924) ) #1 Thu Jan 13 13:46:00 CST 2022
<6>[    0.000000] CPU: ARMv6-compatible processor [410fb767] revision 7 (ARMv7), cr=00c5387d
<6>[    0.000000] CPU: VIPT aliasing data cache, VIPT aliasing instruction cache
<6>[    0.000000] Machine: FH8856V200
<6>[    0.000000] Memory policy: Data cache writeback
<7>[    0.000000] On node 0 totalpages: 9216
<7>[    0.000000] free_area_init_node: node 0, pgdat c04c8074, node_mem_map c23b1000
<7>[    0.000000]   Normal zone: 72 pages used for memmap
<7>[    0.000000]   Normal zone: 0 pages reserved
<7>[    0.000000]   Normal zone: 9216 pages, LIFO batch:1
<7>[    0.000000] pcpu-alloc: s0 r0 d32768 u32768 alloc=1*32768
<7>[    0.000000] pcpu-alloc: [0] 0
<6>[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 9144
<5>[    0.000000] Kernel command line: mem=36M console=ttyS0,115200 root=/dev/mtdblock2 rootfstype=squashfs quiet mtdparts=spi0.0:320K(uboot),2560K(kernel),4352K(appfs),576K(custom),320K(config),64K(data)
<6>[    0.000000] PID hash table entries: 256 (order: -2, 1024 bytes)
<6>[    0.000000] Dentry cache hash table entries: 8192 (order: 3, 32768 bytes)
<6>[    0.000000] Inode-cache hash table entries: 4096 (order: 2, 16384 bytes)
<6>[    0.000000] Memory: 31432K/36864K available (2986K kernel code, 154K rwdata, 784K rodata, 824K init, 148K bss, 5432K reserved, 0K cma-reserved)
<5>[    0.000000] Virtual kernel memory layout:
<5>[    0.000000]     vector  : 0xffff0000 - 0xffff1000   (   4 kB)
<5>[    0.000000]     fixmap  : 0xffc00000 - 0xfff00000   (3072 kB)
<5>[    0.000000]     vmalloc : 0xc2800000 - 0xff800000   ( 976 MB)
<5>[    0.000000]     lowmem  : 0xc0000000 - 0xc2400000   (  36 MB)
<5>[    0.000000]     modules : 0xbf000000 - 0xc0000000   (  16 MB)
<5>[    0.000000]       .text : 0xc0008000 - 0xc02f2a40   (2987 kB)
<5>[    0.000000]       .init : 0xc03d4000 - 0xc04a2000   ( 824 kB)
<5>[    0.000000]       .data : 0xc04a2000 - 0xc04c88c0   ( 155 kB)
<5>[    0.000000]        .bss : 0xc04c88c0 - 0xc04ed9e0   ( 149 kB)
<6>[    0.000000] SLUB: HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
<6>[    0.000000] NR_IRQS:16 nr_irqs:16 16
<6>[    0.000000] Switching to timer-based delay loop, resolution 1000ns
<6>[    0.000000] clocksource: timer1: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1911260446275 ns
<6>[    0.000010] sched_clock: 32 bits at 1000kHz, resolution 1000ns, wraps every 2147483647500ns
<6>[    0.000226] Console: colour dummy device 80x30
<6>[    0.000265] console [ttyS0] enabled
<6>[    0.000284] Calibrating delay loop (skipped), value calculated using timer frequency.. 695.09 BogoMIPS (lpj=3475456)
<6>[    0.060080] pid_max: default: 32768 minimum: 301
<6>[    0.060194] Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.060207] Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.060850] CPU: Testing write buffer coherency: ok
<6>[    0.061189] Setting up static identity map for 0xa0008200 - 0xa0008238
<6>[    0.063152] VFP support v0.3: implementor 41 architecture 1 part 20 variant b rev 5
<6>[    0.063305] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
<6>[    0.063322] futex hash table entries: 256 (order: -1, 3072 bytes)
<6>[    0.063772] NET: Registered protocol family 16
<6>[    0.064279] DMA: preallocated 256 KiB pool for atomic coherent allocations
<6>[    0.068669] CHIP: FH8856V200
<6>[    0.074573] fh_axi_dmac fh_axi_dmac.0: FH DMA Controller, 6 channels
<6>[    0.074992] usbcore: registered new interface driver usbfs
<6>[    0.075080] usbcore: registered new interface driver hub
<6>[    0.075151] usbcore: registered new device driver usb
<6>[    0.076800] clocksource: Switched to clocksource timer1
<6>[    0.082249] NET: Registered protocol family 2
<6>[    0.083112] TCP established hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.083141] TCP bind hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.083164] TCP: Hash tables configured (established 1024 bind 1024)
<6>[    0.083239] UDP hash table entries: 256 (order: 0, 4096 bytes)
<6>[    0.083261] UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
<6>[    0.083435] NET: Registered protocol family 1
<6>[    0.083857] RPC: Registered named UNIX socket transport module.
<6>[    0.083865] RPC: Registered udp transport module.
<6>[    0.083868] RPC: Registered tcp transport module.
<6>[    0.083872] RPC: Registered tcp NFSv4.1 backchannel transport module.
<6>[    0.658094] workingset: timestamp_bits=30 max_order=13 bucket_order=0
<6>[    0.666365] squashfs: version 4.0 (2009/01/31) Phillip Lougher
<6>[    0.667682] jffs2: version 2.2. © 2001-2006 Red Hat, Inc.
<6>[    0.670190] NET: Registered protocol family 38
<6>[    0.670223] io scheduler noop registered
<6>[    0.670458] io scheduler cfq registered (default)
<4>[    0.674646] fh_pwm_probe: clk_rate: 50000000
<6>[    0.674774] PWM driver, Number: 12, IO base addr: 0xc30b0000
<6>[    0.675007] Serial: fh serial driver
<6>[    0.675093] ttyS.0: ttyS0 at MMIO 0xf0700000 (irq = 46, base_baud = 1041666) is a ttyS
<6>[    0.675277] fh serial at 0xf0700000, irq 46
<6>[    0.675328] ttyS.1: ttyS1 at MMIO 0xf0800000 (irq = 47, base_baud = 1041666) is a ttyS
<6>[    0.675520] fh serial at 0xf0800000, irq 47
<6>[    0.675572] ttyS.2: ttyS2 at MMIO 0xf1300000 (irq = 57, base_baud = 1041666) is a ttyS
<6>[    0.675758] fh serial at 0xf1300000, irq 57
<6>[    0.676319] efuse open mode is 307
<6>[    0.676716] CLK misc driver init successfully
<4>[    0.677971] m25p80 spi0.0: found by25q64as, expected m25p80
<6>[    0.678020] m25p80 spi0.0: by25q64as (8192 Kbytes)
<5>[    0.678053] 6 cmdlinepart partitions found on MTD device spi0.0
<5>[    0.678058] Creating 6 MTD partitions on "spi0.0":
<5>[    0.678069] 0x000000000000-0x000000050000 : "uboot"
<5>[    0.679277] 0x000000050000-0x0000002d0000 : "kernel"
<5>[    0.680446] 0x0000002d0000-0x000000710000 : "appfs"
<5>[    0.681484] 0x000000710000-0x0000007a0000 : "custom"
<5>[    0.682543] 0x0000007a0000-0x0000007f0000 : "config"
<5>[    0.683637] 0x0000007f0000-0x000000800000 : "data"
<6>[    0.685385] libphy: Fixed MDIO Bus: probed
<6>[    0.685438] GMAC driver:
<6>[    0.685438]       platform registration...
<4>[    0.685543]       using random MAC address: aa:da:95:2c:d9:7b
<6>[    0.913291] ephy: training data is :1
<4>[    0.914050] fh_gmac fh_gmac.0 eth0: mixed HW and IP checksum settings.
<6>[    0.914263]       eth0 - (dev. name: fh_gmac - id: 0, IRQ #60
<6>[    0.914263]               IO base addr: 0xc30d8000)
<6>[    0.924373] ephy: training data is :1
<6>[    1.118612] libphy: gmac_rmii: probed
<6>[    1.118620] found fh internel phy...
<3>[    1.120629] AFE driver [Raw] : [100M] : [10M] = [101f] : [10] : [1f]
<6>[    1.121350] eth0: PHY ID 00441400 at 0 IRQ -1 (0:00) active
<6>[    1.176910] fh_usb fh_usb.0: DWC OTG Controller
<6>[    1.176965] fh_usb fh_usb.0: new USB bus registered, assigned bus number 1
<6>[    1.177010] fh_usb fh_usb.0: irq 55, io mem 0x00000000
<6>[    1.177268] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
<6>[    1.177281] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.177290] usb usb1: Product: DWC OTG Controller
<6>[    1.177298] usb usb1: Manufacturer: Linux 4.9.129 dwc2_hsotg
<6>[    1.177307] usb usb1: SerialNumber: fh_usb.0
<6>[    1.177887] hub 1-0:1.0: USB hub found
<6>[    1.177941] hub 1-0:1.0: 1 port detected
<6>[    1.178433] usbcore: registered new interface driver cdc_wdm
<6>[    1.178439] i2c /dev entries driver
<6>[    1.178515] I2C driver:
<6>[    1.178515]       platform registration...
<6>[    1.178592]       tx fifo depth: 16, rx fifo depth: 16
<6>[    1.178844]       I2C - (dev. name: fh_i2c id: 0, IRQ #27
<6>[    1.178844]               IO base addr: 0xc30e0000)
<6>[    1.178874] I2C driver:
<6>[    1.178874]       platform registration...
<6>[    1.178943]       tx fifo depth: 16, rx fifo depth: 16
<6>[    1.179195]       I2C - (dev. name: fh_i2c id: 1, IRQ #28
<6>[    1.179195]               IO base addr: 0xc30e8000)
<6>[    1.179225] I2C driver:
<6>[    1.179225]       platform registration...
<6>[    1.179294]       tx fifo depth: 16, rx fifo depth: 16
<6>[    1.179564]       I2C - (dev. name: fh_i2c id: 2, IRQ #62
<6>[    1.179564]               IO base addr: 0xc30f0000)
<6>[    1.181608] card0 disconnected!
<6>[    1.183257] aes driver registered
<6>[    1.184247] NET: Registered protocol family 10
<6>[    1.185687] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
<6>[    1.186570] NET: Registered protocol family 17
<6>[    1.186596] lib80211: common routines for IEEE802.11 drivers
<7>[    1.186602] lib80211_crypt: registered algorithm 'NULL'
<7>[    1.186606] lib80211_crypt: registered algorithm 'WEP'
<7>[    1.186611] lib80211_crypt: registered algorithm 'CCMP'
<7>[    1.186615] lib80211_crypt: registered algorithm 'TKIP'
<5>[    1.186641] Key type dns_resolver registered
<6>[    1.192228] Freeing unused kernel memory: 824K
<4>[    1.192236] This architecture does not have kernel memory protection.
<5>[    1.652437] random: S03network: uninitialized urandom read (4 bytes read)
<4>[    1.834919] vmm: loading out-of-tree module taints kernel.
<6>[    1.835786] Video Memory Manager
<4>[    1.835799] [VMM] version: V1.1.0(g31e4df5),build: 2021-07-16
<4>[    1.835803]
<7>[    1.835824] media_mem_parse_cmdline: s=anonymous,0,0xA2400000,90M.
<7>[    1.835833] media_mem_parse_cmdline: i=4.
<7>[    1.835846] vmm:anonymous,a2400000,5a00000.
<4>[    1.861857] [XBUS] version: (g749c96e-dirty),build: 2020-08-08
<4>[    1.986936] Xbus: fwver=7a9372ed,phyaddr=bfffe000,len=8192.
<4>[    2.042137] media_process: module license 'Proprietary' taints kernel.
<4>[    2.042144] Disabling lock debugging due to kernel taint
<6>[    3.440518] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
<6>[    3.441078] fh_gmac fh_gmac.0 eth0: Link is Up - 100Mbps/Full - flow control rx/tx
<6>[    3.441102] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
<5>[    4.186813] random: fast init done
<4>[    6.464361] UART2:
<4>[    6.464386]
<4>[    6.485632] set period: 0x1f4
<4>[    6.485640] set duty: 0x0
<4>[    6.485643] set phase: 0x0
<4>[    6.485646] set delay: 0x0
<4>[    6.485651] set ctrl: 0x1
<4>[    6.485655] set pulses: 0x0
<4>[    6.485670] set pwm 3, enable: 0xc, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<3>[    6.700391] i2c_fh_handle_tx_abort: slave address not acknowledged (7bit mode)
<3>[    6.703748] i2c_fh_handle_tx_abort: slave address not acknowledged (7bit mode)
<7>[    6.759075] remap_pfn_range start~end: 0xb6a78000 0xb6a9e000, pyh:0xa2400 , nocached.
<7>[    6.761069] remap_pfn_range start~end: 0xb5242000 0xb6a76000, pyh:0xa2426 , nocached.
<7>[    6.762090] remap_pfn_range start~end: 0xb5046000 0xb5241000, pyh:0xa3c5a , nocached.
<7>[    6.762385] remap_pfn_range start~end: 0xb4fed000 0xb5044000, pyh:0xa3e55 , nocached.
<7>[    6.762793] remap_pfn_range start~end: 0xb4c6c000 0xb4fed000, pyh:0xa3eac , nocached.
<7>[    6.768710] remap_pfn_range start~end: 0xb2fec000 0xb4c6c000, pyh:0xa4230 , nocached.
<3>[    6.768908] i2c_fh_handle_tx_abort: slave address not acknowledged (7bit mode)
<3>[    6.786927] i2c_fh_handle_tx_abort: slave address not acknowledged (7bit mode)
<7>[    6.877141] remap_pfn_range start~end: 0xb225c000 0xb2fde000, pyh:0xa5eb0 , nocached.
<7>[    6.877502] remap_pfn_range start~end: 0xb217e000 0xb2259000, pyh:0xa6c32 , nocached.
<4>[    6.982542] set period: 0x1f4
<4>[    6.982550] set duty: 0x0
<4>[    6.982553] set phase: 0x0
<4>[    6.982557] set delay: 0x0
<4>[    6.982562] set ctrl: 0x1
<4>[    6.982566] set pulses: 0x0
<4>[    6.982582] set pwm 2, enable: 0xc, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<7>[    8.225515] remap_pfn_range start~end: 0xb0c69000 0xb0c76000, pyh:0xa6d0d , nocached.
<7>[    8.230758] remap_pfn_range start~end: 0xb0c5a000 0xb0c67000, pyh:0xa6d1a , nocached.
<7>[    8.234304] remap_pfn_range start~end: 0xb0b27000 0xb0b59000, pyh:0xa6d27 , nocached.
<7>[    8.378038] remap_pfn_range start~end: 0xb0af5000 0xb0b27000, pyh:0xa6d59 , nocached.
<7>[    8.521803] remap_pfn_range start~end: 0xb0a63000 0xb0af3000, pyh:0xa6d8b , nocached.
<6>[    8.552808] fh_wdt: [wdt] set topval: 5
<6>[    8.552849] fh_wdt: [wdt] set topval: 9
<6>[    8.622179] sh (339): drop_caches: 3
<4>[   12.170196] set period: 0x1f4
<4>[   12.170204] set duty: 0x1a9
<4>[   12.170207] set phase: 0x0
<4>[   12.170211] set delay: 0x0
<4>[   12.170216] set ctrl: 0x1
<4>[   12.170220] set pulses: 0x0
<4>[   12.170237] set pwm 2, enable: 0xc, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<5>[   21.842582] random: crng init done
<5>[   21.842596] random: 7 urandom warning(s) missed due to ratelimiting
<7>[54197.600106] remap_pfn_range start~end: 0xafc3f000 0xafc60000, pyh:0xa6e1b , nocached.
```

```
# cat /proc/meminfo
MemTotal:          32256 kB
MemFree:           13128 kB
MemAvailable:      16516 kB
Buffers:             380 kB
Cached:             9320 kB
SwapCached:            0 kB
Active:             4252 kB
Inactive:           8288 kB
Active(anon):       2852 kB
Inactive(anon):     5228 kB
Active(file):       1400 kB
Inactive(file):     3060 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:          2856 kB
Mapped:             5192 kB
Shmem:              5240 kB
Slab:               3212 kB
SReclaimable:        668 kB
SUnreclaim:         2544 kB
KernelStack:         680 kB
PageTables:          364 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:       16128 kB
Committed_AS:      51156 kB
VmallocTotal:     999424 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
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
devpts /dev/pts devpts rw,relatime,mode=600,ptmxmode=000 0 0
/dev/mtdblock2 /usr/app squashfs ro,relatime 0 0
/dev/mtdblock3 /tmp/etc/custom jffs2 rw,relatime 0 0
/dev/mtdblock4 /tmp/etc/config jffs2 rw,relatime 0 0
```

```
# cat /proc/mtd
dev:    size   erasesize  name
mtd0: 00050000 00010000 "uboot"
mtd1: 00280000 00010000 "kernel"
mtd2: 00440000 00010000 "appfs"
mtd3: 00090000 00010000 "custom"
mtd4: 00050000 00010000 "config"
mtd5: 00010000 00010000 "data"
```

```
# cat /proc/partitions
major minor  #blocks  name

  31        0        320 mtdblock0
  31        1       2560 mtdblock1
  31        2       4352 mtdblock2
  31        3        576 mtdblock3
  31        4        320 mtdblock4
  31        5         64 mtdblock5
```

```
# cat /proc/version
Linux version 4.9.129 (wilbur@Fossa) (gcc version 6.5.0 (arm_multilib_uclibc_20200924) ) #1 Thu Jan 13 13:46:00 CST 2022
```

```
# cat /proc/vmallocinfo
0xbf000000-0xbf004000   16384 load_module+0x650/0x1aa0 pages=3 vmalloc
0xbf007000-0xbf00c000   20480 load_module+0x650/0x1aa0 pages=4 vmalloc
0xbf010000-0xbf035000  151552 load_module+0x650/0x1aa0 pages=36 vmalloc
0xbf03e000-0xbf053000   86016 load_module+0x650/0x1aa0 pages=20 vmalloc
0xbf058000-0xbf077000  126976 load_module+0x650/0x1aa0 pages=30 vmalloc
0xbf07e000-0xbf0a7000  167936 load_module+0x650/0x1aa0 pages=40 vmalloc
0xbf0ae000-0xbf0c2000   81920 load_module+0x650/0x1aa0 pages=19 vmalloc
0xbf0c6000-0xbf0dc000   90112 load_module+0x650/0x1aa0 pages=21 vmalloc
0xc2804000-0xc2845000  266240 atomic_pool_init+0x0/0x134 user
0xc2845000-0xc2847000    8192 dma_alloc_attrs.constprop.5+0x64/0x70 user
0xc2848000-0xc284d000   20480 fh_axi_dma_adapt_probe+0x68/0x314 phys=e0300000 ioremap
0xc28e0000-0xc2901000  135168 _create_jpg_chan+0xa0/0x2c4 [jpeg] phys=a6e1b000 ioremap
0xc3051000-0xc3094000  274432 jffs2_zlib_init+0x14/0x74 pages=66 vmalloc
0xc3094000-0xc30a0000   49152 jffs2_zlib_init+0x2c/0x74 pages=11 vmalloc
0xc30a0000-0xc30a5000   20480 fh_gpio_probe+0x88/0x264 phys=f0300000 ioremap
0xc30a5000-0xc30a7000    8192 dma_alloc_attrs.constprop.5+0x64/0x70 user
0xc30a8000-0xc30ad000   20480 fh_gpio_probe+0x88/0x264 phys=f4000000 ioremap
0xc30ad000-0xc30af000    8192 dwc2_hcd_init+0x414/0x600 user
0xc30b0000-0xc30b5000   20480 fh_pwm_probe+0x88/0x30c phys=f0400000 ioremap
0xc30b5000-0xc30b7000    8192 fh_mci_probe+0x2a8/0x518 user
0xc30b8000-0xc30bd000   20480 fh_sadc_probe+0x104/0x284 phys=f1200000 ioremap
0xc30c0000-0xc30c5000   20480 fh_efuse_probe+0x7c/0x164 phys=f1600000 ioremap
0xc30c5000-0xc30c7000    8192 mipi_driver_init+0x34/0xc8 [isp] phys=f1100000 ioremap
0xc30c8000-0xc30cd000   20480 fh_spi_probe+0x120/0x4cc phys=f0500000 ioremap
0xc30cd000-0xc30cf000    8192 mipi_driver_init+0x60/0xc8 [isp] phys=f1000000 ioremap
0xc30d0000-0xc30d5000   20480 fh_spi_probe+0x120/0x4cc phys=f0600000 ioremap
0xc30d5000-0xc30d7000    8192 vpu_driver_init+0x68/0x160 [vpu] phys=e7400000 ioremap
0xc30d8000-0xc30dd000   20480 fh_gmac_probe+0xc8/0x49c phys=e0600000 ioremap
0xc30dd000-0xc30df000    8192 vpu_driver_init+0x88/0x160 [vpu] phys=e8700000 ioremap
0xc30e0000-0xc30e5000   20480 fh_i2c_probe+0x17c/0x338 phys=f0200000 ioremap
0xc30e5000-0xc30e7000    8192 hhe_dev_init+0x74/0x21c [enc] phys=e7080000 ioremap
0xc30e8000-0xc30ed000   20480 fh_i2c_probe+0x17c/0x338 phys=f0b00000 ioremap
0xc30ed000-0xc30ef000    8192 hhe_dev_init+0xb4/0x21c [enc] phys=e7046000 ioremap
0xc30f0000-0xc30f5000   20480 fh_i2c_probe+0x17c/0x338 phys=f0100000 ioremap
0xc30f5000-0xc30f7000    8192 hhe_dev_init+0xd4/0x21c [enc] phys=e7080000 ioremap
0xc30f8000-0xc30fd000   20480 devm_ioremap_nocache+0x3c/0x70 phys=f0d00000 ioremap
0xc30fd000-0xc30ff000    8192 hhe_dev_init+0xf4/0x21c [enc] phys=e7000000 ioremap
0xc3100000-0xc3201000 1052672 devm_ioremap_nocache+0x3c/0x70 phys=e0700000 ioremap
0xc3201000-0xc3203000    8192 hhe_dev_init+0x134/0x21c [enc] phys=e7000000 ioremap
0xc3204000-0xc3209000   20480 fh_mci_probe+0x1b4/0x518 phys=e2000000 ioremap
0xc3209000-0xc320b000    8192 jpeg_driver_init+0x2c/0x9c [jpeg] phys=e8300000 ioremap
0xc320c000-0xc3211000   20480 fh_aes_probe+0x78/0x264 phys=e8200000 ioremap
0xc3215000-0xc3226000   69632 xz_dec_lzma2_create+0x3c/0x7c pages=16 vmalloc
0xc3234000-0xc3237000   12288 xbus_get_sys_info+0x9c/0x1f8 [xbus_rpc] phys=bfffe000 ioremap
0xc3237000-0xc3239000    8192 bgm_driver_init+0x50/0x128 [bgm] phys=e8606000 ioremap
0xc3239000-0xc323b000    8192 hhe_sys_init+0xf8/0x3a0 [enc] phys=a3fac000 ioremap
0xc323b000-0xc323d000    8192 isp_start+0xb0/0x1a4 [isp] pages=1 vmalloc
0xc323d000-0xc3240000   12288 isp_start+0xd0/0x1a4 [isp] pages=2 vmalloc
0xc32e0000-0xc32f1000   69632 vpu_driver_init+0x48/0x160 [vpu] phys=ec000000 ioremap
0xc32fa000-0xc32fd000   12288 fh_ioremap+0x28/0x7c [isp] phys=a4239000 ioremap
0xc32fd000-0xc32ff000    8192 fh_ioremap+0x28/0x7c [isp] phys=a4239000 ioremap
0xc3300000-0xc3401000 1052672 isp_driver_init+0x10c/0x334 [isp] phys=e8400000 ioremap
0xc3434000-0xc3437000   12288 fh_ioremap+0x28/0x7c [isp] phys=a4239000 ioremap
0xc3438000-0xc3441000   36864 hhe_dev_init+0x48/0x21c [enc] phys=e70c0000 ioremap
0xc3474000-0xc3477000   12288 fh_ioremap+0x28/0x7c [isp] phys=a4240000 ioremap
0xc3478000-0xc347f000   28672 hhe_chn_mem_init+0x524/0xaa0 [enc] phys=a6d02000 ioremap
0xc3480000-0xc34c1000  266240 hhe_dev_init+0x94/0x21c [enc] phys=10000000 ioremap
0xc34c1000-0xc34c3000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d07000 ioremap
0xc34c3000-0xc34c5000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d08000 ioremap
0xc34c5000-0xc34c7000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d08000 ioremap
0xc34d1000-0xc34d3000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d09000 ioremap
0xc34d3000-0xc34d5000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d09000 ioremap
0xc34d5000-0xc34d7000    8192 hhe_chn_mem_init+0x844/0xaa0 [enc] phys=a6d0a000 ioremap
0xc34d8000-0xc34dc000   16384 hhe_chn_mem_init+0x8f4/0xaa0 [enc] phys=a6d0a000 ioremap
0xc34f0000-0xc34f9000   36864 fh_ioremap+0x28/0x7c [isp] phys=a4239000 ioremap
0xc3500000-0xc3601000 1052672 isp_driver_init+0x128/0x334 [isp] phys=e8500000 ioremap
0xc3610000-0xc361b000   45056 fh_ioremap+0x28/0x7c [isp] phys=a4230000 ioremap
0xc3620000-0xc362a000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bb9000 ioremap
0xc3630000-0xc363a000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bc1000 ioremap
0xc3640000-0xc3667000  159744 vpu_create_grp+0x88/0x58c [vpu] phys=a2400000 ioremap
0xc3670000-0xc367a000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bc9000 ioremap
0xc3680000-0xc36d8000  360448 vpu_create_channel+0x124/0x750 [vpu] phys=a3e55000 ioremap
0xc36e0000-0xc36ea000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bd1000 ioremap
0xc36f0000-0xc36fa000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bd9000 ioremap
0xc3790000-0xc379a000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6be1000 ioremap
0xc37a0000-0xc37aa000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6be9000 ioremap
0xc37b0000-0xc37ba000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6bf1000 ioremap
0xc37c0000-0xc37ca000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6bf9000 ioremap
0xc37d0000-0xc37da000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6c01000 ioremap
0xc37e0000-0xc37ea000   40960 hhe_chn_mem_init+0x844/0xaa0 [enc] phys=a6c09000 ioremap
0xc3800000-0xc39fc000 2080768 vpu_create_channel+0x124/0x750 [vpu] phys=a3c5a000 ioremap
0xc3a00000-0xc3a8f000  585728 fh_ioremap+0x28/0x7c [isp] phys=a4241000 ioremap
0xc3ac0000-0xc3ae2000  139264 hhe_chn_mem_init+0x8f4/0xaa0 [enc] phys=a6c11000 ioremap
0xc3b00000-0xc3b5a000  368640 hhe_chn_mem_init+0x524/0xaa0 [enc] phys=a6b61000 ioremap
0xc3c00000-0xc3e82000 2629632 media_stream_buff_malloc+0x140/0x200 [media_process] phys=a3fac000 ioremap
0xc4000000-0xc5835000 25382912 vpu_create_channel+0x124/0x750 [vpu] phys=a2426000 ioremap
0xc606b000-0xc606f000   16384 n_tty_open+0x10/0x9c pages=3 vmalloc
0xc60ad000-0xc60b1000   16384 n_tty_open+0x10/0x9c pages=3 vmalloc
0xc60b1000-0xc60b5000   16384 n_tty_open+0x10/0x9c pages=3 vmalloc
0xfe000000-0xfe004000   16384 iotable_init+0x0/0xbc phys=e0200000 ioremap
0xfe010000-0xfe014000   16384 iotable_init+0x0/0xbc phys=f0c00000 ioremap
0xfe020000-0xfe024000   16384 iotable_init+0x0/0xbc phys=f0700000 ioremap
0xfe090000-0xfe094000   16384 iotable_init+0x0/0xbc phys=f0000000 ioremap
0xfe0a0000-0xfe0a4000   16384 iotable_init+0x0/0xbc phys=f0800000 ioremap
0xfe0b0000-0xfe0b4000   16384 iotable_init+0x0/0xbc phys=f1300000 ioremap
0xfe0d0000-0xfe0d4000   16384 iotable_init+0x0/0xbc phys=10000000 ioremap
0xfe0e0000-0xfe0e4000   16384 iotable_init+0x0/0xbc phys=ed000000 ioremap
```

```
# cat /proc/vmstat
nr_free_pages 3270
nr_zone_inactive_anon 1307
nr_zone_active_anon 713
nr_zone_inactive_file 765
nr_zone_active_file 350
nr_zone_unevictable 0
nr_zone_write_pending 0
nr_mlock 0
nr_slab_reclaimable 167
nr_slab_unreclaimable 646
nr_page_table_pages 91
nr_kernel_stack 688
nr_overhead 0
nr_bounce 0
nr_free_cma 0
nr_inactive_anon 1307
nr_active_anon 713
nr_inactive_file 765
nr_active_file 350
nr_unevictable 0
nr_isolated_anon 0
nr_isolated_file 0
nr_pages_scanned 0
workingset_refault 0
workingset_activate 0
workingset_nodereclaim 0
nr_anon_pages 714
nr_mapped 1298
nr_file_pages 2425
nr_dirty 0
nr_writeback 0
nr_writeback_temp 0
nr_shmem 1310
nr_shmem_hugepages 0
nr_shmem_pmdmapped 0
nr_anon_transparent_hugepages 0
nr_unstable 0
nr_vmscan_write 0
nr_vmscan_immediate_reclaim 0
nr_dirtied 0
nr_written 0
nr_dirty_threshold 838
nr_dirty_background_threshold 418
```

```
tar cf - / | ftpput 10.0.1.1 root.tar -
tar cf - /usr/ | ftpput 10.0.1.1 usr.tar -
tar cf - /proc/ | ftpput 10.0.1.1 proc.tar -
```

---

```
sudo binwalk -Me --run-as=root mtd1
sudo binwalk -Me --run-as=root mtd2
sudo binwalk -Me --run-as=root mtd3
sudo binwalk -Me --run-as=root mtd4
sudo binwalk -Me --run-as=root mtd5
```
