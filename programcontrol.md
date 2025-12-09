# **PROGRAM-CONTROLLED I/O (10 MARKS)**

Program-controlled I/O is a method in which the **CPU itself controls and manages** all input and output operations **using instructions in a program**.
There is **no interrupt** and **no DMA** used here.

---

# ✅ **Definition**

Program-Controlled I/O is a method of performing input/output operations where the **CPU continuously checks (polls)** the I/O device’s status registers to know whether the device is ready to send or receive data.
The entire I/O process is **handled by the program**, step-by-step.

---

# ✔️ **Key Idea**

* CPU checks **STATUS register** of I/O device.
* A **flag bit** tells whether the device is ready.
* CPU waits (loops) until the flag changes.
* CPU transfers data only when device is ready.

This method is also called **Polling I/O** or **Busy Waiting I/O**.

---

# ⚙️ **Important Flags**

| Flag                          | Meaning                     |
| ----------------------------- | --------------------------- |
| **SIN (Status Input Flag)**   | 1 = input data is available |
| 0 = no input yet              |                             |
| **SOUT (Status Output Flag)** | 1 = output device busy      |
| 0 = output device free        |                             |

---

# ⭐ **Example: INPUT (Reading a character)**

### **Program:**

```
WAITK   TestBit #0, STATUS     ; Check SIN flag (input status)
        Branch = 0 WAITK       ; If SIN = 0 → no data → keep waiting
        Move DATAIN, R0        ; When SIN = 1 → read data into R0
```

### ✔️ **Explanation:**

1. **TestBit** checks SIN bit in STATUS register.
2. If **SIN = 0**, it means **no character is available yet**.

   * CPU goes back to **WAITK** label.
   * This forms an **infinite loop** → CPU keeps checking again and again.
3. When **SIN = 1**, it means **input data is ready**.
4. CPU executes: `Move DATAIN, R0` → Data is moved from **input buffer** to **register R0**.

This is called **busy waiting**, because CPU wastes time checking repeatedly.

---

# ⭐ **Example: OUTPUT (Sending a character)**

### **Program:**

```
WAITD   TestBit #0, STATUS     ; Check SOUT flag (output status)
        Branch = 0 WAITD       ; If SOUT = 1 → device busy → wait
        Move R0, DATAOUT       ; When SOUT = 0 → device ready → send data
```

### ✔️ **Explanation:**

1. Program checks SOUT bit of STATUS register.
2. If **SOUT = 1**, output device is **busy** (cannot accept new data).

   * CPU loops back to WAITD and keeps checking.
3. When **SOUT = 0**, output device is **ready**.
4. CPU executes: `Move R0, DATAOUT` → sends data to the display.

---

# 📌 **Why is it called Program-Controlled I/O?**

Because:

* The **program** decides when to read/write.
* The **program** checks status flags.
* The **program** performs the data transfer.
* The CPU is fully involved in the entire process.

There is **no hardware interrupt**, **no DMA**, only program instructions.

---

# ⭐ **Advantages**

* Very simple to implement.
* No special hardware needed.
* Useful for slow devices and small systems.

---

# ❌ **Disadvantages**

* **CPU time is wasted** (Busy waiting).
* CPU cannot do other tasks while waiting.
* Very inefficient for high-speed I/O devices.
* Reduces overall system performance.

---

# 📝 **10 MARK ANSWER SUMMARY POINTS**

1. Definition of Program-Controlled I/O.
2. Explanation of polling (busy waiting).
3. Role of STATUS register.
4. Meaning of SIN and SOUT flags.
5. Example program for input with explanation.
6. Example program for output with explanation.
7. CPU continuously checks device status.
8. Steps involved in reading data.
9. Steps involved in writing data.
10. Advantages and disadvantages.


