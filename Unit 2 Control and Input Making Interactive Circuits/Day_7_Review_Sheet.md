<!-- command: render -->

# Review Sheet: PWM, ADC, Digital Inputs/Outputs, and Pico 2W Pinout



![pico 2w pinout-small.png](../Unit%201%20Foundations%20Electricity%2C%20Python%2C%20and%20Git/img/pico%202w%20pinout-small.png)

---

## 1. Raspberry Pi Pico 2W Pinout Basics

You should know the purpose of the following:

### General Pin Categories
- **3V3 (3.3 volts)**: Safe power output for small components and sensors.
- **VSYS**: Main system power input. Usually supplied by USB or an external battery.
- **VBUS**: A source of steady 5V power.
- **GND**: Ground. All circuits must share ground.
- **GPIO pins**: General Purpose Input/Output pins you can read from or write to.
- **ADC pins**: Pins that can measure analog voltages using the Pico's built-in analog-to-digital converter.
- **PWM capable pins**: Any GPIO pin can output PWM in MicroPython.

### What you should understand from the pinout
- Which pins support ADC (GPIO 26, 27, 28).
- Where ground and power pins are located.
- How to identify a GPIO number from the physical pin diagram.
- That the Pico 2W adds WiFi but the basic pinout arrangement is unchanged.

### What you do NOT need to understand yet
- UART  
- SPI  
- I2C details

---

## 2. Digital Inputs and Outputs

### Digital Output
To set a pin as an output and write a value:

```python
from machine import Pin
led = Pin(15, Pin.OUT)
led.value(1)   # sets the pin HIGH
led.value(0)   # sets the pin LOW
```

### Digital Input
To read a button:

```python
button = Pin(14, Pin.IN, Pin.PULL_DOWN)
state = button.value()
```

The input value is either:
- `1`: HIGH (3.3V)
- `0`: LOW (0V)

---

## 3. Pull-up and Pull-down Resistors (Important Details)

Digital inputs read HIGH or LOW. But if nothing is connected, the pin "floats."  
A floating input does not know whether it should read 1 or 0. It may randomly change because of electrical noise in the circuit.

To prevent this, we use a **pull-up** or **pull-down** resistor.

### Pull-down resistor
- Connects the pin weakly to ground ($0$ volts).
- Default state is LOW ($0$).
- When you press a button that connects the pin to 3.3V, the input becomes HIGH.
- In code:

```python
button = Pin(14, Pin.IN, Pin.PULL_DOWN)
```

### Pull-up resistor
- Connects the pin weakly to 3.3V.
- Default state is HIGH ($1$).
- Pressing the button connects the pin to ground, making it LOW.
- In code:

```python
button = Pin(14, Pin.IN, Pin.PULL_UP)
```

### Why these resistors matter
- They ensure a **stable default value**.
- They prevent noisy readings.
- They protect your circuit by avoiding direct short circuits between power and ground.

### Internal vs External
- The Pico provides **internal pull-up and pull-down resistors**, activated with `Pin.PULL_UP` or `Pin.PULL_DOWN`.
- External resistors are sometimes needed for sensors, but not for simple button circuits.

---

## 4. PWM Review

PWM stands for Pulse Width Modulation.

Used for:
- Dimming LEDs
- Speed control of motors
- Generating analog-like output signals

Example:

```python
from machine import Pin, PWM
p = PWM(Pin(15))
p.freq(1000)
p.duty_u16(32768)   # about 50 percent brightness
```

Important ideas:
- **Frequency**: how many times the PWM pattern repeats per second.
- **Duty cycle**: the percentage of time the signal is HIGH in each cycle.
- Duty ranges from `0` to `65535` in MicroPython.

---

## 5. ADC Review

The ADC measures analog voltages and converts them into digital values.

Example:

```python
from machine import ADC
sensor = ADC(26)   # ADC0
value = sensor.read_u16()
```

You should know:
- ADC values are between `0` and `65535`.
- `0` corresponds approximately to $0$ volts.
- `65535` corresponds approximately to $3.3$ volts.
- ADC pins are GPIO 26, 27, and 28.

---

# Practice Quiz

## Part I: Multiple Choice

1. A pin configured with `Pin(14, Pin.IN)` is used to:  
   A. Send digital signals  
   B. Read digital signals  
   C. Produce PWM signals  
   D. Measure analog voltages

2. Which of the following pins on the Pico 2W can be used for ADC?  
   A. GPIO 0-5  
   B. Only GPIO 2  
   C. GPIO 26-28  
   D. All GPIO pins

3. PWM is best described as:  
   A. A sensor that measures voltage  
   B. A rapidly switching digital signal that simulates analog output  
   C. A direct analog voltage output  
   D. A communication protocol

4. The duty cycle of a PWM signal controls:  
   A. The frequency  
   B. The percentage of time the signal is HIGH  
   C. The voltage limit of the Pico  
   D. The type of resistor needed

5. A pull-down resistor ensures that a button input reads:  
   A. HIGH by default  
   B. LOW by default  
   C. A floating value  
   D. Always 3.3V

---

## Part II: Short Answer

6. Explain the difference between a digital input and a digital output.

7. Why are pull-up or pull-down resistors needed for button circuits?

8. What does the ADC measure, and why is it useful?

9. What does "duty cycle" mean in a PWM signal?

---

## Part III: Code Reading

10. Consider the following code:

```python
from machine import Pin, PWM
pwm = PWM(Pin(15))
pwm.freq(500)
pwm.duty_u16(5000)
```

Describe what happens to the output on pin 15.

---

## Part IV: Pinout Labeling

Using the Pico 2W pinout diagram at the top of this sheet, label:

- Two power pins  
- Two ground pins  
- One ADC pin  
- One GPIO pin you have used in class  

