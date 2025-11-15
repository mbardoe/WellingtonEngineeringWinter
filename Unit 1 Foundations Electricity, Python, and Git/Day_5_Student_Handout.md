<!-- command: render -->

# Day 5 Student Handout  
**Topic:** Potentiometers, Analog Input, and the ADC on the Raspberry Pi Pico 2 W

---

## 1. What is a Potentiometer?

A **potentiometer** (often called a “pot”) is a **variable resistor**.  
Turning the knob changes the resistance and therefore changes the **voltage** on the middle pin (the wiper).

It acts as a **voltage divider**:

- One side goes to **3.3 V**
- The other side goes to **GND**
- The middle pin provides a voltage between **0 V and 3.3 V**

**Space for picture of potentiometer:**  
[INSERT IMAGE HERE]

---

## 2. Wiring the Potentiometer to the Pico 2 W

Use a **10K ohm potentiometer** and wire it like this:

- Left pin → **3V3(OUT)**  
- Right pin → **GND**  
- Middle pin → **GP26 (ADC0)**  

**ADC pins on the Pico 2 W:**
- GP26 → ADC0  
- GP27 → ADC1  
- GP28 → ADC2  

**Space for wiring picture:**  
[INSERT IMAGE HERE]

---

## 3. Reading the Potentiometer Value in MicroPython

Use this starter code:

```
from machine import ADC, Pin
import time

pot = ADC(26)  # GP26 = ADC0

while True:
    reading = pot.read_u16()  # range: 0–65535
    print("Raw reading:", reading)
    time.sleep(0.1)
```

**What the values mean:**

- **0** → the wiper is near GND  
- **65535** → the wiper is near 3.3 V  
- Middle positions give intermediate values  

---

## 4. Optional: Convert to a Percentage

```
percent = int((reading / 65535) * 100)
print("Percent:", percent)
```

---

## 5. Optional: Control LED Brightness with the Potentiometer

Wire an LED:

- GP15 → resistor → LED anode  
- LED cathode → GND  

Then run:

```
from machine import ADC, Pin, PWM
import time

pot = ADC(26)
led = PWM(Pin(15))
led.freq(1000)

while True:
    reading = pot.read_u16()
    led.duty_u16(reading)
    time.sleep(0.01)
```

This uses PWM (pulse-width modulation) to change brightness.

**Space for LED wiring picture:**  
[INSERT IMAGE HERE]

---

## 6. Key Ideas Today

- Potentiometers act as variable resistors.  
- They create a **voltage divider**, producing a variable voltage.  
- The Pico reads voltage using an **ADC pin**.  
- ADC values range from **0 to 65535** (16-bit).  

---

## 7. Homework

1. Write 4–6 sentences explaining how a potentiometer works.  
2. Modify the code so the reading prints only every **0.2 seconds**.  
3. Bring your wired circuit to next class for testing.

