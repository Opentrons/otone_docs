#Updating Firmware

The motorcontroller inside all Opentrons liquid handlers (called Smoothieboard or just Smoothie) will need it's firmware updated if you are planning to use the Opentrons API and accompanying 2.0 app. The process is simple, and can be done from your computer in under a minute.

To summarize, there are two files on your Smoothie that must be replaced; `FIRMWARE.CUR` and `config`. 

##Download

Download the zipped files from [here](https://github.com/OpenTrons/smoothie-config/archive/1.2.0.zip). After downloading, unpack the zip file to view its contents.

##Open the Smoothie's Drive

Power on and plug in your Opentrons liquid handler, and make sure you do not have the app open. You will notice the Smoothieboard shows up on the computer as a Mass Storage Device, like an external hard drive or flash drive.

![Select Config File] (img/Update-Firmware/firmware_files.png)

Open the Smoothie's storage device to see it's `FIRMWARE.CUR` and `config` files. There might be other files there, but the two you need to worry about are `FIRMWARE.CUR` and `config`, because these are what we will be replacing.

##Copy Over `firmware.bin`

From the folder you downloaded from GitHub, 

![Select Config File] (img/Update-Firmware/SelectFirmwareBin.png)

##Select Your Opentrons Model

Opentrons [come in three models](https://opentrons.com/robots), the Standard, Pro, and Hood. Each model requires a unique "config" file to go along with it.

![Select Config File] (img/Update-Firmware/SelectConfigFile.png)

Inside the downloaded folder, you'll find another folder called "config", which holds a config file for each model. Select your 



1. Copy `firmware.bin` into the Smoothie folder (found on the Smoothie's SD card). This will overwrite the `firmware.cur` upon restart.
2. Restart the Smoothie.
