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

1. clone the yocto poky repo (Here we are using "sumo" branch) `git clone -b sumo git://git.yoctoproject.org/poky`

2. Build environment specification
    Go to poky directory and run the following command
    `source oe-init-build-env BULD_DIR_NAME`
    Ex: `source oe-init-build-env build-qemux86`

3. In `build-qemux86` directory we can conf/local.conf file. It will be saved with default values

4. Building basic core-image-minimal build
    `bitbake core-image-minimal`

5. All the build images will be in `tmp/deploy/images/qemux86/` directory of build folder

6. Run the following command in `tmp/deploy/images/qemux86/` directory to start the qemu of the image created
    `runqemu MACHINE_NAME KERNEL_IMAGE_ROOTFILESYSTEM_NAME`
    Ex: `runqemu qemux86 bzImage-qemux86.bin`


## Image differences
    `core-image-minimal` gives only the option of command line interface,
    with `core-image-sato` we can have gui interface for the image


## Build system
    - Poky: Both a reference distribution and build system
            - It contains "layers" of metadata
            - We can clon it from git://git.yoctoproject.org/poky
            - Primary poky layers
                - oe-core (It is in poky/meta directory)
                - meta-yocto-bsp (It contains the reference board bsps)
                - meta-yocto (It contains reference distributions and other meta informations)
### Metadata
Four categories of metadata:
    1. Recipes (*.bb) : It describes the instructions to build a single package
            - Recipe tasks (TODO: Write in detail)
            - Recipe variables (TODO: Write in detail)
    2. Configuration (*.conf): It controls overall behaviour of build process
            - build/conf/local.conf: It specifies the build details like MACHINE, build operation, and other detials
            - build/conf/bblayers.conf: It is used to add the layers to the yocto build environment
    3. Classes (*.bbclass): Inheritance mechanism for common functionality
            - Provide encapsulation and inheritance logic
            - Abstracts common functionility and share it amongst several recipes
            - Some important classes are:
                1. base.bbclass (Very important) (TODO: Write in detail)
                2. autotools.bbclass
                3. pkgconfig.bbclass
                4. kernel.bbclass
                5. image.bbclass
                6. rootfs*.bbclass
                7. sanity.bbclass
            - Every recipe inherits the base.bbclass automatically
    4. PackageGroups (special *.bb): Groups packages for a filesystem image
            - Way to group packages by functionality or common purpose
            - recipe-cores/packagegroups/
            - All package groups are identified by packagegroup- prefix
            - Commonly used package groups:
                - packagegroup-core-boot
                - packagegroup-core-buildessential
                - packagegroup-core-tools-debug
                - packagegroup-core-nfs
                - packagegroup-core-ssh-dropbear
                - packagegroup-core-ssh-openssh
            

## Bitbake commands
    - bitbake
    - bitbake-layers show-layers
    




    