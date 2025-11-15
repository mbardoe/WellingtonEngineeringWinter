<!-- command: render -->

# Lesson Plan – Day 5  
**Course:** Engineering: Electronics and Computer Programming  
**Duration:** 45 minutes  
**Topic:** Using a 10K Potentiometer (Variable Resistor) with MicroPython  

---

## Objectives

By the end of this lesson, students will:
1. Understand what a potentiometer is and how it works as a variable resistor.
2. Wire a 10K potentiometer to the Raspberry Pi Pico 2 W.
3. Read analog values using an ADC pin.
4. Write MicroPython code to print potentiometer readings.
5. (Optional) Use the potentiometer to control LED brightness.

---

## Materials
- Raspberry Pi Pico 2 W
- Breadboard
- 10K potentiometer
- LED and 220 ohm resistor
- Jumper wires
- USB cable
- Thonny installed

---

## Potentiometer Wiring
- Left pin → **3V3(OUT)**
- Right pin → **GND**
- Middle pin → **GP26 (ADC0)**

---

## Code: Read Potentiometer Value
```
from machine import ADC, Pin
import time

pot = ADC(26)  # GP26 = ADC0

while True:
    reading = pot.read_u16()  # 0–65535
    print("Raw reading:", reading)
    time.sleep(0.1)
```

---

## Optional: Convert to Percentage
```
percent = int((reading / 65535) * 100)
print("Percent:", percent)
```

---

## Optional: Control LED Brightness
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

---

## Closing Questions
- What does the potentiometer measure?
- Why do we need an ADC pin?

---

