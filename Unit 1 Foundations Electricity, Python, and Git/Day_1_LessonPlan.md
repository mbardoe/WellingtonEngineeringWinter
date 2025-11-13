<!-- command: render -->

# Lesson Plan – Day 1

**Course:** Engineering: Electronics and Computer Programming  
**Duration:** 70 minutes  
**Unit:** Introduction to Programming and Electronics  
**Topic:** Getting Set Up – Python, GitHub, and the Raspberry Pi Pico W  

---

## Objectives

By the end of class, students will:
1. Create and verify a **GitHub account**.  
2. Install **Thonny** and verify Python interpreter setup.  
3. Set up the **Raspberry Pi Pico W** for MicroPython.  
4. Understand the purpose of **Git, GitHub**, and **Python** in the course.  
5. Learn and define foundational **vocabulary** for programming and electronics.

---

## Materials

- Student laptops (with Wi-Fi)
- Raspberry Pi Pico W + USB cable
- Thonny installer (pre-downloaded link)
- Projector and instructor demo setup
- GitHub signup link: [https://github.com/](https://github.com/)
- Vocabulary handout (below)

---

## Key Vocabulary

Repository (repo), commit, push, clone, branch, merge, Python, variable, string, integer, loop, logic, boolean, microcontroller, firmware, REPL, IDE, script, upload, hardware, software, voltage, current, resistor, LED.

---

## Lesson Outline

### **Opening (10 min)**
- Welcome and course overview.
- Explain: *“This course connects programming and electronics — by the end, you’ll be writing Python code that controls physical devices.”*
- Brief discussion: What do students already know about Python or circuits?

### **Part 1: GitHub Setup (15 min)**
1. Walk students through creating a **GitHub account**.  
2. Demonstrate how code and documentation will be stored there.  
3. Students create their first **repository** (name it `engineering-class` or similar).  
4. Explain the concept of a **commit** as a “snapshot” of progress.

> Teacher Tip: Emphasize that version control = *"undo for everything."*

### **Part 2: Thonny and Python Setup (20 min)**
1. Guide students to download Thonny from [https://thonny.org](https://thonny.org).  
2. Open Thonny, identify the console, and run:
   ```python
   print("Hello, world!")
    ```
3. Discuss:
    
- What is a **program**?
        
- What does the `print()` function do?
        
- How does the computer read and execute code?
        

### **Part 3: Raspberry Pi Pico Setup (15 min)**

1. Demonstrate how to:
    
    - Hold the BOOTSEL button while connecting via USB.
        
    - Copy the **MicroPython UF2** file to the Pico W (link from Raspberry Pi documentation).
        
2. In Thonny, go to:
    
    - **Tools → Options → Interpreter → MicroPython (Raspberry Pi Pico)**
        
    - Select the correct port and test REPL with:
        
        `print("Pico is working!")`
        
3. Confirm that students can run simple code on the Pico.
    

### **Part 4: Vocabulary + Reflection (10 min)**

- Hand out vocabulary list.
    
- Ask students to pair up and choose 5 words they feel confident explaining.
    
- Quick share-out or written reflection: “What feels most exciting? Most confusing?”
    

---

## Assessment

- Informal observation: students successfully create GitHub accounts, run Thonny, and connect Pico.
    
- Exit Ticket: Students define 3 key terms (from Git/GitHub, Python, and electronics) in their own words.
    

---

- Complete setup checklist (see below).
    
- Write a short reflection on what Git and GitHub are for.
    
- Define 10 key vocabulary words from the list.