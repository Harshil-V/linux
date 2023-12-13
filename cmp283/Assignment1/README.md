# Team Members
1. Harshil Vyas
2. Vidhi Agarwal

# Individual Contribution
Harshil- He setup the gcp instance environment for assignment 1 and did the coding for entry,exit and tertiary controls. 

Vidhi- Helped with the research for the exit controls from the SDM and helped in coding the procbased and secondary procbased controls.

# Steps to do the assignment:
1. Fork the linux kernel code repo - https://github.com/torvalds/linux into your github repository. It will create a copy of the source code in your repo.
2. Install the Dependencies to the GCP instance:
```bash
$ sudo apt-get install libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf llvm
```

3. Clone the forked repo into the GCP instance using command- git clone https://github.com/Harshil-V/linux.git.
```bash
$ git clone https://github.com/Harshil-V/linux.git
```

4. Copy the cmpe283-1.c and the Makefile into the instance.
```bash
$ cd linux
$ cp /boot/[user version] .config
```
5. Refer the Intel SDM and make code changes in cmpe283-1.c for the entry, exit, procbased, secondary procbased and teritiary procbased vmexit controls.
6. Do a make in the root directory.
7. By doing ls, verify that a **.ko** file was generated.
8. Now, to verify code changes, do **sudo insmod cmpe283-1.ko** and then **dmesg**, you should be able to see VMX capabilities of all the MSRs.
```bash
$ sudo insmod cmpe283-1.ko
$ dmesg
```
