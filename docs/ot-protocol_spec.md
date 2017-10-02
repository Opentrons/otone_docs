**OT.One - Mix.Bio Protocol Schema Specification**

**Mix.Bio protocol version 1.0**

The OT.One Liquid Transfer Robot utilizes a JSON file as input in order to execute a specific liquid transfer protocol.  The specific steps and parameters comprising the protocol are specified in name/value fields within the JSON file.  This document provides an annotated example protocol file to aid the user in understanding and construction a protocol file.  At the highest level of the hierarchical file structure, there are 5 sections:  info, deck, head, ingredients, instructions.

The info section provides fields for the user to specify information about the protocol run that the JSON file represents.

The deck section contains fields specifying the modules located on the robot deck.

The head section contains fields specifying the pipettes or other tools located on the robot’s movable head.

The ingredients section provides fields for specifying the reagents and samples being used in the assay and their starting volumes.

The instructions section contains the steps and transfer details of the actual protocol being run on the robot.

The protocol example used here is for illustration purposes and the values do not correspond to a real protocol.

**Info**

“info” {

    “name” : “the name of the protocol”,

    “description” : “a description of the protocol”,

    “run-notes” : “additional information further specifying details of the protocol run”

    “create-date : “creation date of the protocol”,

    “version” : “version designation of the protocol”

}

1. User informational fields for the protocol.
    1. All fields are optional
    2. Default values are values in mix.bio database.  Values can be edited in protocol editor.
    3. Creation date is processed as a string, so all international formats are allowed.  
    4. Version format is user defined and processed as a string

**Deck**

"deck" : {

    "p200-rack" : {

      "labware" : "tiprack-200ul", 

      "slot": "A1"

    },

    "trough": {

      "labware": "trough-12row", 

      "slot": "C2"

    },

    "plate-1": {

      "labware": "96-flat", 

      "slot": "C1"

    },

    "plate-2": {

      "labware": "96-flat", 

      "slot": "D1"

    },

    "plate-3": {

      "labware": "96-flat", 

      "slot": "D2"

    },

    "trash": {

      "labware": "point", 

      "slot": "B2"

    }

  },

1. List each piece of labware on the deck
    1. This includes tip racks, well plates, any tubes, or whatever the robot needs to know about
    2. Specify the location of each piece of lab ware on the deck by the slot identifier
    3. Slot identifier corresponds to the 3 x 5 layout of the deck in format similar to wells in a plate and runs from A1 - E3

2. Each labware is given a custom name, and then defined by a specific labware type
    1. The dimensions of each labware type must be defined inside containers.json
    2. If a new piece of labware is being used, it must be added to containers.json

**Head**

"head" : {

    "p200" : {

      "tool" : "pipette",

      "tip-racks" : [

        {

          "container" : "p200-rack"

        }

      ],

      "trash-container" : {

        "container" : "trash"

      },

      "multi-channel" : true,

      "axis" : "a",

      "volume" : 250,

      "down-plunger-speed" : 300,

      "up-plunger-speed" : 500,

      "tip-plunge" : 8,

      "extra-pull-volume" : 20,

      "extra-pull-delay" : 200,

      "distribute-percentage" : 0.1,

      "points" : [

        {

          "f1" : 10,

          "f2" : 6

        },

        {

          "f1" : 25,

          "f2" : 23

        },

        {

          "f1" : 50,

          "f2" : 49

        },

        {

          "f1" : 200,

          "f2" : 200

        }

      ]

    }

  },

1. Define the 1 or 2 pipettes being used in this protocol
2. Each pipette is given a custom name, and then has a set of parameters
    1. tool
        1. right now, this is always pipette

    2. axis
        1. what axis is it on the robot (a or b)

    3. tip-racks
        1. an array of tip racks that this pipette will access
            1. These racks must be defined up in the Deck section
            2. it’s an array so it can be multiple racks

    4. trash-container
        1. the spot where this pipette will drop it’s dirty tips
        2. it must be defined up in the Deck section

    5. multi-channel
        1. true or false
        2. defines if it’s at 1 tip or 8 tip pipette

    6. volume
        1. the total volume of the pipette, in microliters (uL)

    7. tip-plunge
        1. how many millimeters the pipette must push down to successfully pick up a tip
        2. this depends greatly on the tip being used

    8. distribute-percentage
        1. A percentage of this pipette’s total volume (0.0 to 1.0)
        2. when running a distribute command, the pipette can suck up extra liquid to help accuracy
        3. This pipette will add whatever volume is specified here, by adding this percentage of it’s total volume
            1. Example: if this pipette is 200uL, and distribute-percentage is 0.1, then it will suck up an extra 20uL for each distribute command

    9. down-plunger-speed
        1. how fast will the axis move when going down (mm/minute)

    10. up-plunger-speed
        1. how fast will the axis move when going up (mm/minute)

    11. extra-pull-volume
        1. how many uL this pipette will add if an extra-pull is called in the Instructions section

    12. extra-pull-delay
        1. how many milliseconds this pipette will pause if an extra-pull is called in the Instructions section

    13. points
        1. These are special values, used to change it’s linear plunger movements to a custom curve
        2. it’s an array of uL amounts, where f1 is what was asked for, and f2 is what the pipette actually did when running linearly
            1. we find that when you ask for smaller volumes, the pipette become less accurate in the negative direction
            2. for example, on a p200, we found that if we asked it to move 10uL on a linear scale, it actually moved only 6uL
                1. so in this case, f1 would be 10, and f2 would be 6

