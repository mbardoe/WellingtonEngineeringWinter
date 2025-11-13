<!-- command: render -->

# Lesson Plan – Day 2  
**Course:** Engineering: Electronics and Computer Programming  
**Duration:** 45 minutes  
**Topic:** GitHub Workflow and Introduction to Electricity  

---

## Objectives

By the end of this lesson, students will:
1. Successfully **clone** their repository from GitHub Classroom.  
2. Make a small edit, **commit**, and **push** it back to GitHub.  
3. Demonstrate understanding of key Git and GitHub terms.  
4. Explain the basic relationship between **voltage**, **current**, and **resistance** using Ohm’s Law and the **water analogy**.

---

## Materials

- Laptops with GitHub access and Thonny installed  
- Each student’s GitHub Classroom repository link  
- Projector for demonstrations  
- Breadboard, resistors, LED, power supply (for demonstration only)  
- Whiteboard and markers  

---

## Vocabulary for the Day

**Git/GitHub Terms:** repository, branch, commit, push, pull, merge, clone  
**Electricity Terms:** voltage, current, resistance, Ohm’s Law  

---

## Lesson Outline

### 1. Opening (5 minutes)
- Quick review of yesterday’s setup: Thonny, GitHub account, and Pico.  
- Ask: “Who was able to run code or push to GitHub last class?”  
- Introduce today’s two goals:
  1. Learn to use GitHub Classroom for your projects.  
  2. Begin understanding how electricity flows and how Ohm’s Law describes that flow.

---

### 2. GitHub Classroom Setup (10 minutes)
1. Students open the GitHub Classroom invitation link provided for their next assignment.  
2. Demonstrate on projector:
   - How to accept an assignment (GitHub automatically creates a repository).  
   - How to find the **HTTPS clone URL**.  
3. In their terminal or VS Code/Thonny Git tools:
   ```bash
   git clone https://github.com/organization/repo-name.git
   ```
4. Students confirm the folder appears locally.

---

### 3. Practice Commit and Push (10 minutes)
1. Students open the cloned folder, add a small file (e.g., `day2_practice.txt`) and write:
   ```
   My first commit from class.
   ```
2. Demonstrate the workflow:
   ```bash
   git add .
   git commit -m "Day 2 practice commit"
   git push
   ```
3. Students verify changes appear on GitHub.  
4. Emphasize how **commits** create snapshots of progress.

---

### 4. Short Git Vocabulary Quiz (5 minutes)
Students complete a quick in-class written or digital quiz.

**Example Questions:**
1. What is a *repository*?  
2. What does *commit* mean?  
3. What command uploads your changes to GitHub?  
4. What does it mean to *clone* a repository?  
5. What does *merge* do?  
6. What is *pulling* from a repo used for?

(Answers will be discussed immediately after.)

---

### 5. Introduction to Electricity and Ohm’s Law (12 minutes)
**Demonstration:**
- Draw a simple water system diagram: tank (voltage), pipe (wire), valve (resistor), flow (current).
- Use analogies:
  - **Voltage** = water pressure (potential energy pushing charges).  
  - **Current** = flow rate (how much charge moves per second).  
  - **Resistance** = size of the pipe (how much it resists flow).  
- Explain **Ohm’s Law**:  
$$
  V = I \times R
$$
  “The pressure (voltage) equals flow (current) times restriction (resistance).”
- Discuss trade-offs:
  - Restricting flow increases the energy each unit of charge releases (more ‘work’), but total flow decreases.  
  - High flow with low resistance produces less work per unit but more total energy movement.

**Optional Demonstration:**  
Show an LED circuit with a resistor and explain that if resistance is too low, current is too high and the LED burns out.

---

### 6. Closing and Reflection (3 minutes)
- Ask students to summarize:
  - One Git command they used today.
  - One concept they learned about electricity.
- Preview next class: building a working LED circuit and applying Ohm’s Law to measure voltage and current.

---

## Assessment
- Completion of GitHub clone, commit, and push.  
- Short vocabulary quiz on Git terms.  
- Informal observation of student understanding during the Ohm’s Law discussion.

---

## Homework
1. Review notes on Ohm’s Law and the water analogy.  
2. Complete a short written exercise:
   - Describe how changing resistance affects current and voltage in a circuit.
3. Confirm that their local GitHub repository is working for next class.
