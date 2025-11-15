<!-- command: render -->

# Lesson Plan – Day 6  
**Course:** Engineering: Electronics and Computer Programming  
**Duration:** 70 minutes  
**Topic:** Mini-Project: Designing a Multi-Input, Multi-Output Circuit (Part 1)

---

## Objectives

By the end of this class, students will:
1. Clone the Day 6 project repository from GitHub Classroom.
2. Design a circuit that uses **at least 2 input devices** and **3 output devices**.
3. Begin writing a MicroPython program that:
   - Reads both input devices, and  
   - Generates at least three different outputs using three output devices.
4. Create a project `README.md` documenting:
   - The initial plan,
   - Challenges encountered so far,
   - Differences between the plan and the working design.
5. Make substantial progress on the design during class, with additional work continuing after Thanksgiving break.

---

## Materials

- Raspberry Pi Pico 2 W  
- Breadboard(s)  
- Input devices (students choose two):
  - Pushbuttons  
  - Potentiometers  
  - Photoresistors  
  - Switches  
  - Capacitive touch sensors  
- Output devices (students choose three):
  - LEDs  
  - Buzzers  
  - Servos  
  - DC motors  
  - RGB LED modules  
- Jumper wires, resistors  
- Laptop with Thonny and Git  
- GitHub Classroom assignment link  
- Printed planning sheets (optional)

---

## Vocabulary

- Input device  
- Output device  
- Multi-modal system  
- Control logic  
- Repository  
- README  
- Iteration  

---

## Lesson Outline

### 1. Opening (5 minutes)

- Introduce today’s mini-project:
  Students will design and build a **multi-input, multi-output embedded system**.
- Explain that this will span:
  - Today’s class (Day 6),
  - Continued work after Thanksgiving break.

---

### 2. Clone GitHub Classroom Repository (10 minutes)

Students:
1. Open the classroom assignment link.  
2. Accept the assignment (GitHub creates a personal repository).  
3. Copy the repo’s clone URL.  
4. Clone to their machine:

```
git clone https://github.com/.../day6_project.git
```

5. Confirm the folder contains:
   - `main.py` (starter or blank)  
   - `README.md` (template)  

---

### 3. Project Requirements Overview (5 minutes)

The project **must include**:
- **Two input devices** (examples: button + pot; switch + light sensor; pot + capacitive sensor).  
- **Three output devices** (examples: LED + buzzer + servo; RGB LED + DC motor + LED).  

The program must:
- Continuously read input values,
- Decide what output(s) to generate,
- Produce at least **three different output behaviors**.

The README must document:
- Initial plan and intended behavior,
- Challenges encountered,
- Final differences or improvements.

---

### 4. Circuit Design Planning (10 minutes)

Students sketch:
- Device choices (inputs, outputs),
- Pin choices,
- Power requirements,
- What each input should *control*,
- What the three output modes will be.

Possible guiding questions:
- What will the two inputs control?
- What will each output device do?
- How do your modes differ from one another?

Teacher circulates and checks feasibility.

---

### 5. Circuit Wiring Work Time (15 minutes)

Students begin wiring on the breadboards:
- Encourage testing input pins first (`print()` checks).
- Outputs can be connected one at a time.
- Students should label their circuits or document pins in a notebook.

---

### 6. Starting the MicroPython Program (15 minutes)

Students begin coding their `main.py`.

Recommended starter template:

```
from machine import Pin, ADC, PWM
import time

# Example placeholders:
button = Pin(14, Pin.IN, Pin.PULL_UP)
pot = ADC(26)
led = Pin(15, Pin.OUT)

# Add additional inputs/outputs here

while True:
    # Read input values
    b = button.value()
    p = pot.read_u16()

    # Logic for outputs
    # Students insert their own control logic here

    time.sleep(0.05)
```

Students should:
- Test one device at a time,
- Use the REPL to print input values,
- Gradually add conditional logic.

---

### 7. Work on README.md (5 minutes)

Students begin filling out:
- **Initial plan** (inputs, outputs, desired behavior),
- **Expected flow of logic**, possibly with a diagram,
- **Questions or concerns** for next class.

---

## Closing (5 minutes)

Ask students:
- What devices did you choose and why?
- What is one challenge you expect to face?
- What is one thing you successfully wired or coded today?

Remind them they will continue this project after Thanksgiving break.

---

## Assessment

- Evidence of planning (sketch, README start, pin mapping).
- Circuit wiring progress.
- Initial code in `main.py` demonstrating at least one working input and one working output.

---

## Homework (Optional)

- Continue README documentation.
- Continue wiring testing if possible at home.
- Think of 1 or 2 alternative behaviors to add next class.