**Ingredients**

  "ingredients" : {

    "ReagentA": 

    [

      {

        "container": "Reagents-1",

        "location": "A3",

        "volume": 25000

      }

    ],

    "ReagentB": 

    [

      {

        "container": "Reagents-1",

        "location": "A1",

        "volume": 7000

      }

    ],

    "Standard1": 

    [

      {

        "container": "Standards",

        "location": "A1",

        "volume": 125

      }

    ]   

  },

1. List the positions and uL amounts of each all liquids at the moment when the job starts
2. This is currently only used for doing liquid-tracking, so this section can be empty if liquid-tracking is never used
    1. But for future tracking applications, this field will be necessary

**Instructions**

  "instructions": [

    {

      "tool": "p200",

      "groups": [

        {

          "transfer": [

            {

              "from": {

                "container": "trough",

                "location": "A1",

                "tip-offset": -2,

                "delay" : 2000,

                "touch-tip" : true

              },

              "to": {

                "container": "plate-1",

                "location": "A1",

                "touch-tip" : true

              },

              "volume": 100,

              "blowout" : true,

              "extra-pull" : true

            }

          ]

        },

        {

          "distribute":

          {

            "from": {

              "container": "trough",

              "location": "A1"

            },

            "to": [

              {

                "container": "plate-2",

                "location": "A2",

                "volume" : 20,

                "touch-tip" : true

              },

              {

                "container": "plate-2",

                "location": "A3",

                "volume" : 30,

                "touch-tip" : true

              },

              {

                "container": "plate-2",

                "location": "A4",

                "volume" : 100,

                "touch-tip" : true

              }

            ],

            "blowout" : true

          }

        },

        {

          "consolidate":

          {

            "from": [

              {

                "container": "plate-2",

                "location": "A2",

                "volume" : 20,

                "touch-tip" : true

              },

              {

                "container": "plate-2",

                "location": "A3",

                "volume" : 30,

                "touch-tip" : true

              },

              {

                "container": "plate-2",

                "location": "A4",

                "volume" : 100,

                "touch-tip" : true

              }

            ],

            "to": {

              "container": "plate-3",

              "location": "A5",

              "touch-tip" : true

            },

            "blowout" : true

          }

        },

        {

          "mix": [

            {

              "container": "plate-1",

              "location": "A5",

              "volume" : 100,

              "repetitions" : 5,

              "blowout" : true,

              "liquid-tracking" : true

            }

          ]

        }

      ]

    }

  ]

1. An array of individual instructions to be run sequentially
    1. This section is what was carried over from Auto-Protocol, and shares many of it's design decisions

2. One instruction specifies a tool and groups
    1. tool must point to one of the pipettes, defined in the head section
    2. groups is an array individual groups
        1. a group can specify one (and only one) command type
        2. a group can also be thought of as the lifespan of a tip
            1. at the beginning of a new group, the specified pipette will get a new tip(s) from one of it’s tip-racks
            2. once the group is finished, the specified pipette will drop the tips in it’s trash-container

        3. commands include transfer, distribute, consolidate, and mix
            1. transfer
                1. move specified volume from one location to another
                2. transfers are listed as an array, so you can have multiple transfer commands using the same tip

            2. distribute
                1. move specified volumes from one location to many locations
                2. the to locations are listed as an array, so you can have any number of destination locations with different volumes

            3. consolidate
                1. move specified volumes from many locations to one location
                2. the from locations are listed as an array, so you can have any number of source locations with different volumes

            4. mix
                1. suck up and immediately spit out at one location, thus mixing the solution there
                2. mixes are listed as an array, so you can have multiple mix commands using the same tip

        4. Parameters
            1. volume
                1. how many uL to pick up or spit out

            2. container
                1. what container the command is referencing (defined up in the Deck section)

            3. location
                1. what specific location (well) on this container we’re acting upon
                    1. locations are defined inside containers.json file

            4. tip-offset (optional)
                1. adjust the destination height of this pipette in millimeters (along the Z axis)
                2. for example, if tip-offset is 2, then the pipette will arrive 2 millimeters higher (negative will take it lower)
                    1. Note: the containers.json defines each location’s depth, so if the tip-offset value is negative and goes too deep, the software will constrain it and prevent the tip from hitting the bottom of the location

            5. delay (optional)
                1. how many milliseconds to pause after acting on a liquid
                2. this is helpful for letting the liquid and air pressure settle in the tip

            6. touch-tip (optional)
                1. true or false
                2. after acting on a location, if touch-tip is true, the pipette will touch the tip against the sides of this location
                3. this is useful for getting rid of extra drops hanging off the tip

            7. blowout (optional)
                1. true or false
                2. after dispensing into a location, should the pipette do a blowout with plunger?

            8. extra-pull (optional)
                1. true or false
                2. should the pipette pull up extra volume when sucking up at the from location?
                3. the amount that it will pull up is specified in the Head section

            9. liquid-tracking (optional)
                1. true or false
                2. when acting upon a location, the tip will move by default to the bottom or top of a location
                3. however, if liquid-tracking is true, the tip will move to the current height of the liquid level inside that location
                    1. in order for this to be accurate, the starting positions of each liquid should be defined inside the Ingredients section
                    2. the algorithm will adjust throughout the execution to account for changing liquid levels inside all locations