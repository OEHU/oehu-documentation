#Getting Started

This document tells you how to get your smart meter hooked up to OEHU. By doing so you will store your energy usage data in a decentralized database. From there you can view your data realtime in your OEHU dashboard.  

We divided the guide in 3 parts. Just follow the steps and your smart meter will be online quickly. 

* [**Part 1:** get the right stuff] (#part1)
* [**Part 2:** Preparations] (#part2)
* [**Part 3:** Configure & Go!] (#part3)

## <a name="part1"></a> Part 1: get the right stuff
To be able to use OEHU to read the data of your smart meter you need the following equipement:

* Raspberry Pi (Rpi) (preferably version 2B and up);
* Power cable (micro-usb) for the Rpi;
* Ethernet cable to connect to your home internet network if your Rpi doesn’t have wifi or you don’t have a wifi dongle;
* Smart Meter cable (P1 cable); (available here: <https://www.sossolutions.nl/slimme-meter-kabel>)
* Micro-SD card of 8GB. 

We provide an one-stop shopping cart for your convenience. You can purchase everything you need here <link to shopping cart>. (SOSSolutions?)

When you have the right stuff, continue with part 2.

## <a name="part2"></a> Part 2: Preparations
**Step 1**: download the OEHU software for your Rpi: <http://oehu.org/noobs-oehu>;

**Step 2**: unzip the downloaded image and copy the file to the micro-SD-card;
NB. our set provides a USB SD-card reader in case your laptop lacks an SD-card slot.

**Step 3**: connect everything to your Rpi:

1. Slide the micro-SD card into the designated slot of the Rpi;
2. If your Rpi doesn’t have Wifi build-in: Connect the Ethernet cable or Wifi dongle to the Rpi, otherwise skip this;
3. Connect the P1 connector of the P1 cable to the P1 port of your smart meter.
NB. Usually you have to slide aside a rubber lit to access the P1 port;
4. Connect the USB connector of the P1 cable to the Rpi;
5. Finally, connect the power cable to the Rpi and plug it into a power socket. This will make your Rpi boot;
6. Get yourself a nice cup of coffee, because the booting will take up to 20 minutes. Just let the Rpi do its thing. You know it is ready when you see either: 

	* a new Wifi network called OEHU Setup, or, 
	* when Wifi is not available on the Rpi and you use ethernet instead: you see that your Rpi is connected on this website: <http://oehu.org/setup>;

## <a name="part3"></a> Part 3: Configure & Go!
If wifi is available on your Rpi, your Rpi is turned into a hotspot by now and is sending out a Wifi network called: OEHU Setup. Then start with step 1, otherwise go straight to [step 5] (#part3_step5).

**Step 1**: change the Wifi connection of your laptop to the network: OEHU Setup;

**Step 2**: browse to <http://oehu.local>;

**Step 3**: Here you need to select your own (home) Wifi network. Make sure the Rpi and your laptop are on the same network. Click the Submit button.  
**BE AWARE**: enter the credentials right the first time, otherwise the Rpi will freeze and you need to start all over again.

**Step 4**: change the Wifi connection of your laptop back to your own (home) Wifi network;

<a name="part3_step5"></a> **Step 5**: To configure your Rpi go to <http://oehu.org/setup>;

**Step 6**: Fill in your location and give in the accuracy in meter that you want the viewer to show your location on the map. Click Next. 
NB. It is possible to choose anonymity instead of giving in your precise location. Check the box if you want to stay anonymous.

**Step 7**: Specify the type of building where the smart meter is located. Also specify the amount of occupants of the building. Click Next. 

**Step 8**: Choose your username and password that gives you access to your dashboard on the OEHU website. Make sure you save the passfrase, username and password by downloading the file and storing this in a save location. Normally, the download of the pdf with this information starts automatically. Click Next. 

**Step 9**: If you entered an username and password in step 4, you will now enter your dashboard on the OEHU website: <http://oehu.org/dashboard>  
Typically, after 10 seconds the first information of your smart meter should be visible in the dashboard.

