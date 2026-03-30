## 🏭 PLC Ladder Logic – Timer & Counter Control System
# 📌 Overview
This project demonstrates a ladder logic system designed using:
- Event-based control (Counter)
- Time-based control (Timer)
- Conditional logic (Comparison blocks)
- closed loop system using branches contact (OR)
The system simulates a control process involving alarms and pump activation based on user input and timing conditions and alos based on feedback.

## Logic Breakdown
# 1. Window Alarm
Behavior:
The window triggers the alarm only when it is open
Explanation:
The contact is configured such that:
When the window is OPEN the alarm turns ON
When the window is CLOSED the alarm remains OFF.

Point: This mimics a basic intrusion detection system

# 2. Doorbell Alarm (Reset + One-Shot Behavior)
Behavior:
The doorbell uses a reset (R) with normally open contact
It only reacts to the initial press, not continuous holding
Explanation:
When the doorbell is pressed:
It sends a single reset signal to alarm2
Even if:
The button is held down
Or stays ON
- It will only trigger once
- This is similar to:
   MOMENTARY PUSH BUTTON

# 3. Start Button → Counter (Count Up)
Behavior:
The start button increments a counter each time it is pressed
Explanation:
Each press increases:
ACC (Accumulated value)
The counter has:
PRE (Preset value) = 3

# 4. Counter Comparison → Counter Pump
Behavior:
The pump turns ON only after 3 button presses
Logic:
Plain text
ACC == PRE
Explanation:
When accumulated count reaches 3:
Condition becomes TRUE
counter pump is activated
👉 This ensures:
The system does not respond until a specific number of events occurs
🔹 5. Start Button → On-Delay Timer
Behavior:
The timer starts counting immediately when the start button is pressed
🔹 Timer Parameters
ACC → Current elapsed time
PRE → Set delay (3 seconds)
🔹 6. Timer Comparison → Timer Pump
Behavior:
The pump turns ON only after a 3-second delay
Logic:
Plain text
timer.ACC >= timer.PRE
Explanation:
Timer starts counting when triggered
Once:
Elapsed time ≥ 3 seconds
Condition becomes TRUE
👉 timer pump turns ON
🔄 System Behavior Summary
🟢 Flow:
Window opens → Alarm turns ON
Doorbell pressed → Alarm2 resets (only once)
Start button pressed repeatedly:
After 3 presses → Counter pump ON
Start button also triggers timer:
After 3 seconds → Timer pump ON
🧠 Key Concepts Demonstrated
Event counting (CTU)
Time delay control (TON)
One-shot / edge-trigger logic
Conditional comparison (==, >=)
Output control based on system state
🔐 Cybersecurity Insight
This exercise reinforces an important concept:
You can only detect abnormal behavior if you understand normal system logic
Examples:
Unexpected rapid counter increments → possible malicious automation
Timer bypass → process manipulation
Unauthorized reset signals → alarm suppression
✅ Conclusion
This project helped translate:
Basic logic gate knowledge (AND, OR, NOT)
➡️ Into real-world industrial control behavior
It also highlights how control logic plays a critical role in both:
Automation engineering
Industrial cybersecurity

This exact format...remove the 'n , form it well and I want you to give each one a title...and make it in a way I can copy it...you understand shey? Like you can give the title and put the explanation under it...not use the exact explanation in the one above
