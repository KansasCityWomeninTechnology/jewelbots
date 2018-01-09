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
3. You'll need to download the Arduino IDE \(it's free\) onto a Windows, Apple, or Linux computer \(Chromebooks don't work with Jewelbots yet at this time. Hopefully someday we can figure out a way to do this on chromebooks!\) [Install the Arduino IDE (stands for Integrated Development Environment.)](https://www.arduino.cc/en/Main/Software).
4. After you've got the Arduino IDE started up, you'll need to add the Jewelbots boards by copying and pasting the following block of code into the Arduino's "Additional Boards Manager URLS" text box located in the Preferences. Get to Preferences by looking under the File menu in the IDE.

`https://jewelbots.github.io/arduino-library/package_jewelbots_index.json,https://jewelbots.github.io/arduino-firmware/package_jewelbots_firmware_index.json,https://jewelbots.github.io/arduino-friendship/package_jewelbots_friendship_index.json`

Detailed instructions on how to do this can be found on the [Jewelbots website](https://jewelbots.com/pages/support) if you lick on "Code Setup" then click on "Add Boards".

## Project Setup
---
There are two types of programs for Jewelbots. Solo Coding uses the one input (the magic button) and two outputs (the led lights and the buzzer). Friendship Coding uses two inputs (the magic button and Bluetooth) and three outputs (the led lights, the buzzer, and Bluetooth). We will write one solo coding program and one friendship coding program today.

5. Start by selecting File > New in your Arduino IDE. This will open a new window, feel free to make the window larger so it's easier to use.
6. Next choose File > Save As in your Arduino IDE and choose a name and location for your program file.
7. Every time you create a new file in he Arduino IDE it will have a "setup" and "loop" function already in it. This is because most microcontrollers (especially Arduino brand) use programs with "setup" and "loop" functions. The "setup" function runs each time the the device is powered on, then the "loop" function runs continuously while the device is on. Jewelbots come wtih libraries that allow us to write functions specifically for the Jewelbots inputs (magic button and Bluetooth) and outputs (leds, buzzer, and Bluetooth). The "setup" and "loop" functions will be left blank, but we need to keep them in our code to prevent compile errors.

## Instructions to solo code your Jewelbot
---
The first program we are going to write is a Timer that you set by pressing the magic button on the Jewelbot. After we code, compile and upload our Timer program to the Jewelbot, you will be able to press the magic button X number of times to set the timer for X number of minutes.

8. First we declare our variables. Type the following code at the top of the project file.
```
Buzzer buzz;
LED led;
Timer timer;
int x = 0;

void setup() {
}

void loop() {
}
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

void setup() {
}

void loop() {
}

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
}
```
Now our button_press_long function has a "for loop" that will flash all the leds blue x number of times, with a half second pause between flashes. If you want to change from BLUE to another color, your choices of preset colors are: RED, GREEN, BLUE, YELLOW, MAGENTA, CYAN, or WHITE.

14. The last thing we need to code our button_press_long function to do is to reset x to 0 and buzz to let us know the time is up. The code for that is
```x = 0;
buzz.short_buzz();
```

15. One final thing is that we're going to add a function that tells our Jewelbot to flash all the leds red once per minute. A minute is 60,000 miliseconds but the pause method can't handle numbers that big so we're going to do increments of 10000 times 6 and we'll have the leds flash red every 60 seconds like this. If you want to change from RED to another color, your choices of preset colors are: RED, GREEN, BLUE, YELLOW, MAGENTA, CYAN, or WHITE.
```
for(int j = 1; j <= x*6; j++){
    timer.pause(10000);
    if (j % 6 == 0) {
      led.flash_all(RED, 1000);
}
```

16. One final thing. Let's add an led animation and tell it to play when the timer goes off. This will require two lines of code. Add this code `Animation animation;` at the top of your file with the other variable declarations. Add this code `animation.rainbows();` on the next line after the buzz command.

Now your code is ready to test out. It should look like this...
```
Animation animation;
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

  x = 0;
  buzz.short_buzz();
  animation.rainbows();
}
```
17. Make sure to save your work by choosing File > Save in the Arduino IDE. Plug in your Jewelbot and select TOOLS > BOARDS > SOLO CODING MODE in the Arduino IDE. Make sure the USB port is selected in the IDE as the Port under the Tools menu. Click on the checkmark button in the Arduino IDE, this will verify that the code compiles correctly. If you get any errors, just ask a mentor for help!

18. Put your Jewelbot into upload mode by plugging it in to the computer and holding down on the magic button for three seconds. You will see all four leds breathe blue. Then click the the arrow button in the Arduino IDE to upload your code. You will get an orange success message in the IDE when upload is complete. If you're on a Linux computer and your code repeatedly won't upload, you may need to give your computer permission to write out to the USB ports by typing `sudo adduser $USER dialout` into the terminal.

19. Unplug your Jewelbot and test out your new Timer! Click the magic button one time to set the timer for 1 minute. Press the magic button for two full seconds to start the timer. You will see all four leds flash blue (or whatever color you changed it to) one time for every minute set on the timer. The leds will flash red (or whatever color you changed it to) once every 60 seconds. When the timer ends, you will feel a buzz and see an led animation.

20. Congratulations


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
