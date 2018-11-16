## This guide explains how to create your custom NOOBS OS

_Guide is based on https://www.linux.org/threads/create-your-own-pi-distro.4486/_

### 1. Download NOOBS & configure your Pi like you want to

Download NOOBS: https://www.raspberrypi.org/downloads/noobs/

Install and configure your Pi like you want to. For example, use [this guide](https://github.com/BlocklabNL/VEL/blob/master/NOTES-PREVIEW.MD#raspberry-pi-setup) if you want to install OEHU.

### 2. Backup your prefered OS configuration

Now, as soon as you have your OS configured like you wanted to, create root.tar based on your `/` directory:

    cd /

    sudo tar -cpvf root.tar /bin /boot /debootstrap /dev /etc /home /lib /media /mnt /opt /proc /root /run /sbin /srv /sys /tmp /usr /var --exclude=proc/* --exclude=sys/* --exclude=dev/pts/*

Now, create a boot.tar based on your `boot` folder:

    cd /boot
    sudo tar -cpvf /boot.tar *

You now have 2 files needed for your custom OS.

### 3. Copy & compress tars

Copy the 2 freshly created tars to your computer.

Then, compress the two files as needed by the boot loader program:

    xz -9 -e root.tar
    xz -9 -e boot.tar

### 4. Create your Linux distribution

You have downloaded NOOBS in step 1. Extract the downloaded file, in example `NOOBS_v2_9_0.zip`.

In the `os` folder, duplicate the Raspian folder & call it "OEHU". Delete all folders in `os` except OEHU.

In the root, modify `os.json` to your wishes.

Optionally, add a 40x40 pixels `OEHU.png` to the root.

Optionally, change the images in `slides_vga`.

Inside the OEHU folder, replace `root.tar.xz` and `boot.tar.xz` with the two you made previously.

### 5. Configure last things

Create a new, empty file: wpa_supplicant.conf.

Add the following content to the file:

// Open `wpa_supplicant.conf` and fill in your WiFi network name (SSID) and related passphrase.

    country=NL
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1

    network={
      ssid="SSID OF YOUR WIFI NETWORK"
      psk="PASSWORD FOR ACCESS TO YOUR WIFI NETWORK"
    }

#### Make sure Raspbian installs without a LCD display needed

Edit the file `recovery.cmdline` and add the word `silentinstall` at the end of the first line. This will auto install Raspbian, and reboot into the desktop when finished.

(If you find `recovery.cmdline` has a blank line at the end, delete the line, otherwise silentinstall won't work)

Lastly, in the `os` folder on the SD card, delete all folders except Raspbian.

#### Make sure you can have ssh access

Place a file called `ssh` in the root of the SD card. This will make sure you can access the Pi using SSH.

### 6. Insert the SD into the Pi & power on

Now is the time to remove the SD card from your laptop, put it in your Pi & boot the Pi by powering on. It will automatically install Raspbian.

The installation process takes approximately 20 minutes on a Raspberry Pi 3 B+.

If you ever want to SSH connect, open a terminal and type:

    ssh pi@oehu.local

____

For uploading the package to the server, use the following command:

    rsync -avzhe ssh oehu-pi.zip vel@167.99.33.155:/var/www/downloads

## DOCUMENTATION: Update OEHU image

Once in a while developers can update the OEHU image. If you want to update OEHU, perform the following actions:

        sudo apt-get update -y
        sudo apt-get upgrade -y

        ~/oehu-update/update.sh

Also, check if SWAP is enabled and at least 400M:

    sudo swapon --show

Check if [rpimonitor](https://github.com/XavierBerger/RPi-Monitor) is installed.

    whereis rpimonitor

If not installed, install rpimonitor:

    https://xavierberger.github.io/RPi-Monitor-docs/11_installation.html#installation-from-repository
