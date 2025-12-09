
# **1. DATA GATE (DGATE)**

### **Definition**

A **Data Gate** is a controlled buffer (usually a tri-state buffer) used to place the contents of a register onto a common bus **only when enabled** by a control signal.

### **Purpose**

* It prevents more than one register from driving the bus at the same time.
* Allows **one register at a time** to place its data onto the common bus.

### **Working**

If a register `R1` wants to send data to the bus, its Data Gate control signal (e.g., `R1out`) is activated:

```
R1out = 1 → R1 → (Data Gate) → Bus
R1out = 0 → Data Gate blocks output → Bus unaffected
```

### **Key Point**

✔ A Data Gate allows **only one register** to transmit data to the bus at a time.

---

# **2. DATA MERGE GATE (DMERGE)**

### **Definition**

A **Data Merge Gate** is a controlled gate that allows selected data from the **common bus to enter a specific register** when enabled.

### **Purpose**

* Controls which register receives the data from the bus.
* Ensures that multiple registers do not simultaneously load data from the bus unless required.

### **Working**

If register `R2` wants to load data from the bus, its Data Merge Gate control signal (e.g., `R2in`) is activated:

```
Bus → (Data Merge Gate) → R2
R2in = 1 → data is written into R2  
R2in = 0 → register R2 does not load data
```

### **Key Point**

✔ A Data Merge Gate allows **only selected registers** to load data from the common bus.

---

# **3. USE IN MULTIPLEXED REGISTER TRANSFERS**

In a **multiplexed bus organization**, multiple registers share a single bus for data movement.
Thus, to avoid conflicts:

* **Data Gates** control *which register sends data to the bus*
* **Data Merge Gates** control *which register receives data from the bus*

### **Example Transfer: R1 → R2**

This is implemented using the bus:

### **Step 1: Send R1 to bus**

```
Activate Data Gate of R1:
R1out = 1
```

This passes R1’s contents onto the common bus.

### **Step 2: Receive data from bus into R2**

```
Activate Data Merge Gate of R2:
R2in = 1
```

This loads the bus data into R2.

### **So the transfer happens as:**

```
R1out = 1 (Data Gate ON)
R2in  = 1 (Data Merge Gate ON)
```

### **Why both gates needed?**

* **Data Gate** → ensures *only R1* places data on the bus.
* **Data Merge Gate** → ensures *only R2* loads the data into itself.

Thus, multiplexed bus systems use Data Gates and Data Merge Gates to safely and efficiently coordinate register-to-register transfers.

---

# **4. Summary (Perfect for 10-mark answers)**

| Component           | Purpose                                      | Direction      | Role in Multiplexed Transfers      |
| ------------------- | -------------------------------------------- | -------------- | ---------------------------------- |
| **Data Gate**       | Allows a register to put its data on the bus | Register → Bus | Selects the *source register*      |
| **Data Merge Gate** | Allows a register to load data from bus      | Bus → Register | Selects the *destination register* |

✔ Prevents bus conflicts
✔ Enables controlled data movement
✔ Essential in any bus-based CPU architecture

---


