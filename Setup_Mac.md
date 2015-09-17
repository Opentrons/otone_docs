#OT.One Set-up _Mac OSX_

### Connect Everything

First thing to do is plug everything in correctly. 

1. The RPi to the Smoothieboard with the short USB-A to USB-B.

PICTURE TBD!!!!

2. Smoothieboard to 12V powersupply in wall socket. This is the round barrel jack and larger power brick.  Hit the on button to send power to the motors.

PICTURE TBD!!!!

3. RPi to 5V power supply in wall socket. This is the micro-USB like an Android phone charger. When you plug in the RPi, it will begin to boot up, and the motors will home at the end of boot (approx 3 minutes). Be ready for the motors to move before plugging in the RPi!

PICTURE TBD!!!!

4. Plug the ethernet cable into your computer and the RPi. 

PICTURE TBD!!!!

### Configure Network Settings

The RPi serves the interface for running the robot to your computer over the ethernet cable and to your web browser. You need to manually set some network settings the first time you do this.

*Note: you will not be able to see the interface until the RPi has completed boot-up, which you can tell because the robot runs a home sequence.*

##### 1- Go to System Preferences and click on Networking. 

![Seystem Preferences Screenshot] (img/Setup_Mac/Networking_1.jpg)

##### 2- Select the Ethernet connection that is going to the RPi. Change the Configure IPv4 drop-down menue to "Using DHCP with manual address." Set the address to 10.10.1.1. Then click 'Apply.' 

![Network Settings Screenshot] (img/Setup_Mac/Networking_2.jpg)

##### 3- Open a browser, or a new tab in the browser you already have open (Chrome works well). Type 10.10.1.2 into the address bar and press 'enter.' 

![Browser IP Address Screenshot] (img/Setup_Mac/Networking_3.png)

##### 4- Refresh the browser and you should see the OT.One Interface! Make sure it is green and says 'Browser Connected to Server.' 

![OT.One Interface Screenshot] (img/Setup_Mac/Networking_4.png)




 






