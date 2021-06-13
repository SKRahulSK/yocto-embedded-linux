# yocto-embedded-linux

## yocto supported architectures
    1. ARM (qemuarm)
    2. x86 (qemux86)
    4. x86-64 (qemux86-64)
    5. PowerPC (qemuppc)
    6. MIPS (qemumips, qemumips64)  - Microprocessor without Interlocked Pipelined Stages(MIPS)

## yocto release versions (branches)
    1. Thud - 2.6 - October 2018
    2. Sumo - 2.5 - April 2018

## requirements
    sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath socat cpio python python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping libsdl1.2-dev xterm

## This project is worked on sumo branch of yocto

1. clone the yocto poky repo (Here we are using "sumo" branch)
    `git clone -b sumo git://git.yoctoproject.org/poky`

2. Build environment specification
    Go to poky directory and run the following command
    `source oe-init-build-env BULD_DIR_NAME`
    Ex: `source oe-init-build-env build-qemux86`

3. In `build-qemux86` directory we can conf/local.conf file. It will be saved with default values

4. Building basic core-image-minimal build
    `bitbake core-image-minimal`

5. All the build images will be in `tmp/deploy/images/qemux86/` directory of build folder

6. 



## Image differences
    core-image-minimal gives only the option of command line interface,
    with core-image-sato we can have gui interface for the image

