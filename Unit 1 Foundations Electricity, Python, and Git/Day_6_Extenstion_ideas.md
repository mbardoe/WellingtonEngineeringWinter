<!-- command: render -->

# Optional Extensions for Your 2-Input / 3-Output Project

These extensions are **in order of increasing complexity**.  
Try them in sequence, or choose the one that feels like the right challenge.

Your existing project should already have:
- At least **two inputs** (for example, button + potentiometer)
- At least **three outputs** (for example, LED(s), buzzer, servo, etc.)
- A `main.py` loop that reads inputs and updates outputs.

---

## 1. Store State (Toggle or Mode Memory)

Right now, your outputs may respond *directly* to the current input values.  
In this extension, you will make your system **remember** something over time.

Examples:
- A button that **toggles** an LED on and off (instead of just mirroring the button).  
- A system mode that changes each time you press a button:
  - Mode 0: all LEDs off  
  - Mode 1: LED 1 blinks  
  - Mode 2: LED 2 blinks  

### Key Idea: Use a Variable Outside the Loop

You need a variable defined before the loop that you **update inside** the loop.

Example sketch:

```python
from machine import Pin
import time

button = Pin(14, Pin.IN, Pin.PULL_UP)
led = Pin(15, Pin.OUT)

mode = 0   # this variable stores state
last_button = 1

while True:
    current_button = button.value()

    # Detect button press transition: HIGH -> LOW
    if last_button == 1 and current_button == 0:
        mode = (mode + 1) % 3  # cycles: 0, 1, 2, 0, 1, 2, ...

    # Use the mode to control behavior
    if mode == 0:
        led.value(0)
    elif mode == 1:
        led.value(1)
    elif mode == 2:
        led.value((int(time.time() * 2) % 2))  # simple blink

    last_button = current_button
    time.sleep(0.02)
```
You can adapt this pattern to:

- store “armed/disarmed” state
- store brightness level
- store current output pattern

2. Use Both Inputs Together (Branch into Different Behaviors)
In your base project, inputs might control different things independently.
In this extension, you will create branches in behavior depending on both inputs.

Examples:

Button chooses between “mode A” and “mode B”, and the potentiometer does different things in each mode.

If the button is pressed and the pot is above a threshold, you trigger a special pattern.

Key Idea: Combine Conditions in if-statements
You can use and, or, and nested if statements.

Example sketch:

```python
from machine import Pin, ADC
import time

button = Pin(14, Pin.IN, Pin.PULL_UP)
pot = ADC(26)

led1 = Pin(15, Pin.OUT)
led2 = Pin(16, Pin.OUT)

while True:
    button_state = button.value()          # 0 when pressed
    pot_value = pot.read_u16()            # 0–65535
    high_pot = pot_value > 40000

    if button_state == 0 and high_pot:
        # Branch 1: button pressed AND pot high
        # Example: both LEDs on
        led1.value(1)
        led2.value(1)
    elif button_state == 0 and not high_pot:
        # Branch 2: button pressed AND pot low
        # Example: only led1 on
        led1.value(1)
        led2.value(0)
    else:
        # Branch 3: button not pressed
        # Example: only led2 on
        led1.value(0)
        led2.value(1)

    time.sleep(0.05)
```
Your challenge:

- Replace the “example” actions with your own outputs (servo, buzzer, patterns, etc.).
- Make the branches meaningfully different, not just “LED on/off.”

3. Add a New Sensor or Output (Photoresistor and/or Buzzer)
Now extend your hardware by adding one or two new components:

- Photoresistor (LDR) + resistor as a [voltage divider](https://youtu.be/TLfnSQdpAnQ) into an ADC pin
- Buzzer (preferably a passive buzzer) driven by PWM



You should:

Wire the new device correctly.

Add code that reads or controls it.

Integrate it into your existing logic (do not just make a separate test program).

3a. Photoresistor as a Light Sensor
Typical wiring:

Photoresistor + fixed resistor form a voltage divider.

Middle node → ADC pin (e.g. GP27).

One side of the divider to 3V3, other to GND.

Example sketch:

```python
from machine import ADC
import time

ldr = ADC(27)   # wired to the voltage divider

while True:
    light_raw = ldr.read_u16()
    print("Light level:", light_raw)
    # TODO: use this value to change an LED pattern or mode
    time.sleep(0.1)
```
Use the reading to:

turn something on only in the dark,

change brightness or blink speed,

choose between behaviors.

3b. Buzzer as an Output (PWM)
Basic scaffold:

```python
from machine import Pin, PWM
import time

buzzer = PWM(Pin(17))
buzzer.freq(1000)          # 1 kHz tone

def beep(duration_ms=200):
    buzzer.duty_u16(30000)  # non-zero duty (makes sound)
    time.sleep(duration_ms / 1000)
    buzzer.duty_u16(0)      # silence

# Example use:
# beep(200)
```
Integrate the buzzer with:

button presses (feedback sounds),

light levels (alarm when too bright/dark),

pot position (pitch control, if you adjust freq()).

4. Create a Separate Module and Use It in main.py
In this extension, you will refactor your code so that some functionality lives in a separate Python file (a module), and main.py imports and uses it.

Examples:

sensors.py handles reading the potentiometer or photoresistor.

outputs.py handles controlling LED patterns or buzzer behavior.

4a. Create a Module (e.g., sensors.py)
Create a file sensors.py on the Pico with something like:

```python
# sensors.py

from machine import ADC, Pin

pot = ADC(26)
ldr = ADC(27)

def read_pot_percent():
    raw = pot.read_u16()
    return int((raw / 65535) * 100)

def read_light_raw():
    return ldr.read_u16()
```
You can also create an output module, for example outputs.py:

```python

# outputs.py

from machine import Pin, PWM
import time

led = Pin(15, Pin.OUT)
buzzer = PWM(Pin(17))

def set_led(on):
    led.value(1 if on else 0)

def beep_short():
    buzzer.freq(1000)
    buzzer.duty_u16(30000)
    time.sleep(0.1)
    buzzer.duty_u16(0)
```
4b. Import and Use the Module in main.py
In main.py:

```python

import time
import sensors
import outputs

from machine import Pin

button = Pin(14, Pin.IN, Pin.PULL_UP)

while True:
    button_state = button.value()
    pot_percent = sensors.read_pot_percent()
    light = sensors.read_light_raw()

    # Example use of module logic:
    if button_state == 0 and pot_percent > 50:
        outputs.set_led(True)
        outputs.beep_short()
    else:
        outputs.set_led(False)

    # TODO: add more complex behavior here

    time.sleep(0.05)
    
```
Your challenge:

- Decide which parts of your project belong in a module.
- Keep main.py as “high-level” logic that calls functions from your module(s).
- Make sure everything still works after refactoring.

General Expectations
For each extension, you should:

- Keep your wiring diagram or pin table up to date.
- Make regular commits to Git with clear messages.

Update your README.md to describe:

- what you changed,
- why you changed it,
- any challenges you encountered.