# Notes, links to other projects, random thoughts and so on

## Raspberry pi setup:

### Get Noobs

Use Noobs to install Raspbian OS on your Pi.

&raquo; [Download Noobs](https://downloads.raspberrypi.org/NOOBS_latest)

### Install Noobs on your pi

Make sure you have the micro-SD card inserted into your laptop.

In the previous step you downloaded a ZIP. Extract the ZIP files to the SD card.

### Configure WiFi on your Pi

You still have the SD card inserted in your laptop.

In your file explorer, open the SD card.

#### Setup WiFi

Create a new, empty file: `wpa_supplicant.conf`.

Add the following content to the file:

    country=NL
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1

    network={
      ssid="SSID OF YOUR WIFI NETWORK"
      psk="PASSWORD FOR ACCESS TO YOUR WIFI NETWORK"
    }

Save the file.

#### Make sure Raspbian installs without a LCD display needed

Edit the file `recovery.cmdline` and add the word `silentinstall` at the end of the first line. This will auto install Raspbian, and reboot into the desktop when finished.

(If you find `recovery.cmdline` has a blank line at the end, delete the line, otherwise silentinstall won't work)

Lastly, in the `os` folder on the SD card, delete all folders except Raspbian.

#### Make sure you can have ssh access

Place a file called `ssh` in the root of the SD card. This will make sure you can access the Pi using SSH.

#### Insert the SD into the Pi & power on

Now is the time to remove the SD card from your laptop, put it in your Pi & boot the Pi by powering on. It will automatically install Raspbian.

The installation process takes approximately 20 minutes on a Raspberry Pi 3 B+.

### Now connect to the Pi using SSH

On your laptop, connect to the same WiFi network as the Pi.

Then, open a Terminal.

On the terminal, type: `ssh pi@raspberrypi.local`.

The password of the pi = `raspberry`

### Updating Pi

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get --fix-broken install
sudo apt-get upgrade
```

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/y9KlLxtMTOA?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

### Setup hostname

To change the hostname to oehu run:

```
sudo raspi-config
```

Then go to Network options -> Hostname -> and type "oehu".

You need to reboot for the changes to take effect.

After rebooting, connect to the Pi via ssh using: `ssh pi@oehu.local`

### Change SWAP memory from 100MB to 1G

1. Remove swap: `sudo swapoff -a`
2. Add swap: [link](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)

### Software needed for data uploading

Node 10.10 is tested and working steadily. Follow the instructions below to install node.

    curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
    sudo apt install -y nodejs

Confirm that node is installed succesful:

    node -v

After succesfully installing NodeJS, install the specific OEHU software:

```
git clone https://github.com/oehu/oehu-setup-api
cd oehu-setup-api
npm install
```

Running `npm install` will cost some time. +- 15 minutes on RPi 3 B+.

### Run stuff at startup

Open a new terminal & connect to the Pi via ssh using: `ssh pi@oehu.local`.

#### install pm2

```
sudo npm install -g pm2
pm2 startup
```

**Run the output** that you see in the terminal after running the `pm2 startup` script.

#### install http-server

```
sudo npm install -g http-server
```

#### Configure oehu-setup-api

Go to the oehu-setup-api: 

```
cd ~/oehu-setup-api
```

In this folder, run:

```
pm2 start sudo --no-automation --name oehu-setup-api -- npm run start
```

#### Configure oehu-website

Run the following commands to prepare the site:

    cd ~/
    git clone https://github.com/OEHU/oehu-website.git
    cd oehu-website
    git checkout setup
    npm install
    npm run build

Now add this process to pm2:

    cd build-copy
    pm2 start sudo --no-automation --name oehu-website -- http-server . -p 80

#### Run all pm2 programs on boot

Make it run at boot

```
pm2 save
```

### Make cron that automatically pulls updates from git

    cd ~/
    git clone https://github.com/OEHU/oehu-update.git

Run `crontab -e`. Add:

      0 6  *   *   1     /home/pi/oehu-update/update.sh
      @reboot            /home/pi/oehu-update/update.sh

Every 1st day of the week at 6:00am, the update script will run.

____

You have now installed everything needed for this alpha testing session.

You're ready to continue the normal setup guide at https://oehu.org/get-started.

Start at **Part 3: Configure & Go!** => **Step 5** 
