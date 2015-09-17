#Choose and Edit a Protocol

The OT.One runs protocols based on OT-Protocol JSON documents like this one: [protocol.json] (docs/protocol.json)

This is an OT-Protocol JSON document explained: [OT-Protocol JSON Explained] (docs/ot-protocol_spec.md)

([JSON] (http://json.org/) is just a way of structuring textual data hierarchically, and OT-Protocol is just JSON used in a way specific to liquid handling robots)

##### 1- Download OT-Protocol Document from Mix.Bio

Each protocol document specifies the which pipette(s) are on the robot head, what labware is on the robot deck, and then what instructions that the robot follows for a given run. Find the OT-Protocol document that seems to be closes to what you are looking for in the [Mix.Bio Protocol Library] (https//:mix.bio/browse) and download it.

!-- Screenshot of choosing a Mix.Bio library protocol and downloading it

##### 2- Edit OT-Protocol 

You can edit the document you downloaded from the Protocol Library with the [Protocol Editor] (https//:editor.mix.bio). Just browse for your downloaded OT-Protocol document, or drag the JSON file directly in as shown here:

![Drag into Editor Screengrab] (img/Choose_Protocol/Editor_1.jpg)

When it has processed, it should look something like this:

![Populated Editor Screengrab] (img/Choose_Protocol/Editor_2.png)

Now you can start editing your protocol!

*Note:* Just click a field and type in your new value to change it. The value is saved when you click back out of that field (click on something neutral, not a different field). 

Below the Info section of the protocol is highlighted. It specifies 'meta' information about the document. 

![Info Section of Editor] (img/Choose_Protocol/Editor_Info.jpg)

*Head Section* 

The head section specifies what pipettes are attached to the robot, in which position, and what their attributes are. You can do things here like change the rate the robot moves the plunger (slow it down for more viscous material for example) and define which tip-rack & trash location each pipette should use. 

![Head Section of Editor] (img/Choose_Protocol/Editor_Head.jpg)

*Deck Section*

The deck section is where you declair all the labware you're using in a given run. It always needs to include at least one tip rack for the pipette you are using, and one trash for the pipette to eject tips in. Other than that, you can add things like 96 well plates and microfuge tubes!

The labware definitions specify the exact physical demensions of each piece of labware we have added to the library. This means that the machine knows where every well in a 96-well plate is after you tell it just one position, for example. 

_Note: When adding items to the deck, you can type whatever you want in the 'Name:' field (something descriptive like 'Source Plate' or 'Reagent Trough' is generally encouraged), but the value you enter in the 'Labware:' field must correspond exactly to a value in the Labware Library._

This is a list of what you can enter into the 'Labware:' field: [OpenTrons Labware Library 1.0] (Labware_Library.md)









##### Next Step: [Calibrate and Run] (Calibrate_Run.md)
