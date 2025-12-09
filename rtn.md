

# **1. RUN Signal — RTN Description**

### **Meaning**

The **RUN** signal determines whether the SRC machine’s control unit continues executing instructions or stops.

### **Formal RTN**

```
if RUN = 1 then
    PC ← PC + 4
    Fetch, Decode, Execute instruction
else
    CPU is halted
```

### **Explanation**

* **RUN = 1 → CPU executes normally**
* **RUN = 0 → CPU stops (HALT state)**
* Usually, the HALT instruction sets RUN = 0.

---

# **2. START Signal — RTN Description**

### **Meaning**

The **START** signal initializes the SRC machine before execution begins.

### **Formal RTN**

```
if START = 1 then
    PC ← 0
    RUN ← 1
```

### **Explanation**

* START resets the PC to the starting address (usually 0).
* It also sets RUN = 1 so the processor begins instruction execution.

---

# **3. Main Memory Operations — RTN Description**

### **There are two main operations:**

1. **Read (Load)**
2. **Write (Store)**

### **(A) Memory Read Operation**

```
MDR ← Memory[MAR]
```

Meaning:

* MAR contains the memory address.
* MDR receives the data stored at that address.

### **(B) Memory Write Operation**

```
Memory[MAR] ← MDR
```

Meaning:

* MDR contains the data to be stored.
* That data is written into the memory location given by MAR.

### **Control Signals**

* Read signal: `READ = 1`
* Write signal: `WRITE = 1`
  Only one of these is active at a time.

So full RTN:

```
if READ = 1 then MDR ← Memory[MAR]
if WRITE = 1 then Memory[MAR] ← MDR
```

---

# **4. STATE of SRC Machine — RTN Description**

The SRC machine uses a **finite-state control unit** with these main states:

1. **FETCH**
2. **DECODE**
3. **EXECUTE**
4. **MEM (optional)**
5. **WRITE-BACK**

### **RTN for each state:**

---

### **(A) FETCH State**

```
MAR ← PC
READ ← 1
IR ← Memory[MAR]
PC ← PC + 4
```

---

### **(B) DECODE State**

```
Decode IR
Identify opcode, registers, immediate fields
```

---

### **(C) EXECUTE State**

Execution depends on instruction type:

Example:

* **ADD R1, R2, R3**

```
ALUout ← R2 + R3
```

---

### **(D) MEMORY State (for load/store)**

#### Load:

```
MAR ← ALUout
READ ← 1
MDR ← Memory[MAR]
```

#### Store:

```
MAR ← ALUout
MDR ← Rsrc
WRITE ← 1
Memory[MAR] ← MDR
```

---

### **(E) WRITE-BACK State**

```
Rdest ← ALUout          ; for arithmetic/logical instructions
Rdest ← MDR             ; for loads
```

---

# **SRC State Transitions (Summary)**

```
START → FETCH → DECODE → EXECUTE → MEM → WRITEBACK → FETCH → ...
```

---

# **Full Summary (Perfect for 10 marks)**

| Component        | RTN Description                        | Purpose                          |
| ---------------- | -------------------------------------- | -------------------------------- |
| **RUN Signal**   | `if RUN = 1 then execute; else halt`   | Controls CPU execution           |
| **START Signal** | `if START = 1 then PC ← 0, RUN ← 1`    | Initializes processor            |
| **Memory Read**  | `MDR ← Memory[MAR]`                    | Load data                        |
| **Memory Write** | `Memory[MAR] ← MDR`                    | Store data                       |
| **SRC States**   | FETCH, DECODE, EXECUTE, MEM, WRITEBACK | Defines entire instruction cycle |

