# Jieuno / Vatilon PB4

https://www.vatilon.com/productinfo/1634883.html

https://www.aliexpress.com/item/1005006050297919.html 4k + POE


Software for update:
https://www.vatilon.com/xflrjxz > Batch tools

Firmware:
https://www.vatilon.com/ipcrjxz

```
Device Type: PB4
Uboot Version: uboot-2016-15
Kernel Version: linux-4.9-11
Software Version: V1.13.23-20240524
```

```
telnet 10.0.0.33 2360
root:ipc@hs66
```

```
# tftp -l /dev/mtd0 -r mtd0 -p 10.0.0.27
# tftp -l /dev/mtd1 -r mtd1 -p 10.0.0.27
# tftp -l /dev/mtd2 -r mtd2 -p 10.0.0.27
# tftp -l /dev/mtd3 -r mtd3 -p 10.0.0.27
# tftp -l /dev/mtd4 -r mtd4 -p 10.0.0.27
# tftp -l /dev/mtd5 -r mtd5 -p 10.0.0.27
```

On PC:

```
sudo binwalk -Me --run-as=root mtd1
sudo binwalk -Me --run-as=root mtd2
sudo binwalk -Me --run-as=root mtd3
sudo binwalk -Me --run-as=root mtd4
sudo binwalk -Me --run-as=root mtd5
```

