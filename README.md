# Jewelbots Curriculum
---

## Overview
---
Hello! I'm so happy to share with you all the fun I have making up programs for my Jewelbot \(programmable friendship bracelet\).

## Prep Work
---
While we wait for everyone to arrive, we have some fun activities for you to work on. Don't worry, we'll do the project part as a group!

1. Parents: Please take our anonymous [survey](https://docs.google.com/forms/d/e/1FAIpQLSdKlS1CXl3lq1FuCNgFuoBucqZhq4f7Yr2V67PMp0IiuhfuBg/viewform).
2. Open your Jewelbot and plug it in to the USB port on your computer to start charging it up.
3. Install the Arduino IDE (stands for Integrated Development Environment.)[Arduino Software](https://www.arduino.cc/en/Main/Software).
4. Visit the Instructions section of the Jewelbots website and click on "Code Setup" then click on "Add Boards" and start working your way through the instructions [Jewelbots](https://jewelbots.com/pages/support).

## Project Setup
---
There are two types of programs for Jewelbots. Solo Coding uses the one input (the magic button) and two outputs (the led lights and the buzzer). Friendship Coding uses two inputs (the magic button and Bluetooth) and three outputs (the led lights, the buzzer, and Bluetooth). We will write one solo coding program and one friendship coding program today.

5. Start by selecting File > New in your Arduino IDE. This will open a new window, feel free to make the window larger so it's easier to use.
6. Next choose File > Save As in your Arduino IDE and choose a name and location for your program file.
7. Every time you create a new file in he Arduino IDE it will have a "setup" and "loop" function already in it. This is because most microcontrollers (especially Arduino brand) use programs with "setup" and "loop" functions. The "setup" function runs each time the the device is powered on, then the "loop" function runs continuously while the device is on. Jewelbots are slightly different. They come wtih libraries that allow us to write functions specifically for the Jewelbots inputs (magic button and Bluetooth) and outputs (leds, buzzer, and Bluetooth). So for this class we won't be using "setup" and "loop". You can delete them or leave them blank.

## Instructions to solo code your Jewelbot
---
The first program we are going to write is a Timer that you set by pressing the magic button on the Jewelbot. After we code, compile and upload our Timer program to the Jewelbot, you will be able to press the magic button X number of times to set the timer for X number of minutes.

8. First we declare our variables. Type the following code at the top of the project file.
```
Buzzer buzz;
LED led;
Timer timer;
int x = 0;
```
Buzzer and LED are variables that represent the outputs on your Jewelbot. Timer is a variable that we will use to count the passing microseconds. The final variable is called "x". We define x as an integer by giving it the prefix "int". We set x to have the value of 0 by typing `x = 0`. In programming, the symbol = does not mean equals, it means "has the value of".

9. Next we write our first function! It will have the name button_press. It will have the return type of void which we indicate by giving it the prefix void. This function will also take no arguments which we will indicate by putting the word void inside parenthesis before the opening braces of the function body.
```
void button_press(void){

}
```
10. Inside the braces of the function body, add this line of code. `x = x+1;` Remembering that the = sign means "has the value of" in programming, read the line of code out loud. Can you guess what it is doing? Based on the name of this function, can you describe what is going to happen every time the button is pressed? Your code should now look like this.
```
Buzzer buzz;
LED led;
Timer timer;
int x = 0;

void button_press(void){
  x = x+1;
}
```

11. Next we will write another function. This one has the name button_press_long. It also takes (void) arguments and has a return type of void. See if you can guess how to type that. Don't be shy about trying something. We will provide the correct code in the next step.

12. Inside the braces of the function body we need to add some code that tells the Jewelbot what to do when the button is pressed for a long press. The short button presses set the timer, and the long button press starts the timer. Several steps need to happen inside the button_press_long function. The first thing we add to our button_press_long are some variables to use as counters.
```
void button_press_long(void) {
  int i = 0;
  int j = 0;
```
13. The next thing we are adding to our button_press_long function is a loop telling the leds to flash x number of times. Add the following to your button_press_long function.
```
for(int i = 1; i <= x; i++){
    led.flash_all(BLUE,1000);
    timer.pause(500);
}
```
This is a "for loop". A "for loop" is a conditional that repeats some code according to the conditions you give it. It is super useful for writing code that you want to repeat many times. The syntax of a "for loop" is that it starts with the word "for". Next the conditions are insude parenthesis. The conditions always go in this order (start, stop, step). In our code, the conditions are `(int i = 1; i <= x; i++)`. This statement tells the Jewelbot to repeat the code inside the "for loop" on the following conditions: _start_ with an integer type of variable called i that has the value of 1, _stop_ when i no longer has a value of equal to or less than x, _step_ each time through the loop by adding 1 to i for every repeat. Don't understand it all yet? Not to worry, this is the sort of thing that's easiest to learn by doing. So let's move on! Your code should now look like this.
```
Buzzer buzz;
LED led;
Timer timer;
int x = 0;

void setup() {
}

void loop() {
}

void button_press(void){
  x = x+1;
}

void button_press_long(void) {
  int i = 0;
  int j = 0;

  for(int i = 1; i <= x; i++){
    led.flash_all(BLUE,1000);
    timer.pause(500);
  }

  for(int j = 1; j <= x*6; j++){
    timer.pause(10000);
    if (j % 6 == 0) {
      led.flash_all(RED, 1000);
    }
  }
}
```
Now our button_press_long function has a "for loop" that will flash all the leds blue x number of times, with a half second pause between flashes.

14. The last thing we need to code our button_press_long function to do is to reset x to 0 and buzz to let us know the time is up. The code for that is
```x = 0;
buzz.short_buzz();
```

15. Now your code is ready to test out. It should look like this...
```
Buzzer buzz;
LED led;
Timer timer;
int x = 0;

void setup() {
}

void loop() {
}

void button_press(void){
  x = x+1;
}

void button_press_long(void) {
  int i = 0;
  int j = 0; // i and j are local variables with scope only inside this function.
  for(int i = 1; i <= x; i++){
    led.flash_all(BLUE,1000);
    timer.pause(500);
  }

  x = 0;
  buzz.short_buzz();
}
```
16. 

### How to code

You'll need to download the Arduino IDE \(it's free\) onto a Windows, Apple, or Linux computer \(Chromebooks don't work with Jewelbots yet at this time. Hopefully someday we can figure out a way to do this on chromebooks!\) After you've got the Arduino IDE started up, you'll need to add the Jewelbots boards by copying and pasting the following block of code into the Arduino's "Additional Boards Manager URLS" text box located in the Preferences. Get to Preferences by looking under the File menu in the IDE.

`https://jewelbots.github.io/arduino-library/package_jewelbots_index.json,https://jewelbots.github.io/arduino-firmware/package_jewelbots_firmware_index.json,https://jewelbots.github.io/arduino-friendship/package_jewelbots_friendship_index.json`

The first thing to know is that Jewelbots have two different coding boards: Friendship Coding Mode and Solo Coding Mode. You can switch between the two boads by looking under the Tools menu in the IDE and selecting Boards. Some functions can be used in both solo mode and friendship mode, but not all of them. I'm not sure how many of the functions are reusable between both boards. Maybe that is something you can figure out!

In order to start a new project, select New from the File menu on the IDE. Arduino will choose a default name for your file based on the date, however you can change this if you wish when you save the file. It's a good idea to go ahead and save the file before you begin working, then save again often as you code.

Uploading code to your Jewelbot is next! You plug your jewelbot into the computer. Make sure the USB port is selected in the IDE as the Port under the Tools menu. If you're on a Linux computer and your code repeatedly won't upload, you may need to give your computer permission to write out to the USB ports by typing `sudo adduser $USER dialout` into the terminal.

Before hitting that upload button on the IDE make sure your jewelbot is in coding mode by holding down on the Jewelbot's button for 2 seconds, letting up and waiting for the blue lights to fade. The hit the upload button!

### How to pair
Jewelbots can actually be used right out of the box without ever programming them at all. You might need to charge it up first, but you don't need to program it to use it! Many Jewelbots can be assigned to the same friendship group color, however, Jewelbots can only be paired two at a time. In order to pair, first make sure both Jewelbots are unplugged, turned on, and within 60 centimeters of each other. Next, hold down the button on both Jewelbots for 2 full seconds \(counting 1 Mississippi, 2 Mississippi.\) One Jewelbot will light up all white, the other will cycle through colors one at a time. You pick the friendship group color by pressing the button on the cycling Jewelbot.

## Homework
---
Did you love working with code? If you want to learn more on your own, we have suggestions for you.

* Come to one of our other Coding & Cupcakes events [Eventbrite](https://www.eventbrite.com/o/coding-amp-cupcakes-kansas-city-16053804463).
* Come to a Coder Dojo event [Coder Dojo](http://coderdojokc.com/).
* Create an account on [Codecademy] (http://www.codecademy.com/) and try out another microcontroller programming language like Python or Javascript [Programming](https://www.codecademy.com/catalog/subject/programming).
* Visit the Jewelbots community forums (they are well moderated to be safe for kids) and watch their videos on advanced programming for your Jewelbot [Jewelbots Community Forums](http://alpha.jewelbots.com/).
* Visit Tinkercad Learn and click on "Circuits" [Tinkercad Learn](https://www.tinkercad.com/learn/).
* Check out the Arduino project hub for ideas about what you can make with your new skills! [Arduino Project Hub](https://create.arduino.cc/projecthub).
