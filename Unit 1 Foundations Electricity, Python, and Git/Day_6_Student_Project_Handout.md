<!-- command: render -->

# Day 6 Project Handout  
**Engineering: Electronics and Computer Programming**  
**Mini-Project: Multi-Input, Multi-Output Circuit**  

---

## 1. Project Overview

Today you will begin designing and building a small electronic system that uses:

- **At least 2 input devices**  
- **At least 3 output devices**  
- A MicroPython program that reads input values and produces **at least 3 distinct output behaviors**

You will continue working on this project after Thanksgiving break.

Your work must be documented in a `README.md` file within your GitHub Classroom repository.

---

## 2. Requirements Summary

### Hardware Requirements
Your circuit must include:
- **Two inputs** (choose from below):
  - Pushbutton  
  - Switch  
  - Potentiometer  
  - Photoresistor  
  
- **Three outputs** (choose from below):
  - LED  
  - RGB LED  
  - Buzzer
  - Other approved actuator  

Each device must be safely and correctly wired.

### Software Requirements
Your `main.py` program must:
1. Read both input devices.  
2. Use logic (if/else or other structures) to control at least **three different outputs or output behaviors**.  
3. Run continuously in a loop.  
4. Be commented and readable.

### Documentation Requirements
Your `README.md` must include:
1. **Initial Plan**  
   - What you intended to build  
   - Which inputs and outputs you selected  
2. **Challenges**  
   - Wiring issues  
   - Code bugs  
   - Unexpected behavior  
3. **Differences from the Initial Plan**  
   - What changed and why  

---

## 3. Planning Worksheet

Use this worksheet to plan before building.

### A. Inputs
List your **two** chosen input devices and what they will control.

1. Input #1: ______________________________  
   Behavior Controlled: _______________________

2. Input #2: ______________________________  
   Behavior Controlled: _______________________

### B. Outputs
List your **three** chosen outputs and what each should do.

1. Output #1: ______________________________  
   Description: _______________________________

2. Output #2: ______________________________  
   Description: _______________________________

3. Output #3: ______________________________  
   Description: _______________________________

### C. Initial Logic Plan
Describe how your system will behave.

- If input A does ____________, then output X should ______________________  
- If input B does ____________, then output Y should ______________________  
- Additional behavior: _________________________________________________  

### D. Pin Mapping Table
Fill this in as you design your circuit.

| Device | Type (Input/Output) | Pin Number | Notes |
|--------|----------------------|------------|-------|
|        |                      |            |       |
|        |                      |            |       |
|        |                      |            |       |
|        |                      |            |       |
|        |                      |            |       |


---

## 4. Starter Code Template

Use this as a base for your project:

```
from machine import Pin, ADC, PWM
import time

BUTTON_PIN=-1
POT_PIN=-1

LED_ONE_PIN=-1
LED_TWO_PIN=-1
BUZZER_PIN=-1

# Example placeholders — replace with your devices
button = Pin(BUTTON_PIN, Pin.IN, Pin.PULL_UP)
pot = ADC(POT_PIN)

led1 = Pin(LED_ONE_PIN, Pin.OUT)
led2 = Pin(LED_TWO_PIN, Pin.OUT)
buzzer = PWM(BUZZER_PIN)

while True:
    # Read inputs
    button_state = button.value()
    pot_value = pot.read_u16()

    # Output logic (replace with your own)
    # Example:
    #if Boolean evaluation:
        # output action
        
    #elif Boolean evaluation:
        # different action
        
    #else:
        # Alternative action



    time.sleep(0.05)
```

---

## 5. Grading Rubric (100 Points Total)

### A. Hardware Implementation (30 points)
- 2 working input devices (10 pts)  
- 3 working output devices (10 pts)  
- Circuit is safe, organized, and clearly mapped (10 pts)

### B. Software Implementation (35 points)
- Program reads both inputs correctly (10 pts)  
- Program produces at least 3 distinct output behaviors (15 pts)  
- Code is clear, commented, and functional (10 pts)

### C. Documentation (25 points)
- README includes initial plan (10 pts)  
- README describes challenges and debugging (10 pts)  
- README explains differences between plan and final system (5 pts)

### D. Process and Professionalism (10 points)
- Effective use of class time  
- Regular commits to GitHub  
- Collaborative and safe working habits  

---

## 6. Goals for Today

By the end of class, you should have:
1. Cloned your GitHub Classroom repository.  
2. Completed the planning worksheet.  
3. Built or begun building your circuit.  
4. Started your `main.py` and `README.md` files.  

---

## 7. After Thanksgiving Break

Next class, you will:
- Finish wiring  
- Complete programming  
- Finalize the README  
- Push commits back to GitHub