```
# cat /usr/app/product
product=PB
uboot=15
kernel=11
appfs=11323
ota_url=/fh8856v200/PB/PB.bin
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
        exfat
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
<6>[    0.000263] console [ttyS0] enabled
<6>[    0.000282] Calibrating delay loop (skipped), value calculated using timer frequency.. 695.09 BogoMIPS (lpj=3475456)
<6>[    0.060080] pid_max: default: 32768 minimum: 301
<6>[    0.060196] Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.060209] Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.060856] CPU: Testing write buffer coherency: ok
<6>[    0.061193] Setting up static identity map for 0xa0008200 - 0xa0008238
<6>[    0.063152] VFP support v0.3: implementor 41 architecture 1 part 20 variant b rev 5
<6>[    0.063304] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
<6>[    0.063321] futex hash table entries: 256 (order: -1, 3072 bytes)
<6>[    0.063773] NET: Registered protocol family 16
<6>[    0.064284] DMA: preallocated 256 KiB pool for atomic coherent allocations
<6>[    0.068670] CHIP: FH8856V200
<6>[    0.074560] fh_axi_dmac fh_axi_dmac.0: FH DMA Controller, 6 channels
<6>[    0.074979] usbcore: registered new interface driver usbfs
<6>[    0.075068] usbcore: registered new interface driver hub
<6>[    0.075140] usbcore: registered new device driver usb
<6>[    0.076794] clocksource: Switched to clocksource timer1
<6>[    0.082234] NET: Registered protocol family 2
<6>[    0.083099] TCP established hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.083129] TCP bind hash table entries: 1024 (order: 0, 4096 bytes)
<6>[    0.083151] TCP: Hash tables configured (established 1024 bind 1024)
<6>[    0.083226] UDP hash table entries: 256 (order: 0, 4096 bytes)
<6>[    0.083248] UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
<6>[    0.083418] NET: Registered protocol family 1
<6>[    0.083846] RPC: Registered named UNIX socket transport module.
<6>[    0.083853] RPC: Registered udp transport module.
<6>[    0.083857] RPC: Registered tcp transport module.
<6>[    0.083861] RPC: Registered tcp NFSv4.1 backchannel transport module.
<6>[    0.658114] workingset: timestamp_bits=30 max_order=13 bucket_order=0
<6>[    0.666386] squashfs: version 4.0 (2009/01/31) Phillip Lougher
<6>[    0.667697] jffs2: version 2.2. © 2001-2006 Red Hat, Inc.
<6>[    0.670205] NET: Registered protocol family 38
<6>[    0.670236] io scheduler noop registered
<6>[    0.670473] io scheduler cfq registered (default)
<4>[    0.674664] fh_pwm_probe: clk_rate: 50000000
<6>[    0.674792] PWM driver, Number: 12, IO base addr: 0xc30b0000
<6>[    0.675022] Serial: fh serial driver
<6>[    0.675109] ttyS.0: ttyS0 at MMIO 0xf0700000 (irq = 46, base_baud = 1041666) is a ttyS
<6>[    0.675295] fh serial at 0xf0700000, irq 46
<6>[    0.675348] ttyS.1: ttyS1 at MMIO 0xf0800000 (irq = 47, base_baud = 1041666) is a ttyS
<6>[    0.675540] fh serial at 0xf0800000, irq 47
<6>[    0.675593] ttyS.2: ttyS2 at MMIO 0xf1300000 (irq = 57, base_baud = 1041666) is a ttyS
<6>[    0.675781] fh serial at 0xf1300000, irq 57
<6>[    0.676349] efuse open mode is 307
<6>[    0.676746] CLK misc driver init successfully
<4>[    0.677996] m25p80 spi0.0: found by25q64as, expected m25p80
<6>[    0.678045] m25p80 spi0.0: by25q64as (8192 Kbytes)
<5>[    0.678076] 6 cmdlinepart partitions found on MTD device spi0.0
<5>[    0.678081] Creating 6 MTD partitions on "spi0.0":
<5>[    0.678093] 0x000000000000-0x000000050000 : "uboot"
<5>[    0.679309] 0x000000050000-0x0000002d0000 : "kernel"
<5>[    0.680489] 0x0000002d0000-0x000000710000 : "appfs"
<5>[    0.681524] 0x000000710000-0x0000007a0000 : "custom"
<5>[    0.682585] 0x0000007a0000-0x0000007f0000 : "config"
<5>[    0.683673] 0x0000007f0000-0x000000800000 : "data"
<6>[    0.685429] libphy: Fixed MDIO Bus: probed
<6>[    0.685480] GMAC driver:
<6>[    0.685480]       platform registration...
<4>[    0.685583]       using random MAC address: ce:01:3a:1f:c8:b0
<6>[    0.913283] ephy: training data is :2
<4>[    0.914043] fh_gmac fh_gmac.0 eth0: mixed HW and IP checksum settings.
<6>[    0.914256]       eth0 - (dev. name: fh_gmac - id: 0, IRQ #60
<6>[    0.914256]               IO base addr: 0xc30d8000)
<6>[    0.924369] ephy: training data is :2
<6>[    1.119765] libphy: gmac_rmii: probed
<6>[    1.119774] found fh internel phy...
<3>[    1.121784] AFE driver [Raw] : [100M] : [10M] = [101f] : [10] : [1f]
<6>[    1.122504] eth0: PHY ID 00441400 at 0 IRQ -1 (0:00) active
<6>[    1.176903] fh_usb fh_usb.0: DWC OTG Controller
<6>[    1.176958] fh_usb fh_usb.0: new USB bus registered, assigned bus number 1
<6>[    1.177003] fh_usb fh_usb.0: irq 55, io mem 0x00000000
<6>[    1.177260] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
<6>[    1.177273] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.177283] usb usb1: Product: DWC OTG Controller
<6>[    1.177292] usb usb1: Manufacturer: Linux 4.9.129 dwc2_hsotg
<6>[    1.177300] usb usb1: SerialNumber: fh_usb.0
<6>[    1.177880] hub 1-0:1.0: USB hub found
<6>[    1.177932] hub 1-0:1.0: 1 port detected
<6>[    1.178426] usbcore: registered new interface driver cdc_wdm
<6>[    1.178432] i2c /dev entries driver
<6>[    1.178509] I2C driver:
<6>[    1.178509]       platform registration...
<6>[    1.178586]       tx fifo depth: 16, rx fifo depth: 16
<6>[    1.178838]       I2C - (dev. name: fh_i2c id: 0, IRQ #27
<6>[    1.178838]               IO base addr: 0xc30e0000)
<6>[    1.178868] I2C driver:
<6>[    1.178868]       platform registration...
<6>[    1.178936]       tx fifo depth: 16, rx fifo depth: 16
<6>[    1.179187]       I2C - (dev. name: fh_i2c id: 1, IRQ #28
<6>[    1.179187]               IO base addr: 0xc30e8000)
<6>[    1.179218] I2C driver:
<6>[    1.179218]       platform registration...
<6>[    1.179286]       tx fifo depth: 16, rx fifo depth: 16
<6>[    1.179557]       I2C - (dev. name: fh_i2c id: 2, IRQ #62
<6>[    1.179557]               IO base addr: 0xc30f0000)
<6>[    1.181603] card0 disconnected!
<6>[    1.183260] aes driver registered
<6>[    1.184250] NET: Registered protocol family 10
<6>[    1.185698] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
<6>[    1.186577] NET: Registered protocol family 17
<6>[    1.186601] lib80211: common routines for IEEE802.11 drivers
<7>[    1.186607] lib80211_crypt: registered algorithm 'NULL'
<7>[    1.186612] lib80211_crypt: registered algorithm 'WEP'
<7>[    1.186616] lib80211_crypt: registered algorithm 'CCMP'
<7>[    1.186620] lib80211_crypt: registered algorithm 'TKIP'
<5>[    1.186650] Key type dns_resolver registered
<6>[    1.192234] Freeing unused kernel memory: 824K
<4>[    1.192242] This architecture does not have kernel memory protection.
<5>[    1.652860] random: S03network: uninitialized urandom read (4 bytes read)
<4>[    1.848043] vmm: loading out-of-tree module taints kernel.
<6>[    1.848913] Video Memory Manager
<4>[    1.848925] [VMM] version: V1.1.0(g31e4df5),build: 2021-07-16
<4>[    1.848930]
<7>[    1.848951] media_mem_parse_cmdline: s=anonymous,0,0xA2400000,90M.
<7>[    1.848960] media_mem_parse_cmdline: i=4.
<7>[    1.848972] vmm:anonymous,a2400000,5a00000.
<4>[    1.874557] [XBUS] version: (g749c96e-dirty),build: 2020-08-08
<4>[    1.999462] Xbus: fwver=7a9372ed,phyaddr=bfffe000,len=8192.
<4>[    2.054230] media_process: module license 'Proprietary' taints kernel.
<4>[    2.054238] Disabling lock debugging due to kernel taint
<6>[    2.420967] exFAT: Version 1.2.9
<6>[    3.478934] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
<5>[    4.216807] random: fast init done
<6>[    4.487345] fh_gmac fh_gmac.0 eth0: Link is Up - 100Mbps/Full - flow control off
<6>[    4.487373] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
<4>[    6.438276] UART2:
<4>[    6.438299]
<4>[    6.461311] set period: 0x1f4
<4>[    6.461318] set duty: 0x0
<4>[    6.461321] set phase: 0x0
<4>[    6.461324] set delay: 0x0
<4>[    6.461329] set ctrl: 0x1
<4>[    6.461333] set pulses: 0x0
<4>[    6.461349] set pwm 3, enable: 0xc, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<3>[    6.674030] i2c_fh_handle_tx_abort: slave address not acknowledged (7bit mode)
<3>[    6.677227] i2c_fh_handle_tx_abort: slave address not acknowledged (7bit mode)
<7>[    6.747292] remap_pfn_range start~end: 0xb6a1c000 0xb6a42000, pyh:0xa2400 , nocached.
<7>[    6.749269] remap_pfn_range start~end: 0xb51e6000 0xb6a1a000, pyh:0xa2426 , nocached.
<7>[    6.750280] remap_pfn_range start~end: 0xb4fea000 0xb51e5000, pyh:0xa3c5a , nocached.
<7>[    6.750583] remap_pfn_range start~end: 0xb4f91000 0xb4fe8000, pyh:0xa3e55 , nocached.
<7>[    6.750991] remap_pfn_range start~end: 0xb4c10000 0xb4f91000, pyh:0xa3eac , nocached.
<7>[    6.753896] remap_pfn_range start~end: 0xb2f90000 0xb4c10000, pyh:0xa4230 , nocached.
<3>[    6.754092] i2c_fh_handle_tx_abort: slave address not acknowledged (7bit mode)
<3>[    6.760957] i2c_fh_handle_tx_abort: slave address not acknowledged (7bit mode)
<7>[    6.819673] remap_pfn_range start~end: 0xb2200000 0xb2f82000, pyh:0xa5eb0 , nocached.
<7>[    6.819949] remap_pfn_range start~end: 0xb2122000 0xb21fd000, pyh:0xa6c32 , nocached.
<4>[    6.922966] set period: 0x1f4
<4>[    6.922973] set duty: 0x0
<4>[    6.922976] set phase: 0x0
<4>[    6.922979] set delay: 0x0
<4>[    6.922984] set ctrl: 0x1
<4>[    6.922988] set pulses: 0x0
<4>[    6.923004] set pwm 2, enable: 0xc, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<7>[    7.885612] remap_pfn_range start~end: 0xb0c0d000 0xb0c1a000, pyh:0xa6d0d , nocached.
<7>[    7.886320] remap_pfn_range start~end: 0xb0bfe000 0xb0c0b000, pyh:0xa6d1a , nocached.
<7>[    7.947719] remap_pfn_range start~end: 0xb0bef000 0xb0bfc000, pyh:0xa6d27 , nocached.
<7>[    7.948398] remap_pfn_range start~end: 0xb0be0000 0xb0bed000, pyh:0xa6d34 , nocached.
<7>[    7.954523] remap_pfn_range start~end: 0xb09ad000 0xb09df000, pyh:0xa6d41 , nocached.
<7>[    8.190512] remap_pfn_range start~end: 0xb097b000 0xb09ad000, pyh:0xa6d73 , nocached.
<7>[    8.347614] remap_pfn_range start~end: 0xb08e9000 0xb0979000, pyh:0xa6da5 , nocached.
<6>[    8.718550] fh_wdt: [wdt] set topval: 5
<6>[    8.718588] fh_wdt: [wdt] set topval: 9
<6>[    8.789158] sh (332): drop_caches: 3
<4>[   12.086303] set period: 0x1f4
<4>[   12.086314] set duty: 0x1a9
<4>[   12.086317] set phase: 0x0
<4>[   12.086321] set delay: 0x0
<4>[   12.086326] set ctrl: 0x1
<4>[   12.086330] set pulses: 0x0
<4>[   12.086347] set pwm 2, enable: 0xc, duty cycle: 8500 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<5>[   19.645114] random: crng init done
<5>[   19.645129] random: 7 urandom warning(s) missed due to ratelimiting
<7>[   21.520729] remap_pfn_range start~end: 0xaef45000 0xaef66000, pyh:0xa6e35 , nocached.
<4>[  186.204163] set period: 0x1f4
<4>[  186.204171] set duty: 0x78
<4>[  186.204174] set phase: 0x0
<4>[  186.204177] set delay: 0x0
<4>[  186.204182] set ctrl: 0x1
<4>[  186.204186] set pulses: 0x0
<4>[  186.204204] set pwm 2, enable: 0xc, duty cycle: 2400 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[  187.305938] set period: 0x1f4
<4>[  187.305946] set duty: 0x1e
<4>[  187.305949] set phase: 0x0
<4>[  187.305953] set delay: 0x0
<4>[  187.305958] set ctrl: 0x1
<4>[  187.305962] set pulses: 0x0
<4>[  187.305978] set pwm 2, enable: 0xc, duty cycle: 600 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[  189.255006] set period: 0x1f4
<4>[  189.255016] set duty: 0x0
<4>[  189.255019] set phase: 0x0
<4>[  189.255023] set delay: 0x0
<4>[  189.255028] set ctrl: 0x1
<4>[  189.255032] set pulses: 0x0
<4>[  189.255048] set pwm 2, enable: 0xc, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[  197.432439] set period: 0x1f4
<4>[  197.432447] set duty: 0x14
<4>[  197.432450] set phase: 0x0
<4>[  197.432454] set delay: 0x0
<4>[  197.432459] set ctrl: 0x1
<4>[  197.432463] set pulses: 0x0
<4>[  197.432479] set pwm 2, enable: 0xc, duty cycle: 400 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<4>[  210.625180] set period: 0x1f4
<4>[  210.625188] set duty: 0x0
<4>[  210.625191] set phase: 0x0
<4>[  210.625195] set delay: 0x0
<4>[  210.625200] set ctrl: 0x1
<4>[  210.625204] set pulses: 0x0
<4>[  210.625221] set pwm 2, enable: 0xc, duty cycle: 0 ns, period cycle: 10000,numofpulse: 0, delay: 0 ns, phase: 0 ns, stop: 0
<3>[  573.844433] [VENC]hhe_submit_frame(2410): src yuv resolution is not matched with user set resolution!
<7>[  589.584006] remap_pfn_range start~end: 0xaeed2000 0xaef45000, pyh:0xa6e56 , nocached.
```

