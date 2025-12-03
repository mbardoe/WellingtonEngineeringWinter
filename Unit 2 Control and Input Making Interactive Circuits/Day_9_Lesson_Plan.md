<!-- command: render -->

# Day 8 Lesson Plan  
**Topics:** Introduction to the Multimeter and Oscilloscope  
**Homework:** None (optional practice measurements encouraged)

---

## Lesson Overview

Students will learn how to use a digital multimeter (DMM) for measuring voltage, resistance, and continuity, and they will be introduced to the oscilloscope as a tool for visualizing electrical signals. Because only one oscilloscope is available, the class will use a demonstration-based approach supplemented with small-group rotations for hands-on multimeter work.

This lesson occurs on the day of the quiz, so the first part of the class covers the quiz, and the second part introduces measurement tools.

---

## Objectives

By the end of this lesson, students will be able to:

1. Safely operate a digital multimeter to measure DC voltage, continuity, and resistance.  
2. Understand the role of an oscilloscope in electronics work.  
3. Interpret basic oscilloscope readings such as amplitude and frequency.  
4. Compare the strengths and limitations of a multimeter versus an oscilloscope.  
5. Begin applying these measurement tools to debug or explore simple microcontroller circuits.

---

## Materials Needed

- One oscilloscope  
- Multiple digital multimeters  
- Banana leads and probe leads  
- Breadboards and simple circuits (LEDs, resistors, buttons, potentiometers, wires)  
- Raspberry Pi Pico 2W boards for generating signals (PWM output for oscilloscope)  
- Whiteboard and markers  

---

## Schedule (60 minutes)

### 1. Opening and Quiz (10–12 minutes)

- Administer the short quiz on PWM, ADC, digital I/O, and pinout knowledge.  
- Students turn in quizzes; instructor briefly transitions to new topic.  
- Introduce the concept of "measurement tools" and why engineers use them.

Transition statement:  
"We have been writing code and connecting circuits, but now we need to measure what is actually happening. Today we learn two essential tools: the multimeter and the oscilloscope."

---

### 2. Introduction to the Multimeter (10 minutes)

Teacher-led walkthrough demonstrating:

- The primary measurement modes:
  - **DC Voltage (V with straight line)**  
  - **Resistance (Ohms symbol)**  
  - **Continuity (speaker symbol)**  
- Proper probe placement (COM and V-Ohm ports).  
- Safe handling and avoiding current-measurement mistakes.  
- How to read measurement ranges and auto-ranging behavior.

Example mini-demo:

- Measure the voltage of a 3.3V pin on the Pico.  
- Measure the resistance of a resistor.  
- Test continuity across a wire or button.  

Students copy a simple reference chart into their notebooks.

---

### 3. Multimeter Hands-On Rotations (15 minutes)

Divide students into small groups of 2–3.

Tasks to complete:

1. **Voltage Measurement:**  
   Measure 3.3V from the Pico or a power rail.

2. **Resistance Measurement:**  
   Verify the value of a resistor from their kits.

3. **Continuity Test:**  
   Check whether a breadboard connection is continuous.

4. **Debug Challenge (Optional if time):**  
   Provide a small circuit with one intentional disconnection.  
   Students must identify the break using continuity mode.

Teacher circulates, confirms correct probe placements, and corrects unsafe meter settings.

---

### 4. Introduction to the Oscilloscope (Demonstration) (15 minutes)

Because only one oscilloscope is available, this part is whole-class.

Demonstration steps:

1. **What an oscilloscope does:**  
   - Shows voltage over time.  
   - Lets you observe waveforms (PWM, signals from sensors, ripple, noise).  
   - Allows real-time debugging your multimeter cannot show.

2. **Basic controls:**  
   - Channel selection and probe attenuation (1x vs 10x).  
   - Vertical scale (volts per division).  
   - Horizontal scale (time per division).  
   - Triggering (what it is, simple use case: stable waveform).

3. **Demo signal:**  
   Use a Pico PWM pin to generate a square wave:
   ```python
   from machine import Pin, PWM
   p = PWM(Pin(15))
   p.freq(500)
   p.duty_u16(32768)
   ```
   Show on screen:  
   - Square wave shape  
   - Amplitude ($\approx$ 3.3 V)  
   - Frequency (500 Hz)  
   - Duty cycle concept visually  

4. **Compare to a multimeter:**  
   - Multimeter would simply read an average voltage.  
   - Oscilloscope shows the full shape and frequency.  
   - Scope captures fast-changing signals the DMM cannot show.

Encourage students to ask:  
"What do you notice? What do you wonder about this waveform?"

---

### 5. Optional Student Interaction with the Oscilloscope (If time allows) (5 minutes)

Invite 2–3 students to adjust settings:  
- Change time base  
- Change volts/div  
- Adjust trigger level  

The rest of the class observes how the display changes.

---

## Closing (3 minutes)

- Reinforce that multimeters are for **static or slow measurements**, and oscilloscopes are for **waveforms, timing, and fast signals**.  
- Encourage students to practice using the multimeter during future project work time.  
- No homework assigned (quiz completed in class), but students may optionally practice measurements at home if they have access to equipment.

---

## Notes for Instructor

- Use simple circuits. Avoid exposing students to risky current measurements.  
- Consider photographing the oscilloscope waveform to post on Canvas for review.  
- Next class (Day 9) can involve applying measurement tools to debug student projects.

