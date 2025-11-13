<!-- command: render -->

# Day 3 Student Handout  
**Topic:** Log Ride Analogy, Breadboards, Pico Pinout, and LED Blink

---

## 1. Log Ride Analogy

| Component | Log Ride Analogy | Effect |
|----------|------------------|--------|
| Resistor | Narrow section | Reduces flow |
| Diode | One-way gate | Flow allowed one direction |
| Capacitor | Side pool | Stores/releases water |
| Switch | Gate | Starts/stops flow |
| DC Motor | Water wheel | Converts flow into motion |

---

## 2. Raspberry Pi Pico W Pinout

![Pico 2 W Pinout](img/pico%202w%20pinout.png)



Important pins:

- GPIO (GP0–GP28): programmable digital pins  
- GND: ground reference  
- 3V3(OUT): regulated 3.3 V output  
- VBUS: 5 V from USB  
- VSYS: system power (battery or external 5 V)  
- RUN: reset input  
- 3V3(EN): regulator enable  

---

## 3. Breadboard Basics

- Power rails: long columns for + and –  
- Rows: groups of 5 connected internally  
- Center gap breaks continuity  

Circuit layout:
- GP15 → resistor → LED anode  
- LED cathode → GND  

---

## 4. Predict the LED Behavior

Code A:
```python
led.value(1)
time.sleep(1)
led.value(1)
time.sleep(1)
```

Code B:
```python
while True:
    led.toggle()
    time.sleep(0.1)
```

Code C:
```python
while True:
    led.value(1)
    time.sleep(0.2)
    led.value(0)
    time.sleep(0.5)
```

Write predictions in your notebook.

---

## 5. Blink Circuit Code

Use this program in Thonny:

```python
from machine import Pin
import time

led = Pin(15, Pin.OUT)

while True:
    led.value(1)
    time.sleep(0.5)
    led.value(0)
    time.sleep(0.5)
```

---

## 6. Goals for Today

- Understand electricity using analogy  
- Identify pinout and breadboard connections  
- Build and run a working LED blink circuit  
- Predict LED behavior based on code  

