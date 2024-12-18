# Cross-Compiling-Preempt_Rt-patch-on-any-raspbery-pi
Preempt-RT patch to the kernel source for raspberry pi
**Introduction**
Raspbian lite with fully preemptive real-time kernel. This repo follows the official methodology to cross compile the kernel as explained here https://www.raspberrypi.com/documentation/computers/linux_kernel.html.

In addition to building the kernel, this repo also offers a raspbian lite sd card image with the built kernel ready to be used on a raspberry pi.

The fully preempt rt model is enabled inside Dockerfile using ./scripts/config --enable. The fully preempt rt model can be enabled only if virtualization is disabled.
For building you only need your Laptop, Computer. After successfull build , it will create a zip file of image. you can directly write that zip file on your sdcard using "pi imager". 

**User Guide**

Install Required Tools: Ensure you have the essential tools installed for cross-compilation.

sudo apt update

sudo apt install build-essential libncurses-dev bison flex libssl-dev bc

Install Cross-Compiler: Depending on your target architecture (e.g., ARM), install the appropriate cross-compiler. For example, for ARM:

sudo apt install gcc-arm-linux-gnueabihf

git clone “https://github.com/remusmp/rpi-rt-kernel”

cd rpi-rti-kernel

Clone this repository and run** make [platform]** where platform is either:

    64 bits: Pi5, Pi4, PiCM4, Pi400, Pi3, PiCM3, PiZero2
    32 bits: Pi1, PiZero, PiCM1, Pi2, Pi3-32, PiCM3-32, PiZero2-32, Pi4-32, Pi400-32, PiCM4-32
For example i'm making it for Pi3-32
make Pi3-32    (Note: for pi3 64 bit, it gives errors on boot) it will create image file
locate that image file and open that directory in terminal 
now after that connect your sd card to your system 

sudo dd if=r of=/dev/sda status=progress   it will burn image file r on sd card where “r” is the image file name  or you can use pi imager to directly write zip image file to your sdcard


now insert sdcard in raspberry pi and boot it
