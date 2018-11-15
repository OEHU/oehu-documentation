#Get Started

So, you want to have full access to your energy data and view nice usage charts. It takes three steps to be up & running: 

* [**Part 1:** Get the right stuff] (#part1)
* [**Part 2:** Connect/prepare your OEHU] (#part2)
* [**Part 3:** Configure & go!] (#part3)

## <a name="part1"></a> Part 1: get the right stuff
We provide an all-in-one set for your convenience: <https://www.sossolutions.nl/raspberry-smartmeter-voor-oehu-leden>

To be able to use OEHU and read the data of your smart meter you need this equipment:

* Raspberry Pi (Rpi) (preferably version 2B and up)
* Power + micro-usb cable for the Rpi
* Smart Meter P1 cable
* Micro-SD card of 8GB
* Optional: Ethernet cable to connect to your home internet network if your Rpi doesn’t have WiFi or you don’t have a WiFi dongle.

When you have the right stuff, continue with part 2.

## <a name="part2"></a> Part 2: Preparations
**Step 1**: download the OEHU software for your Rpi: <https://api.oehu.org/downloads/oehu-pi.zip>;

**Step 2**: Extract the ZIP file. 

Copy the contents of the unzipped folder to the micro-SD-card.

Our set provides a SD-card adapter in case your laptop lacks an microSD-card slot.

**Step 3**: Set your WiFi password

If you have a WiFi network, set your WiFi password. Otherwise just connect an ethernet cable.

This is how you set your WiFi password:

* On your SD card, open the file wpa_supplicant.conf
* Fill in your WiFi network name (SSID) and password
* Save the file

NB. Don't use the guest network of your router!

Now you can remove the SD card from your laptop.

**Step 4**: connect everything to your Rpi:

1. Slide the micro-SD card into the designated slot of the Rpi;
2. Connect the P1 connector of the P1 cable to the P1 port of your smart meter.
NB. Usually you have to slide aside a rubber lit to access the P1 port;
3. Connect the USB connector of the P1 cable to the Rpi;
4. Finally, connect the power cable to the Rpi and plug it into a power socket. This will make your Rpi boot. You'll see the red and green leds fire up.
5. Get yourself a nice cup of coffee, because the booting will take up to 20 minutes. Just let the Rpi do its thing. You know it is ready when you can open this website: <http://oehu.local>;

## <a name="part3"></a> Part 3: Configure & Go!

**Step 1**: To configure your Rpi go to <http://oehu.local>;

**Step 2**: Fill in your location and give in the accuracy in meter that you want the viewer to show your location on the map. Click Next. 
NB. It is possible to choose anonymity instead of giving in your precise location. Check the box if you want to stay anonymous.

**Step 3**: Specify the type of building where the smart meter is located. Also specify the amount of occupants of the building. 

Click Next. 

**Step 4**: Choose your username and password that will give you access to your dashboard on the OEHU website. Make sure you save the passphrase, username and password by writing it down on paper or storing it in your password manager. The passphrase is important: It gives you access to your data, and lets you modify it.

Click Next.

**Step 5**: You will now enter your dashoboard on the OEHU website: <http://oehu.org/dashboard>  
Typically, after 10 seconds the first information of your smart meter should be visible in the dashboard.

The amount of active meters on the OEHU homepage is updated.

Congratulations!
You're now running your own node. Thank you for using OEHU. In the future, just go to oehu.org to view your dashboard 😄

##Questions about the setup?
Join the OEHU community on Telegram <https://t.me/joinchat/A8b03hI61nBIbnVF18582A> or ask your question via Twitter <https://twitter.com/oehu_project>. We are happy to help if needed!

##Troubleshooting
Make sure that your microSD card is formatted in FAT format.

The RPi version 2B has ARMv6 hardware. The RPi version 3(+) has ARMv7 hardware. Make sure you download the right package for your hardware. NB. The package for the RPi version 2B is not available. The package that is available is tested for RPi 3 only.

