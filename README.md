This repository contains updated patches for spoofing rdtsc while running KVM  

Tested on Linux 6.1.19 on an AMD CPU

Credits to [this repository](https://github.com/WCharacter/RDTSC-KVM-Handler) for making this possible

View diff files for changes

# Instructions
* Clone official Linux kernel
* Install requirements for compiling kernel
    * Example for Debian based distros:
```
sudo apt-get install build-essential libncurses-dev bison flex libssl-dev libelf-dev
```
* Change directory into the Linux kernel repository you just cloned
* Make the necessary modifications
    * vmx.c is going to /arch/x86/kvm/vmx
    * svm.c is going to /arch/x86/kvm/svm
* Copy your current kernel configuration into your kernel folder
```
cp -v /boot/config-$(uname -r) .config
```
* Make kernel
```
make -j $(nproc)
```
* Install kernel
```
make modules_install && make install
```
* Reboot
