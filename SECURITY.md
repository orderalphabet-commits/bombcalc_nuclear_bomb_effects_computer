# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.
/*
* author Huber Flores
*/

### CyanogendMod7.2
### Builded in 64 bits Machine with Ubuntu quantal quetzal 12.10 

# Install android SDK
# Download version x86_64
# Tutorial http://developer.android.com/sdk/index.html

### Install dependencies
$ sudo apt-get update
$ sudo apt-get install zip build-essential curl git-core \
      python gcc patch flex bison gperf \
      g++ squashfs-tools \
      ia32-libs g++-multilib zlib1g-dev \
      lib32z1-dev lib32ncurses5-dev \
      gcc-multilib libwxgtk2.8-dev \
      tofrodos texinfo mtools ccache \
      gnupg libc6-dev x11proto-core-dev \
      libx11-dev lib32readline-gplv2-dev \
      libgl1-mesa-dev libxml2-utils


$ sudo apt-get install gnupg flex bison gperf build-essential squashfs-tools \
     zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
     libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
     libgl1-mesa-dev g++-multilib mingw32 tofrodos \
     python-markdown libxml2-utils xsltproc zlib1g-dev:i386


$ sudo apt-get install git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev \ 
     libwxgtk2.8-dev squashfs-tools zip pngcrush schedtool libxml2 xsltproc


# 64 bits dependecies

$ sudo apt-get install lib32z1-dev lib32ncurses5-dev lib32readline-gplv2-dev \
      gcc-4.7-multilib g++-4.5-multilib



# Install java
# Java SE 1.6 is required (other version, even greater is not accepted by the compiler)
# Download jdk-6u34-linux-x64.bin

$ chmod +x jdk-6u34-linux-x64.bin
$ sudo ./jdk-6u34-linux-x64.bin
$ sudo mv jdk1.6.0_34 /usr/lib/jvm/

$ sudo apt-get install update-java 
$ sudo update-java (Choose your java version, if you have more installed)


### Set up environment (Follow the instructions to have similar environments)

$ mkdir CyanogenModBuild
$ cd CyanogenModBuild
$ mkdir environment
$ cd environment
$ mkdir ~/bin
$ mkdir ~/android/system


# Install repo command in /bin
$ curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo
$ chmod a+x ~/bin/repo

# Open your bashrc file (in my case)
$ cd /homer/huber
$ nano .bashrc

# add the following line at the end
export PATH=$PATH:/home/huber/android-linux-x86_64/sdk/platform-tools:/home/huber/Desktop/CyanogenModBuild/environment/bin

export USE_CCACHE=1


# Now you can call $ repo and $ adb from any location
# Initialize repository

$ cd ./android/system
$ repo init -u git://github.com/CyanogenMod/android.git -b gb-release-7.2

# it will take time
# Once finished, then synchronize repositories (-j16 is for the number of concurrent threads)
$ repo sync -j16

# Copy proprietary files from the device
# Plug the device to your computer

$ cd ~/android/system/device/samsung/galaxys2/ 
$ ./extract-files.sh

# No missing files or errors should appear. If some files are missing, then you can try to find the missing file by downloading a stable CyanogenMod ROM (http://get.cm/?device=galaxys2&type=stable,  cm-7.2.0-galaxys2.zip)

# Download the ROM Manager
$ cd ./android/system/vendor/cyanogen/
$ ./get-rommanager 

# Synchronize again for updates
$ cd ~/android/system/ 
$ repo sync 

# Build CyanogenMod7.2
$. build/envsetup.sh 
$ brunch galaxys2 


# Possible errors may appear

1)
Unknown parameter xmlns for tags/attrs...
make: *** [out/target/product/galaxys2/obj/STATIC_LIBRARIES/libwebcore_intermediates/WebCore/XMLNSNames.cpp] Error 255

# [SOLVED]: This is a bug from GCC 4.7, try to downgrade GCC to 4.5 or 4.6.2
# if you have 4.7 already installed, then install 4.5 or 4.6. Later, switch between compilers with the update-alternatives command, below procedure

$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.7 47
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.6 46
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.5 45


$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.7 47
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.6 46
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.5 45


$ sudo update-alternatives --config gcc
There are 3 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path              Priority   Status
------------------------------------------------------------
  0            /usr/bin/gcc-4.7   47        auto mode
* 1            /usr/bin/gcc-4.5   45        manual mode
  2            /usr/bin/gcc-4.6   46        manual mode

  3            /usr/bin/gcc-4.7   47        manual mode


In short, both, GCC and G++ should have same version (e.g 4.5)


2) 
# Missing prop files dependecies
# Extract them from the stable version as discussed before


3) Cloud issue (Amazon - Generic Ubuntu)
# The following packages have unmet dependencies:
# ia32-libs : Depends: ia32-libs-multiarch but it is not installable
# E: Unable to correct problems, you have held broken packages.

# [SOLVED]:
# Enable the installation of i386 packages on your 64 bits system:

$ dpkg --add-architecture i386
$ apt-get update

# Once the compilation process has finished, copy the ROM to your internal sdcard cm-7-20130131-UNOFFICIAL-galaxys2.zip (location:/android/system/out/target/product/galaxys2/)

### Flash the ROM in the device (Remember to have a backup)
# Open CWM
# Choose install zip from internal sdcard
# Install ROM cm-7-20130131-UNOFFICIAL-galaxys2.zip
# Wipe factory
# Wipe cache
# Restart device











