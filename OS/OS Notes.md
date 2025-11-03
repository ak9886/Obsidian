---
updated_at: 2025-10-28T11:00:48.004+05:30
edited_seconds: 30
---
#OS 


## 🧠 DISK SCHEDULING ALGORITHMS

### 1️⃣ FCFS (First Come First Serve)

**Concept:**  
Requests are served in the order they arrive. No reordering.

**Given:**

- Head starts at 50
    
- Requests: 82, 170, 43, 140, 24, 16, 190
    
- Range: 0–199
    

**Order of Service:**  
50 → 82 → 170 → 43 → 140 → 24 → 16 → 190

**Total Head Movement:**  
= |82−50| + |170−82| + |43−170| + |140−43| + |24−140| + |16−24| + |190−16|  
= 32 + 88 + 127 + 97 + 116 + 8 + 174 = **642 tracks**

🟩 **Pros:** Simple to implement  
🟥 **Cons:** Very high seek time (inefficient for large queues)

---

### 2️⃣ SSTF (Shortest Seek Time First)

**Concept:**  
The request closest to the current head position is served next → minimizes seek time.

**Given:**

- Head = 50
    
- Queue: 82, 170, 43, 140, 24, 16, 190
    

**Step-by-Step:**

- Closest to 50 → 43
    
- Closest to 43 → 24
    
- Closest to 24 → 16
    
- Closest to 16 → 82
    
- Closest to 82 → 140
    
- Closest to 140 → 170
    
- Closest to 170 → 190
    

**Order:** 50 → 43 → 24 → 16 → 82 → 140 → 170 → 190  
**Total Head Movement:**  
= |50−43| + |43−24| + |24−16| + |82−16| + |140−82| + |170−140| + |190−170|  
= 7 + 19 + 8 + 66 + 58 + 30 + 20 = **208 tracks**

🟩 **Pros:** Less movement than FCFS  
🟥 **Cons:** Can cause _starvation_ (some far requests may never get served)

---

### 3️⃣ SCAN (Elevator Algorithm)

**Concept:**  
The head moves in one direction (e.g. towards higher cylinders), serving all requests, and reverses only when it hits the end (0 or 199).

**Given:**

- Head = 50
    
- Requests: 68, 173, 41, 102, 15, 134, 55, 67, 90, 182
    
- Sorted: 15, 41, 55, 67, 68, 90, 102, 134, 173, 182
    

**Assume:** Head moves towards 199 first.

**Order:**  
50 → 55 → 67 → 68 → 90 → 102 → 134 → 173 → 182 → **199** → 41 → 15

**Total Head Movement:**  
= (199−50) + (199−15) = 149 + 184 = **333 tracks**

🟩 **Pros:** Fair – every request eventually gets served  
🟥 **Cons:** Longer seek time due to full end traversal

---

### 4️⃣ LOOK Algorithm

**Concept:**  
Like SCAN, but the head _doesn’t go to the end_ of the disk unless a request exists there. It stops at the last request in each direction.

**Order:**  
50 → 55 → 67 → 68 → 90 → 102 → 134 → 173 → 182 → 41 → 15

**Total Head Movement:**  
= (182−50) + (182−15) = 132 + 167 = **299 tracks**

🟩 **Pros:** Faster than SCAN (avoids unnecessary travel)  
🟥 **Cons:** Still biased toward the direction it initially moves

---

### 🔸 SCAN vs LOOK Comparison

|Algorithm|Total Movement (tracks)|Efficiency|
|---|---|---|
|SCAN|333|Lower|
|LOOK|299|Better|

LOOK saves **34 tracks**, so it’s **more efficient**.

---

## 🧩 PAGE REPLACEMENT ALGORITHMS

### 1️⃣ FIFO (First In First Out)

**Concept:**  
Oldest loaded page is replaced first.

**Example:**  
Reference string: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2  
Frames = 3

**Fault Sequence:**  
F F F F – F F F F F F – –  
✅ Total Page Faults = **10**  
✅ Hit Ratio = 3/13 = **23.08%**  
✅ Miss Ratio = 76.92%

🟩 **Pros:** Simple to implement  
🟥 **Cons:** Can cause **Belady’s anomaly** (more frames → more faults)

---

### 2️⃣ Belady’s Anomaly Example

**Reference:** 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5  
Frames = 3

**Total Faults:** 9  
**Explanation:**  
Adding more frames doesn’t always reduce faults — anomaly occurs due to FIFO not considering future references.

---

### 🔹 Key Metrics

- **Page Fault Rate** = (Page Faults ÷ Total References)
    
- **Hit Rate** = 1 − Page Fault Rate
    
- **Belady’s Anomaly** = anomaly in FIFO where increasing frames causes _more_ faults
    

---

### 🔸 Quick Comparison Summary

|Algorithm|Approach|Advantage|Disadvantage|
|---|---|---|---|
|FCFS|Sequential|Easy|Very slow|
|SSTF|Closest request|Low seek time|Starvation possible|
|SCAN|Moves to end, then back|Fair|Wastes time at ends|
|LOOK|Moves to last request only|Efficient|Biased|
|FIFO|First-in-first-out pages|Simple|Belady’s anomaly|

---

### **3 Thought-Provoking Exam Questions**

**Q1:** Why does LOOK outperform SCAN even though both move in the same general pattern?  
**Q2:** How does SSTF risk starvation, and how could it be prevented?  
**Q3:** In page replacement, why can FIFO produce worse results when frame size increases?

---

Would you like me to create **diagram-style summaries** (head movement graphs + page replacement tables) for each algorithm? It helps you revise 10× faster visually before the exam.