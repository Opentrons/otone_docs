#Calibrate and Run a Protocol

Before you can run your protocol, you need to tell the robot where one position is for each piece of labware on the deck. You do this by jogging the machine to that position and saving it. 

#### 1- Drag OT-Protocol document into interface. 

You've chosen and edited an OT-Protocol now, so drag that into the interface so we can run it. 

![Drag OT-Protocol document here] (img/Calibrate_Run/Calibrate_1.jpg)

Once you drag in a protocol, all the labware it uses will pop up here

![Deck Positions] (img/Calibrate_Run/Calibrate_2.jpg)

When there is no position previously saved for a piece of labware, the only button available will be 'Save.' After you have jogged the robot to a position and hit 'Save,' there will also be a 'Move To' button. Pressing 'Move To' will instruct the robot to go to the saved position for that labware. 

You can only hit buttons when you have the correct labware highlighted. This is to prevent you from accidently saving the wrong position. 

**Saving Well Positions**

Generally, you want to calibrate a well position to the exact top of a well (remember to have a tip on the robot). A good rule of thumb is if there were a piece of paper sitting on the well, the tip would be barely touching it. 

When picking up and dispensing liquid, the robot defaults to the bottom of the well as defined by its Labware Library definition. So, telling it the exact top will insure that the robot goes all the way to the bottom. Remember, if you dont want the robot to go all the way to the bottom, you can use the tip-offset value in the OT-Protocol document, or just 'cheat' and calibrate the position higher than the actual well. As a rule of thumb you'll run a protocol with just water for the first time so you'll be able to tweak the positions and get them right.

