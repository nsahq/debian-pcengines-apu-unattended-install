# Debian PCEngines APU Unattended Install
Payload for running Debian on PCEngines APU. Fully unattended Debian netboot installation using USB stick with working console support via serial/null modem/usb.

The files provided are intended for educational purposes and to service as a base to build your own from. They will work as is, but *you must* make sure to *change the user and password supplied as the default*.

## Details

The files provided contains the following:
- Modified grub config with serial support
- Modified isolinux config with serial support
- Modified interactive menus
- preseed for unattended installation

The files can either be added to an installation image and flashed to a USB drive, or burned as a CD/DVD.

To create a hybrid ISO (for bootable USB) follow the guide at https://github.com/nsahq/debian-custom-image-creator .

The apu directory in this repository can be copied directly to the payload folder in the base directory of debian-custom-image-creator.

## Step-by-step

1. Clone the repos
```bash
git clone https://github.com/nsahq/debian-pcengines-apu-unattended-install.git && git clone https://github.com/nsahq/debian-custom-image-creator.git
```
2. Copy the apu directory to payload
```bash
mkdir -p debian-custom-image-creator/payload && cp -r debian-pcengines-apu-unattended-install/apu debian-custom-image-creator/payload/
```
3. Enter the directory and run the script
```bash
cd debian-custom-image-creator && ./reimager.sh -l CoolOS -n apuinstaller -p apu -a amd64 -r testing
```
4. Add the image to the installation medium of you want to use. (USB guide in reimager repo)

WARNING!
The pre-seed file contains pre-set username and password:
User: apu
Password: changeme

To change the user and password either do it manually once the system is installed, or by altering the preseed.seed file in apu/preseed/preseed.seed under the user section.

DO NOT LEAVE THE USER AND PASSWORD UNCHANGED ON YOUR APU!

