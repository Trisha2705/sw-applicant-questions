# Challenge

This assessment is intentionally short and approachable. We value how you learn and reason about problems more than prior electronics experience.

All work is completed in the Tinkercad online simulator. Create a free account at:

https://www.tinkercad.com

## Project Summary
Build a reaction time tester. The device waits a random amount of time, signals the user, and measures how quickly the button is pressed.

## Required Behaviors
Implement the following states in both the circuit and the program.

### 1) Idle
- LED is off.
- The system waits for a button press to arm the device.

### 2) Armed
- LED slowly pulses.
- The device waits a random duration between 2 and 10 seconds.
- If the button is pressed during this phase, record a false start (see "False Start" below).

### 3) Reaction
- LED turns on instantly as the signal.
- Start the timer and record the reaction time when the button is pressed.

## Output and Feedback
### LED feedback based on reaction time

| Reaction Time | LED Pattern  |
| ------------- | ------------ |
| < 200 ms      | Fast blink   |
| 200-350 ms    | Medium blink |
| > 350 ms      | Slow blink   |

### Serial Monitor output
Print output similar to the following:
```
Attempt: 3
Reaction: 284 ms
Average: 301 ms
False Starts: 1
```

### False Start
If the button is pressed before the signal:
- Rapidly flash the LED for 2 seconds.
- Record a false start.
- Return to Idle.

## Rules
Please read [RULES.md](RULES.md) before starting.

## Submission
Place the following in [submission/SUBMISSION.md](submission/SUBMISSION.md):
1. Your Tinkercad circuit link. Set your project visibility to `public` and share the link.
2. A short explanation of how your program and circuit work, including any assumptions or design decisions.

Follow the submission guide in [README.md](README.md).
