## Tinkercad Circuit Link
``````
https://www.tinkercad.com/things/cmJHeFI3oYV-reaction-time-tester-?sharecode=Gqqmb0y5yZSCxzh7tNF9V1-S90cTkFypqkPnqTwhr-8

## Program Explanation
```

The program is a simple reaction time tester that works using three main states: IDLE, ARMED, and REACTION. In the IDLE state, the LED is off, and the system just waits for the user to press the button to start. Once the button is pressed, the program moves into the ARMED state.

In the ARMED state, I generate a random delay between 2 and 10 seconds before the signal turns on. I used random() for this so the user can’t predict when the LED will light up. I also used delay() to make the LED blink slowly so the user knows the system is active (blinking). For example, if the user presses the button too early, it counts as a false start, and the LED flashes really fast for 2 seconds. 

To make the delay more unpredictable, I used randomSeed(analogRead(0)). This reads a floating analog pin, which picks up random electrical noise. This means the delay changes each time the program runs. I added this after researching so there is no delay pattern.  

During the ARMED state, the LED also slowly blinks to show the system is ready. If the button is pressed during this period, it’s a false start, the LED flashes rapidly as a warning, and the program goes back to IDLE.

Once the random delay finishes, the program enters the REACTION state. The LED turns on fully, and the user has to press the button as quickly as possible. I measure the reaction time using millis() by recording when the LED turns on and comparing it to when the button is pressed.

The program keeps track of attempts, total reaction time, and false starts, and prints them to the Serial Monitor. I also calculate the average reaction time so the user can see if they are improving.

The LED also gives visual feedback depending on how fast the user reacted: fast blinking for very quick reactions, medium blinking for average reactions, and slow blinking for slower reactions. The program resets to IDLE.

For the circuit, the LED is connected to pin 9 because it supports Pulse Width Modulation, which is useful for the pulsing effect in the ARMED state. I added a 200-ohm resistor to protect the LED. I calculated this using Ohm’s law, taking into account the 5V supply from the Arduino, the LED voltage of 3 needed to turn it on, and 15 ma current needed for LED. The push button is connected to pin 2 using INPUT_PULLUP, which acts as an internal resistor. 