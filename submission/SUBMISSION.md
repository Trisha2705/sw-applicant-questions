## Tinkercad Circuit Link

``````


## Program Explanation
```

The program is a simple reaction time tester that works using three main states: IDLE, ARMED, and REACTION. In the IDLE state, the LED is off, and the system just waits for the user to press the button to start. Once the button is pressed, the program moves into the ARMED state. Here, I use a random delay between 2 and 10 seconds before the signal comes on. I made the delay random using random() and also used the delay() function to make the LED blink. For example, if the user presses the button too early, it counts as a false start, and the LED flashes really fast for 2 seconds. 

To make the random delay more unpredictable, I used randomSeed(analogRead(0)). This reads an unused analog pin, which is floating, so it picks up a bit of random electrical noise from the environment. This noise gives a different number each time, so the LED signal happens at a different time on each attempt. I found this worked better than just relying on random() alone when I was researching reaction time programs.

During the ARMED state, the LED also slowly blinks to show the system is ready. If the button is pressed during this period, it’s a false start, the LED flashes rapidly as a warning, and the program goes back to IDLE.

Once the random delay finishes, the program enters the REACTION state. The LED turns on fully to tell the user to press the button as fast as they can. The program then measures the time from the LED turning on to the button being pressed using millis(). This is recorded as the user’s reaction time. The program keeps track of the number of attempts, the total reaction time, and the number of false starts. It also calculates the average reaction time and prints all of this to the Serial Monitor so the user can see their performance.

The LED also gives visual feedback depending on how fast the user reacted: fast blinking for very quick reactions, medium blinking for average reactions, and slow blinking for slower reactions. The program resets to IDLE.

For the circuit, the LED is connected to pin 9 because it supports Pulse Width Modulation, which is useful for the pulsing effect in the ARMED state. I added a 200-ohm resistor to protect the LED. I calculated this using Ohm’s law, taking into account the 5V supply from the Arduino, the LED voltage of 3 needed to turn it on, and 15 ma current needed for LED. The push button is connected to pin 2 using INPUT_PULLUP, which acts as an internal resistor. 