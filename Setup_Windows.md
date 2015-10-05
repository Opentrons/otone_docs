#OT.One Set-up *Windows 7*

### Plug things in

First thing to do is plug everything in correctly. 

1. Plug the ethernet cable from your computer into the RPi.
2. The RPi to the Smoothieboard with the short USB-A to USB-B.
3. Smoothieboard to 12V powersupply in wall socket. This is the round barrel jack and larger power brick.  
4. Hit the on button to send power to the motors.

![Chords Plugged In Image] (img/Setup_Mac/Plugged_1.jpg)

Finnally, connect the RPi to 5V power supply in wall socket. This is the micro-USB like an Android phone charger, and goes in the top of the RPi in the slit in the aluminum box. 

_When you plug in the RPi, the robot will begin to boot up,_ and the motors will home at the end of boot (approx 3 minutes). Be ready for the motors to move before plugging in the RPi!

### Configure Network Settings

Required: Windows 7 PC with an ethernet port (or USB to ethernet dongle)

1) Using an administrators account, open the "RUN" window, enter "REGEDIT" and click OK.  On the "User Account Control" confirmation box, click the "Yes" button.

![REGEDIT] (img/Setup_Windows/REGEDIT.JPG)

2) On the open "Registery Editor" window, on the left pane, go to "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\SharedAccess\Parameters"

3) In the listed parameters in the right pane, double click "ScopeAddress" to open the "Edit String" box and change the "Value data" to "10.10.1.1" and then click OK.

![ScopeAddress] (img/Setup_Windows/ScopeAddress.JPG)

4) Next, double clck "StandaloneDHCPAddress" to open the "edit String" box and change the "Value data" to "10.10.1.1" and then click OK.

![StandaloneDHCP] (img/Setup_Windows/StandaloneDHCP.JPG)

5) Close the Registry Editor window.

6) Restart the computer to activate the new settings.

7) Open "Control Panel"/"Network and Sharing Center" - you should see both a wireless connection and unidentified network.

8) In "Network and Sharing Center", click on "Change adapter settings" on the left side.

9) Right click on "Local Area Connection" and then click on "Properties".

10) Click on "Internet Protocol Version 4 (TCP/IPv4)" entry in the list, and then click on the "Properties" button underneath.

11) Select the "Use the following IP Address" radio button and enter "10.10.1.1." in the form.  Subent mask should be 255.255.255.0.

![LocalAreaConnectionToSubnetMask] (img/Setup_Windows/LocalAreaConnectionToSubnetMask.JPG)

12) Click OK to close the "Properties" window.

13) Next, left click on "Wireles network connection", then click "Properties".

14) Select the "Sharing" tab and click the checkbox labeled "Allow other users to connect through their computer's Internet connection".  Click OK to close dialog boxes.

![WirelessConnections] (img/Setup_Windows/WirelessConnections.JPG)

15) Click OK and then click Close.  The "Network and Sharing Center" window can then be closed.

16) Open browser and navigate to http://10.10.1.2.  The page may need to be refreshed.

17) Robot GUI willa ppear in browser and display a green status message in upper right hand corner ("Browser Connected to Server") and the user can move the robot head using the controls on the GUI.

18) Click on the "Config" tab.  The green "online" indicator under the "Connect" button should be visible.

Once you have all that, its time to move the robot! Go to the next step: [Jogging Controls] (Jogging_Controls.md). 