```
# cat /proc/meminfo
MemTotal:          32256 kB
MemFree:           12356 kB
MemAvailable:      15472 kB
Buffers:             316 kB
Cached:             9372 kB
SwapCached:            0 kB
Active:             5280 kB
Inactive:           7804 kB
Active(anon):       3408 kB
Inactive(anon):     5496 kB
Active(file):       1872 kB
Inactive(file):     2308 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:          3412 kB
Mapped:             4920 kB
Shmem:              5508 kB
Slab:               3272 kB
SReclaimable:        688 kB
SUnreclaim:         2584 kB
KernelStack:         768 kB
PageTables:          388 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:       16128 kB
Committed_AS:      64060 kB
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
0xbf0e3000-0xbf0fa000   94208 load_module+0x650/0x1aa0 pages=22 vmalloc
0xc2804000-0xc2845000  266240 atomic_pool_init+0x0/0x134 user
0xc2845000-0xc2847000    8192 dma_alloc_attrs.constprop.5+0x64/0x70 user
0xc2848000-0xc284d000   20480 fh_axi_dma_adapt_probe+0x68/0x314 phys=e0300000 ioremap
0xc2e3f000-0xc2e43000   16384 n_tty_open+0x10/0x9c pages=3 vmalloc
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
0xc32f9000-0xc32fb000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d07000 ioremap
0xc32fb000-0xc32fd000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d08000 ioremap
0xc32fd000-0xc32ff000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d08000 ioremap
0xc3300000-0xc3401000 1052672 isp_driver_init+0x10c/0x334 [isp] phys=e8400000 ioremap
0xc3433000-0xc3435000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d09000 ioremap
0xc3435000-0xc3437000    8192 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6d09000 ioremap
0xc3438000-0xc3441000   36864 hhe_dev_init+0x48/0x21c [enc] phys=e70c0000 ioremap
0xc3473000-0xc3475000    8192 hhe_chn_mem_init+0x844/0xaa0 [enc] phys=a6d0a000 ioremap
0xc3478000-0xc347f000   28672 hhe_chn_mem_init+0x524/0xaa0 [enc] phys=a6d02000 ioremap
0xc3480000-0xc34c1000  266240 hhe_dev_init+0x94/0x21c [enc] phys=10000000 ioremap
0xc34dc000-0xc34e0000   16384 hhe_chn_mem_init+0x8f4/0xaa0 [enc] phys=a6d0a000 ioremap
0xc3500000-0xc3601000 1052672 isp_driver_init+0x128/0x334 [isp] phys=e8500000 ioremap
0xc3610000-0xc361a000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bb9000 ioremap
0xc3620000-0xc362a000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bc1000 ioremap
0xc3630000-0xc363a000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bc9000 ioremap
0xc3640000-0xc3667000  159744 vpu_create_grp+0x88/0x58c [vpu] phys=a2400000 ioremap
0xc3670000-0xc367a000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bd1000 ioremap
0xc3680000-0xc36d8000  360448 vpu_create_channel+0x124/0x750 [vpu] phys=a3e55000 ioremap
0xc36e0000-0xc36ea000   40960 hhe_chn_mem_init+0x5f8/0xaa0 [enc] phys=a6bd9000 ioremap
0xc36f0000-0xc36fa000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6be1000 ioremap
0xc3790000-0xc379a000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6be9000 ioremap
0xc37a0000-0xc37aa000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6bf1000 ioremap
0xc37b0000-0xc37ba000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6bf9000 ioremap
0xc37c0000-0xc37ca000   40960 hhe_chn_mem_init+0x714/0xaa0 [enc] phys=a6c01000 ioremap
0xc37d0000-0xc37da000   40960 hhe_chn_mem_init+0x844/0xaa0 [enc] phys=a6c09000 ioremap
0xc3800000-0xc39fc000 2080768 vpu_create_channel+0x124/0x750 [vpu] phys=a3c5a000 ioremap
0xc3a00000-0xc3a5a000  368640 hhe_chn_mem_init+0x524/0xaa0 [enc] phys=a6b61000 ioremap
0xc3a80000-0xc3aa2000  139264 hhe_chn_mem_init+0x8f4/0xaa0 [enc] phys=a6c11000 ioremap
0xc3ba0000-0xc3bc1000  135168 _create_jpg_chan+0xa0/0x2c4 [jpeg] phys=a6e35000 ioremap
0xc3c00000-0xc3e82000 2629632 media_stream_buff_malloc+0x140/0x200 [media_process] phys=a3fac000 ioremap
0xc4000000-0xc5835000 25382912 vpu_create_channel+0x124/0x750 [vpu] phys=a2426000 ioremap
0xc6362000-0xc6365000   12288 fh_ioremap+0x28/0x7c [isp] phys=a4239000 ioremap
0xc6366000-0xc6369000   12288 fh_ioremap+0x28/0x7c [isp] phys=a4239000 ioremap
0xc6369000-0xc636b000    8192 fh_ioremap+0x28/0x7c [isp] phys=a4239000 ioremap
0xc636c000-0xc636f000   12288 fh_ioremap+0x28/0x7c [isp] phys=a4240000 ioremap
0xc6370000-0xc6379000   36864 fh_ioremap+0x28/0x7c [isp] phys=a4239000 ioremap
0xc6380000-0xc638b000   45056 fh_ioremap+0x28/0x7c [isp] phys=a4230000 ioremap
0xc6400000-0xc648f000  585728 fh_ioremap+0x28/0x7c [isp] phys=a4241000 ioremap
0xc6963000-0xc6967000   16384 n_tty_open+0x10/0x9c pages=3 vmalloc
0xc6967000-0xc696b000   16384 n_tty_open+0x10/0x9c pages=3 vmalloc
0xfe000000-0xfe004000   16384 iotable_init+0x0/0xbc phys=e0200000 ioremap
0xfe010000-0xfe014000   16384 iotable_init+0x0/0xbc phys=f0c00000 ioremap
0xfe020000-0xfe024000   16384 iotable_init+0x0/0xbc phys=f0700000 ioremap
0xfe090000-0xfe094000   16384 iotable_init+0x0/0xbc phys=f0000000 ioremap
0xfe0a0000-0xfe0a4000   16384 iotable_init+0x0/0xbc phys=f0800000 ioremap
0xfe0b0000-0xfe0b4000   16384 iotable_init+0x0/0xbc phys=f1300000 ioremap
0xfe0d0000-0xfe0d4000   16384 iotable_init+0x0/0xbc phys=10000000 ioremap
0xfe0e0000-0xfe0e4000   16384 iotable_init+0x0/0xbc phys=ed000000 ioremap
0xfe0e0000-0xfe0e4000   16384 iotable_init+0x0/0xbc phys=ed000000 ioremap
```

