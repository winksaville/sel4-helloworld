# sel4-helloworld

This project is a "simple" hello world type program for seL4,
The source is [main.c](.https://github.com/winksaville/sel4-helloworld/blob/master/src/main.c).
It consists of multiple git repositorie managed by [Google Repo](https://code.google.com/p/git-repo/)
as are other seL4 projects. To get all of this and all of the other necessary
repositories for seL4-helloworld go to
[sel4-helloworld-manifest](https://github.com/winksaville/sel4-helloworld-manifest)
and follow the instructions there.

Next you need the toolchain prerequisites are [here](https://sel4.systems/Download/DebianToolChain.pml).
Then get the configuration and make the images:
```
$ cp configs/ia32_simulation_helloworld_defconfig .config
$ make
```
Finally, you can then run the simulation under qemu. To quit type "ctrl-a" then "c" and "q" and then "carriage return/Enter" to exit:
```
$ make simulate-hw-ia32
qemu-system-i386 \
	-m 512 -nographic -kernel images/kernel-ia32-pc99 \
	-initrd images/helloworld-image-ia32-pc99

Boot config: parsing cmdline 'images/kernel-ia32-pc99 '
Boot config: console_port of node #0 = 0x3f8
Boot config: debug_port of node #0 = 0x3f8
Boot config: max_num_nodes = 1
Boot config: num_sh_frames = 0x0
Physical memory usable by seL4: start=0x100000 end=0x1fc00000 size=0x1fb00000
Kernel loaded to: start=0x100000 end=0x156000 size=0x56000 entry=0x10003e
Kernel stack size: 0x1000
APIC: Bus frequency is 1000 MHz
ACPI: RSDP paddr=0xf62c0
ACPI: RSDP vaddr=0xdfcf62c0
ACPI: RSDT paddr=0x1ffe16a9
ACPI: RSDT vaddr=0xdffe16a9
ACPI: MADT paddr=0x1ffe15f9
ACPI: MADT vaddr=0xdffe15f9
ACPI: MADT apic_addr=0xfee00000
ACPI: MADT flags=0x1
ACPI: MADT_APIC apic_id=0x0
ACPI: MADT_IOAPIC ioapic_id=0 ioapic_addr=0xfec00000 gsib=0
ACIP: MADT_ISO bus=0 source=0 gsi=2 flags=0x0
ACIP: MADT_ISO bus=0 source=5 gsi=5 flags=0xd
ACIP: MADT_ISO bus=0 source=9 gsi=9 flags=0xd
ACIP: MADT_ISO bus=0 source=10 gsi=10 flags=0xd
ACIP: MADT_ISO bus=0 source=11 gsi=11 flags=0xd
ACPI: 1 CPU(s) detected
Detected 1 IOAPICs, but configured to use PIC instead
Will boot up 1 seL4 node(s)
Detected 1 boot module(s):
  module #0: start=0x157000 end=0x1f0908 size=0x99908 name='images/helloworld-image-ia32-pc99'
ELF-loading userland images from boot modules:
  module #0 for node #0: size=0x130000 v_entry=0x8052232 v_start=0x8048000 v_end=0x8178000 p_start=0x1f1000 p_end=0x321000
Moving loaded userland images to final location: from=0x1f1000 to=0x156000 size=0x130000
PCI: Detected device @ bus=0x0 dev=0x0 fun=0x0: vid=0x8086 did=0x1237 type=normal
PCI: Detected device @ bus=0x0 dev=0x1 fun=0x0: vid=0x8086 did=0x7000 type=normal
PCI: Detected device @ bus=0x0 dev=0x1 fun=0x1: vid=0x8086 did=0x7010 type=normal
PCI:     BAR[4] ignored: PCI IO space not supported
PCI: Detected device @ bus=0x0 dev=0x1 fun=0x3: vid=0x8086 did=0x7113 type=normal
PCI: Detected device @ bus=0x0 dev=0x2 fun=0x0: vid=0x1234 did=0x1111 type=normal
PCI:     BAR[0] address=0xfd000000 size=0x1000000
PCI:     BAR[2] address=0xfebf0000 size=0x1000
PCI: Detected device @ bus=0x0 dev=0x3 fun=0x0: vid=0x8086 did=0x100e type=normal
PCI:     BAR[0] address=0xfebc0000 size=0x20000
PCI:     BAR[1] ignored: PCI IO space not supported

Starting node #0
Switching to a safer, bigger stack
"Hello, World!"
Ignoring call to sys_exit_group
Ignoring call to sys_rt_sigprocmask
Ignoring call to sys_gettid
Ignoring call to sys_getpid
sys_tgkill assuming self kill
Undelivered IRQ: 0
QEMU 2.3.0 monitor - type 'help' for more information
(qemu) q
```
