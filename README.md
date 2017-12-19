# jewelbots

Hello! I'm so happy to share with you all the fun I have making up programs for my jewelbot \(programmable friendlship bracelet\).

Jewelbots can actually be used right out of the box without ever programming them at all. You might need to charge it up first, but you don't need to program it to use it!

## How to pair

Many jewelbots can be assigned to the same friendship group color, however, jewelbots can only be paired two at a time. In order to pair, first make sure both jewelbots are unplugged, turned on, and within 60 centimeters of each other. Next, hold down the button on both jewelbots for 2 full seconds \(counting 1 Mississippi, 2 Mississippi.\) One jewelbot will light up all white, the other will cycle through colors one at a time. You pick the friendship group color by pressing the button on the cycling jewelbot.

## How to code

You'll need to download the Arduino IDE \(it's free\) onto a Windows, Apple, or Linux computer \(Chromebooks don't work with jewelbots yet at this time. Hopefully someday we can figure out a way to do this on chromebooks!\) After you've got the Arduino IDE started up, you'll need to add the jewelbots boards by copying and pasting the following block of code into the Arduino's "Additional Boards Manager URLS" text box located in the Preferences. Get to Preferences by looking under the File menu in the IDE.

`https://jewelbots.github.io/arduino-library/package_jewelbots_index.json,https://jewelbots.github.io/arduino-firmware/package_jewelbots_firmware_index.json,https://jewelbots.github.io/arduino-friendship/package_jewelbots_friendship_index.json`

The first thing to know is that jewelbots have two different coding boards: Friendship Coding Mode and Solo Coding Mode. You can switch between the two boads by looking under the Tools menu in the IDE and selecting Boards. Some functions can be used in both solo mode and friendship mode, but not all of them. I'm not sure how many of the functions are reusable between both boards. Maybe that is something you can figure out!

In order to start a new project, select New from the File menu on the IDE. Arduino will choose a default name for your file based on the date, however you can change this if you wish when you save the file. It's a good idea to go ahead and save the file before you begin working, then save again often as you code.

Uploading code to your jewelbot is next! You plug your jewelbot into the computer. Make sure the USB port is selected in the IDE as the Port under the Tools menu. If you're on a Linux computer and your code repeatedly won't upload, you may need to give your computer permission to write out to the USB ports by typing `sudo adduser $USER dialout` into the terminal.

Before hitting that upload button on the IDE make sure your jewelbot is in coding mode by holding down on the jewelbot's button for 2 seconds, letting up and waiting for the blue lights to fade. The hit the upload button!

