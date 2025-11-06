---
updated_at: 2025-11-06T13:19:34.173+05:30
edited_seconds: 30
---
#APP 
Perfect — let’s go step by step for your *Week 11 Tutorial Assignment (17-10-2025)* on *Parallel and Network Programming Paradigms*.
I’ll give you *answers, explanations, and full executable Python programs* for each question 👇

---

## 🧠 *Parallel Programming Paradigm*

---

### *Q1. Shared Scoreboard Problem*

*Question:*
In a multiplayer game, several threads update a shared scoreboard simultaneously.
Scores occasionally appear incorrect. What mechanism can ensure the scoreboard always reflects correct scores?

---

### ✅ *Answer:*

The issue arises because *multiple threads* are *updating the same shared variable* (the scoreboard) *at the same time* — causing *race conditions*.

To ensure correctness, use *thread synchronization mechanisms* such as a *Lock (Mutual Exclusion Lock)* from Python’s threading module.

---

### *Example Code:*
```python
import threading

# Shared scoreboard
scoreboard = {"player1": 0, "player2": 0}
lock = threading.Lock()

def update_score(player, points):
    global scoreboard
    with lock:  # Critical section
        current = scoreboard[player]
        scoreboard[player] = current + points
        print(f"{player} scored {points}, total: {scoreboard[player]}")

threads = []

# Simulate multiple updates
for i in range(5):
    t1 = threading.Thread(target=update_score, args=("player1", 10))
    t2 = threading.Thread(target=update_score, args=("player2", 15))
    threads.extend([t1, t2])
    t1.start()
    t2.start()

for t in threads:
    t.join()

print("\nFinal Scoreboard:", scoreboard)


---

### 🧩 *Explanation:*

* Without locks, two threads could read and write scoreboard at the same time → *inconsistent results*.
* Using lock.acquire() or with lock: ensures *only one thread* updates the scoreboard at a time.
* This guarantees *data integrity* and prevents *race conditions*.

---

### *Q2. Weather Simulation using Multiprocessing*

---

#### ✅ *Task:*

* 4 independent processes (computers)
* Each generates *5 random temperatures*
* Combine in the *master process* to compute the *average temperature*

---

### *Python Code:*

python
import multiprocessing
import random

def generate_temperatures(region_id, result_dict):
    # Each process generates 5 random temperatures
    temps = [random.uniform(20, 40) for _ in range(5)]
    result_dict[region_id] = temps
    print(f"Region {region_id} temperatures: {temps}")

if __name__ == "__main__":
    manager = multiprocessing.Manager()
    result_dict = manager.dict()

    processes = []
    for i in range(4):
        p = multiprocessing.Process(target=generate_temperatures, args=(i, result_dict))
        processes.append(p)
        p.start()

    for p in processes:
        p.join()

    # Combine results in master process
    all_temps = [temp for temps in result_dict.values() for temp in temps]
    average_temp = sum(all_temps) / len(all_temps)
    print("\nAll temperatures:", all_temps)
    print(f"Average temperature: {average_temp:.2f} °C")

```

---

### 🧩 *Explanation:*

* Each process runs *independently, with **its own memory space* (unlike threads).
  This is why they *cannot share global variables directly*.
* A **Manager().dict()** is used to safely share data between processes.
* Data is exchanged via *Inter-Process Communication (IPC)* — the Manager creates a shared object accessible across processes.
* Finally, the master process collects and averages all results.

---

## 🌐 *Network Programming Paradigm*

---

### *Q1. TCP Client-Server File Transfer*

---

### **Server (save as tcp_server.py):**

python
import socket
import threading

def handle_client(conn, addr):
    print(f"Connected to {addr}")
    with open("received_file.txt", "wb") as f:
        while True:
            data = conn.recv(1024)
            if not data:
                break
            f.write(data)
    print("File received successfully.")
    conn.close()

def start_server():
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server.bind(("127.0.0.1", 5000))
    server.listen(5)
    print("Server listening on port 5000...")
    
    while True:
        conn, addr = server.accept()
        thread = threading.Thread(target=handle_client, args=(conn, addr))
        thread.start()

if __name__ == "__main__":
    start_server()


---

### **Client (save as tcp_client.py):**

python
import socket
import threading

def send_file():
    client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client.connect(("127.0.0.1", 5000))
    filename = "sample.txt"

    with open(filename, "rb") as f:
        data = f.read(1024)
        while data:
            client.send(data)
            data = f.read(1024)
    client.close()
    print("File sent successfully.")

if __name__ == "__main__":
    thread = threading.Thread(target=send_file)
    thread.start()


---

### 🧩 *Explanation:*

* The *server* runs first, listening on port 5000.
* The *client* connects and sends a file (sample.txt).
* The *server saves* it as received_file.txt.
* Both use *threads* to allow multiple clients or parallel execution.

---

### *Q2. UDP Client-Server Message Exchange*

---

### *Server (udp_server.py):*

python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
server.bind(("127.0.0.1", 6000))
print("UDP Server listening on port 6000...")

while True:
    data, addr = server.recvfrom(1024)
    print(f"Received from {addr}: {data.decode()}")
    server.sendto(b"Message received by server", addr)


---

### *Client (udp_client.py):*

python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

message = "Hello Server, this is UDP Client!"
client.sendto(message.encode(), ("127.0.0.1", 6000))

data, addr = client.recvfrom(1024)
print("Server replied:", data.decode())
client.close()


---

### 🧩 *Explanation:*

* UDP is *connectionless, so there’s **no handshake* like TCP.
* The *client sends a datagram, and the **server responds*.
* It’s *faster, but **less reliable* — no guarantee of delivery or order.

---

## ✅ *Summary Table*

| Type                 | Concept                 | Mechanism Used  | Python Module         |
| -------------------- | ----------------------- | --------------- | --------------------- |
| Parallel (Threads)   | Shared scoreboard       | Lock            | threading           |
| Parallel (Processes) | Independent computation | IPC via Manager | multiprocessing     |
| Network (TCP)        | Reliable file transfer  | Stream socket   | socket, threading |
| Network (UDP)        | Fast message exchange   | Datagram socket | socket              |

---

Would you like me to put *all these programs with explanations* into a *single formatted PDF (assignment-ready)*?
I can generate that for you instantly.