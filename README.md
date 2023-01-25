# router-emulator

## Pre-configuration on MAC
On Mac you will need to add a loopback interface alias to 10.0.4.1 before running:

`sudo ifconfig lo0 alias 10.0.4.1`

## Running
* Start with SSH forwarding:

`sudo qemu-system-x86_64 -hda netlab.img -smp 4 -m 2G -net user,hostfwd=tcp:10.0.4.1:22-:22 -net nic`

* Start with SSH forwarding and CPU acceleration

`sudo qemu-system-x86_64 -hda netlab.img -smp 4 -m 2G -cpu host,vmware-cpuid-freq=on -accel hvf -net user,hostfwd=tcp:10.0.4.1:22-:22 -net nic`

* Start with SSH and SNMP port forwarding:

`sudo qemu-system-x86_64 -hda netlab.img -smp 4 -m 2G -net user,hostfwd=tcp:10.0.4.1:22-:22,hostfwd=udp:10.0.4.1:161-:161 -net nic`

