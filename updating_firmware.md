#Updating Firmware

The motorcontroller inside all Opentrons liquid handlers (called Smoothieboard or just Smoothie) will need it's firmware updated if you are planning to use the Opentrons API and accompanying 2.0 app.

The process is simple, and can be done from your computer in under a minute.

###Download

Download the zipped files from [here](https://github.com/OpenTrons/smoothie-config/archive/1.2.0.zip). After downloading, unpack the zip file to view its contents.

###Select Your Opentrons Model

Opentrons [come in three models](https://opentrons.com/robots), the Standard, Pro, and Hood. Each model requires a unique "config" file to go along with it.

Inside the downloaded folder, you'll find another folder called "config", which holds a config file for each model. Select your 



1. Copy `firmware.bin` into the Smoothie folder (found on the Smoothie's SD card). This will overwrite the `firmware.cur` upon restart.
2. Restart the Smoothie.
