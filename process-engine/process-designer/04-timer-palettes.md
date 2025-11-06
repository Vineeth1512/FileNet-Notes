# ⏰ Timer Palette in IBM FileNet Process Designer (BPM)

The **Timer Palette** in IBM FileNet Process Designer provides special steps that manage **time-based control** within a workflow.  

These steps help you **pause, resume, suspend, or end** parts of a process after specific time intervals — perfect for implementing **deadlines, reminders, and timeouts**.

---

## 🧩 What Timer Steps Do

Timer steps allow you to:
- Delay process actions until a specific date or time  
- Handle timeouts automatically  
- Suspend or resume processes after waiting  
- End timers when no longer needed  

Timers make workflows **time-aware** and ensure actions occur **on schedule**.

---

## ⏱️ Common Timer Steps

### 1. **BeginTimer**

**Purpose:**  
Starts or **activates a timer** for the workflow or a specific step.

**What it does:**  
- Marks the start of a timer interval  
- The timer counts until a condition or time limit is reached  
- Often used before a **Suspend** or **Wait** action

**Example:**  
🕐 Begin a timer when waiting for customer feedback — “Reply within 48 hours.”

**In short:**  
- Starts timing countdown  
- Defines beginning of a timed section  

---

### 2. **EndTimer**

**Purpose:**  
Marks the **end** of a specific timer that was started earlier.

**What it does:**  
- Stops a single running timer  
- Used when the timed activity completes successfully before expiration  

**Example:**  
✅ Once customer feedback is received, use **EndTimer** to stop the “Response Timer”.

**In short:**  
- Stops one running timer  
- Indicates successful completion  

---

### 3. **EndAllTimer**

**Purpose:**  
Stops **all active timers** in the workflow.

**What it does:**  
- Cancels every timer that was started  
- Useful when you want to end all timing events together (for example, process completed early)

**Example:**  
🛑 If loan is approved early, **EndAllTimer** stops all reminder or escalation timers.

**In short:**  
- Ends all timers in the process  
- Used for cleanup and control  

---

### 4. **ExpirationTimeTimer**

**Purpose:**  
Defines the **expiration or deadline time** for a process or activity.

**What it does:**  
- Sets a specific date/time when the timer expires  
- When expired, a defined action or path executes (like escalation)

**Example:**  
⏳ A **ExpirationTimeTimer** triggers an escalation after **3 days** if approval is not completed.

**In short:**  
- Sets a deadline  
- Triggers an action on timeout  

---

### 5. **ResumeDeadlineTimer**

**Purpose:**  
Resumes a process when a **deadline** has passed.

**What it does:**  
- Wakes up a suspended workflow when the set time limit is reached  
- Can continue process execution automatically

**Example:**  
🕒 After waiting for 24 hours, **ResumeDeadlineTimer** resumes the process to send a reminder email.

**In short:**  
- Resumes process after a set time  
- Automatically wakes up workflow  

---

### 6. **ResumeTimer**

**Purpose:**  
Used to **manually or programmatically resume** a suspended process before its deadline.

**What it does:**  
- Reactivates the workflow  
- Can be triggered by another step or event (like user input)

**Example:**  
🔔 When a user submits required data early, **ResumeTimer** resumes the workflow immediately.

**In short:**  
- Manually resumes workflow  
- Used for early resume or user-triggered actions  

---

### 7. **SuspendDeadlineTimer**

**Purpose:**  
Suspends the workflow **until a specified deadline**.

**What it does:**  
- Temporarily pauses process execution  
- Process remains inactive until deadline or resume event occurs  

**Example:**  
🛌 **SuspendDeadlineTimer** pauses a process until **next Monday 9 AM** for scheduled maintenance.

**In short:**  
- Suspends until given deadline  
- Automatically resumes later  

---

### 8. **SuspendTimer**

**Purpose:**  
Temporarily **pauses** workflow execution for a defined duration or condition.

**What it does:**  
- Suspends workflow  
- Keeps state saved in Process Engine  
- Waits until resumed by **ResumeTimer** or a condition  

**Example:**  
⏸️ **SuspendTimer** pauses a process for **48 hours** waiting for payment confirmation.

**In short:**  
- Pauses process  
- Waits until resumed manually or automatically  

---

## 🧠 Summary Table

| Step Name | Purpose | Behavior | Example |
|------------|----------|-----------|----------|
| **BeginTimer** | Start a timer | Begins timing countdown | Start 48-hour response timer |
| **EndTimer** | Stop one timer | Ends a specific timer | Stop response timer after reply |
| **EndAllTimer** | Stop all timers | Ends every active timer | Cancel all reminders |
| **ExpirationTimeTimer** | Define deadline | Triggers event after time expires | Escalate after 3 days |
| **ResumeDeadlineTimer** | Resume on deadline | Restarts after time limit | Resume to send reminder |
| **ResumeTimer** | Resume process | Reactivate suspended process | Resume when user responds |
| **SuspendDeadlineTimer** | Suspend till deadline | Pauses until set time/date | Wait until Monday 9 AM |
| **SuspendTimer** | Suspend temporarily | Pauses workflow until resumed | Wait 48 hours for payment |

---

## 💡 Key Notes

- Timers make workflows **time-sensitive** and **automated**.  
- Always pair `BeginTimer` with `EndTimer` for clarity.  
- Use **EndAllTimer** when you want to clear all running timers.  
- Avoid overlapping multiple timers — it can complicate process control.  
- Ideal for **reminders, deadlines, SLAs,** and **auto-escalations**.

---

## 🏁 Tip to Remember

> **BeginTimer / EndTimer** → Start & Stop timing  
> **EndAllTimer** → Stop all timers  
> **Suspend / Resume** → Pause and continue workflow  
> **DeadlineTimers** → Handle time-based conditions and SLAs
