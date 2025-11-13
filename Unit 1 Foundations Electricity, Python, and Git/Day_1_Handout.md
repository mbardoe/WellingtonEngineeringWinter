<!-- command: render -->
# Day 1 – Getting Started: Python, GitHub, and Your Raspberry Pi Pico W

## What We’re Doing Today
- Setting up your **GitHub account** (your digital engineering notebook).
- Installing **Thonny**, your Python coding environment.
- Flashing and connecting your **Raspberry Pi Pico W**.
- Running your first Python program.

---

## Step 1 – Create a GitHub Account
1. Go to [https://github.com](https://github.com).
2. Click **Sign Up** → use your school email.
3. Choose a simple username (e.g., first-last or initials).
4. Verify your email.
5. Download [https://desktop.github.com/download/](https://desktop.github.com/download/).
5. Create a new repository:
   - Name: `engineering-class`
   - Description: “My Engineering and Computer Programming work.”
   - Set to **Public** for now.
6. Add a simple README file.

**Vocabulary:**
- **Repository (repo):** A folder that stores code and its history online.
- **Commit:** A saved version of your code.
- **Push:** Sending commits to GitHub.

---

## Step 2 – Install Thonny
1. Visit [https://thonny.org](https://thonny.org).
2. Download the version for your system (Windows, macOS, or Linux).
3. Open Thonny.
4. In the console (bottom area), type:
   ```python
   print("Hello, world!")
    ```

You just wrote your first Python program.

## Step 3 – Set Up Your Raspberry Pi Pico W

Hold down the BOOTSEL button and plug the Pico into USB.

It will appear as a drive on your computer.

Copy the MicroPython UF2 file (your teacher will provide the link) onto that drive.

The Pico will reboot automatically.

In Thonny:

Go to Tools → Options → Interpreter

Choose MicroPython (Raspberry Pi Pico)

Select the correct port.

In the REPL, type:


```python

print("Pico is working!")
```

If you see that message, you’re ready to go!

## Step 4 – Vocabulary to Know

|Category	|Key Words|
|-----------|-------|
|Programming	|variable, function, loop, logic, boolean, string, integer|
|Git & GitHub	|repository (repo), commit, push, clone, branch|
|Hardware	|microcontroller, firmware, IDE, script, REPL|
|Electronics	|voltage, current, resistance, LED, resistor|

We’ll revisit and define these in our own words soon.

## Step 5 – Exit Ticket

Before you leave:

* Make sure you can log into GitHub.
* Run your first program in Thonny.
* Connect your Pico successfully.
* Define three vocabulary words of your choice in your notebook.

## Homework

In GitHub Classroom there is an assignment that asks you to demonstrate your proficiency with git and GitHub.