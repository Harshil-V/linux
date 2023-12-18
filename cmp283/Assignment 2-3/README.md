
# CMPE 283: Virtulization - Assignment #2 / #3

## Students:
- [Harshil Vyas](https://www.linkedin.com/in/harshil-vyas/)
- [Vidhi Agarwal](https://www.linkedin.com/in/vidhi-ag/)

## Setup
1. Install the Linux Kernal Source Code
   
```bash
$ git clone https://github.com/Harshil-V/linux
```

2.  Change Directory to linux

```bash
$  cd linux
```

3. Install Package

```bash
apt-get install build-essential kernel-package fakeroot libncurses5-dev libssl-dev ccache bison flex libelf-dev 
```

4. Copy Boot Config file to the Linux Folder

```bash
$ sudo bash && cp /boot/config-[based on your vm] .config
```

5. Make Old Config

```bash
$ make oldconfig
```

6. Make the kernal image 

```bash
$ make perpare && make -j[# of cpus of you vm] 
```

7. Make modules

```bash
$ make -j8 modules
```

8. Install Modules  (TODO UPDATE THE COMMAND)

```bash
$ sudo make INSTALL_MOD_STRIP=1 modules_install && sudo make install
```

9.  Reboot

```bash
$ reboot
```

10. Check the Kernal Module Change

```bash
$ uname -a
```

11. Download the required to Hosting a nested vm

```bash
$ sudo apt-get install qemu-kvm libvirt-bin virtinst bridge-utils cpu-checker
```

12. Instal an  Linux ISO Image that you like

We picked CentOS:
https://centos.mirror.shastacoe.net/centos/7.9.2009/isos/x86_64/

```bash
$ wget "https://centos.mirror.shastacoe.net/centos/7.9.2009/isos/x86_64/CentOS-7-x86_64-Minimal-2207-02.iso"
```

1.  Update KVM and KVM_INTEL

```bash
$ rmmod kvm_intel && rmmod kvm && modprobe kvm && modprobe kvm_intel && lsmod | grep kvm
```

14. Create the nested VM

```bash
$ virt-install --network bridge:virbr0 --name nested-vm --os-variant=centos7.0 --ram=2048 --vcpus=2 --disk size=20 --graphics none --location=[your_path] --extra-args="console=tty0 console=ttyS0,115200" --check all=off
```

15. Start The VM and enter console

```bash
$ virsh start [your VM name]
$ virsh console [your VM name]
$ virsh shutdown [your VM name]
```

## Questions

### Assignment #2 (0x4FFFFFFF) & (0x4FFFFFFE)

1. Contribution
   
    > Answer: <br> Harshil - Set up the environment for assignment 2 with the nested VM and did coding for leaf node 0x4FFFFFFF. <br> <br> Vidhi - Did coding for leaf node 0x4FFFFFFE, created the test program and verified the results.

2. Describe in detail the steps you used to complete the assignment. 
   
   > Please Read the step mentioned above

### Assignment #3 (0x4FFFFFFC) & (0x4FFFFFFD)

1. Contribution
   
   > Answer: <br> Harshil - Set up the environment for assignment 3 with the nested VM and did coding for leaf node 0x4FFFFFFC. <br> <br> Vidhi - Did coding for leaf node 0x4FFFFFFD, created the test program and verified the results for the assignment questions along with Harshil.

2. Describe in detail the steps you used to complete the assignment. 
   > Please Read the step mentioned above

3. Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail?
 
    > Answer: <br>  No, the number of exits does not increase at a stable rate. For example, for exit number 31, the total exits doubled, for exit number 1, the total exits increased by just a small amount and for exit number 47, it didn’t change at all. <br> <br> During a full VM boot, exits before boot were 739532, and after the boot, they were 1450170. <br> <br> VM operation we tried: ping 8.8.8.8, for most of the type of exits, the total number of exits after this operation did not show any drastic change.
 

4. Of the exit types defined in the SDM, which are the most frequent? Least?

    > Answer: <br> For us, out of all the exits defined in SDM, the most frequent is exit number 10, with total exits as 246621 and the least ones were 29 and 55, with total exits as only 2.






