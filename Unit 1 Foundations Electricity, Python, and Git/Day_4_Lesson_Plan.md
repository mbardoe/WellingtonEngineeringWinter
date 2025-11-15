<!-- command: render -->

# Lesson Plan – Day 4  
**Course:** Engineering: Electronics and Computer Programming  
**Duration:** 70 minutes  
**Topic:** Flashing Firmware, Digital Input with Buttons, Pull-Up/Pull-Down Resistors, and LED Control

---

## Objectives

By the end of this lesson, students will:
1. Install or reinstall MicroPython firmware onto the Raspberry Pi Pico 2 W.  
2. Write a MicroPython program that blinks an LED.  
3. Build a button input circuit and understand the role of pull-up and pull-down resistors.  
4. Write code that reads a button press and prints its state to the monitor.  
5. Combine input and output: a circuit and program that lights an LED when the button is pressed.

---

## Materials

- Raspberry Pi Pico 2 W  
- USB cable  
- Breadboard  
- LED and 220 ohm resistor  
- Pushbutton  
- Jumper wires  
- Projector for demonstration  
- Thonny installed on student laptops  

---


## Vocabulary

- Firmware  
- GPIO (input vs output)  
- Pull-up resistor  
- Pull-down resistor  
- Floating pin  
- Digital input  
- Debounce (introduced lightly)

---

## Lesson Outline

### 1. Flashing MicroPython Firmware (10 minutes)

Steps:

1. Hold down BOOTSEL while plugging in the Pico 2 W.  
2. The board mounts as a USB drive.  
3. Drag the MicroPython firmware `.uf2` file onto the drive.  
4. The Pico reboots.

In Thonny:

```python
print("Pico ready.")
```

---

### 2. LED Blink Program (10 minutes)

Circuit:
- GP15 → resistor → LED anode  
- LED cathode → GND

Program:

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

### 3. Button Input Circuit (15 minutes)

Explain floating pins and pull-up/pull-down logic.

Circuit:
- One side of button → GND  
- Other side → GP14  

Use the internal pull-up resistor:

```python
button = Pin(14, Pin.IN, Pin.PULL_UP)
```

---

### 4. Program to Print Button State (10 minutes)

```python
from machine import Pin
import time

button = Pin(14, Pin.IN, Pin.PULL_UP)

while True:
    if button.value() == 0:
        print("Button pressed")
    else:
        print("Button released")
    time.sleep(0.2)
```

---

### 5. LED When Button Pressed (20 minutes)

Final circuit: LED + button connected.

```python
from machine import Pin
import time

led = Pin(15, Pin.OUT)
button = Pin(14, Pin.IN, Pin.PULL_UP)

while True:
    if button.value() == 0:
        led.value(1)
    else:
        led.value(0)
    time.sleep(0.05)
```

---

## Closing (5 minutes)

Discussion questions:
- Why do pull-up resistors exist?  
- What does it mean when a pin is “floating”?  
- How did input and output interact today?

---

## Assessment

- Working blink circuit  
- Button input program  
- Combined LED + button program  

---

## Homework

1. Explain why pull-up resistors are needed.  
2. Modify your code so the LED blinks twice when the button is pressed.  
3. Bring your circuits for testing next class.

