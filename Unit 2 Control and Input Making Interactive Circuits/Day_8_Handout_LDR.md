<!-- command: render -->

# Day 8: Light Sensor (LDR) and Voltage Divider Handout

## What You Will Learn
- What a photoresistor (LDR) is and how it reacts to light.
- What a voltage divider is and why sensors often use one.
- How to wire and read an LDR using an ADC pin on your microcontroller.
- How to write simple code to respond to changing light levels.

---

# 1. What is an LDR?
An **LDR (Light Dependent Resistor)** is a resistor whose resistance changes with light:
- More light → lower resistance  
- Less light → higher resistance

Your microcontroller **cannot measure resistance directly**, but it *can* measure voltage.  
This is why we use a **voltage divider**.

---

# 2. Voltage Divider Basics
A voltage divider uses two resistors in series to split voltage.

Formula:

$$ V_{out} = V_{in} \cdot \frac{R_2}{R_1 + R_2} $$

Where:

- $R_1$ is the top resistor
- $R_2$ is the bottom resistor
- $V_{out}$ is measured at the midpoint

In our circuit:

- One resistor = LDR (variable)
- Other resistor = fixed 10 kΩ
- The voltage at the middle changes with light.

---

# 3. Wiring Diagram (Text Version)

```
3.3V ---- LDR ----*---- 10k resistor ---- GND
                  |
                  +---- ADC pin (GP26)
```

Steps:

1. Connect one leg of the LDR to 3.3 V.
2. Connect the other leg of the LDR to a row on the breadboard.
3. From that row, connect a 10 kΩ resistor to GND.
4. Connect the **junction** between the LDR and resistor to an **ADC pin** (GP26).

---

# 4. Starter Code: Reading the LDR

```python
from machine import ADC, Pin
import time

sensor = ADC(26)

while True:
    value = sensor.read_u16()
    print(value)
    time.sleep(0.1)
```

Try this:

- Cover the sensor with your hand.
- Shine a phone flashlight on it.
Watch how the printed numbers change.

---

# 5. Threshold Example

```python
from machine import ADC, Pin
import time

sensor = ADC(26)
led = Pin(15, Pin.OUT)

threshold = 30000

while True:
    level = sensor.read_u16()

    if level > threshold:
        led.value(1)
    else:
        led.value(0)

    time.sleep(0.05)
```

Adjust `threshold` to match room lighting.

---

# 6. Your Tasks

1. In your own words, explain what a voltage divider does.  
2. Record the ADC values in three conditions: 

   - classroom lights on  
   - hand covering LDR  
   - bright phone flashlight  
   
3. Write short code (8–12 lines) that turns an LED on only when light is above or below your chosen threshold.

---

# 7. Extra Challenge
Try mapping the light level to PWM brightness.

