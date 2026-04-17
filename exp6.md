
---

# 🧪 ✅ EXPERIMENT 6 — CLOUD VM (AWS / GCP)

---

# 🎯 1. AIM

> To explore cloud platforms and create a virtual machine using a cloud service provider. 

---

# 🧠 2. UNDERSTAND IN 30 SECONDS

👉 Cloud = using computer over internet
👉 VM = virtual computer (like your laptop, but online)

---

## 🔥 Example:

* You create a computer on cloud
* Connect using terminal
* Run commands

---

# ⚙️ 3. MAIN CONCEPT FLOW

👉 **Sign Up → Create VM → Connect → Test**

---

# 💻 4. WHAT TO WRITE IN EXAM

---

## 🧠 **Theory (Short)**

A Virtual Machine (VM) is an on-demand computing resource in cloud computing that provides processing power without physical hardware.

Cloud platforms like AWS, Azure, and GCP allow users to create and manage VMs easily. 

---

# 🔴 PROCEDURE (AWS EC2 — MOST IMPORTANT)

---

### Step 1: Login

👉 Open AWS Console

---

### Step 2: Go to EC2

👉 Click **Launch Instance**

---

### Step 3: Choose OS

👉 Ubuntu 22.04

---

### Step 4: Choose Instance

👉 t2.micro (Free Tier)

---

### Step 5: Create Key Pair

👉 Download `.pem` file

---

### Step 6: Configure Security

👉 Allow:

* SSH (Port 22)

---

### Step 7: Launch Instance

👉 Click **Launch**

---

### Step 8: Connect

```bash
ssh -i key.pem ubuntu@public-ip
```

---

# 🟢 OPTIONAL (GCP METHOD)

👉 Go to:

* Compute Engine → VM Instances
* Create instance
* Select machine type
* Click Create
* Use SSH

---

# 🔵 TEST (IMPORTANT STEP)

👉 Install something:

```bash
sudo apt update
sudo apt install nginx -y
```

👉 Open browser:

```
http://<public-ip>
```

👉 You will see:
👉 **Welcome to nginx**

---

# 📊 EXPECTED OUTPUT

* VM created
* Connected via SSH
* Nginx installed
* Web page displayed

---

# 🧾 RESULT

> Successfully created and configured a virtual machine using cloud platform and verified its working. 

---

# 🧠 MEMORY TRICK

👉 Just remember:

**Login → Launch → Connect → Install → Test**

---

# 🎯 WHAT WILL HAPPEN IN EXAM

👉 3 possibilities:

### ✅ Case 1: Internet + AWS available

→ You actually create VM

### ⚠️ Case 2: No internet

→ You only write procedure

### 🔥 Case 3: Viva only

→ They ask concept questions

---

# 🧠 IMPORTANT VIVA QUESTIONS

👉 What is VM?
👉 What is cloud computing?
👉 What is EC2?
👉 What is key pair?
👉 What is security group?

---