```
# cat /proc/vmstat
nr_free_pages 3139
nr_zone_inactive_anon 1374
nr_zone_active_anon 852
nr_zone_inactive_file 577
nr_zone_active_file 468
nr_zone_unevictable 0
nr_zone_write_pending 0
nr_mlock 0
nr_slab_reclaimable 171
nr_slab_unreclaimable 605
nr_page_table_pages 97
nr_kernel_stack 768
nr_overhead 0
nr_bounce 0
nr_free_cma 0
nr_inactive_anon 1374
nr_active_anon 852
nr_inactive_file 577
nr_active_file 468
nr_unevictable 0
nr_isolated_anon 0
nr_isolated_file 0
nr_pages_scanned 0
workingset_refault 0
workingset_activate 0
workingset_nodereclaim 0
nr_anon_pages 853
nr_mapped 1230
nr_file_pages 2422
nr_dirty 0
nr_writeback 0
nr_writeback_temp 0
nr_shmem 1377
nr_shmem_hugepages 0
nr_shmem_pmdmapped 0
nr_anon_transparent_hugepages 0
nr_unstable 0
nr_vmscan_write 0
nr_vmscan_immediate_reclaim 0
nr_dirtied 0
nr_written 0
nr_dirty_threshold 798
nr_dirty_background_threshold 398
```