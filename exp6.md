
---

# 📄 🧪 EXPERIMENT 6 — CLOUD VIRTUAL MACHINE

---

# 🎯 **Aim**

To study and explore cloud platforms such as AWS, Microsoft Azure, and Google Cloud Platform, and to create and configure a virtual machine using a cloud service provider. 

---

# 🧠 **Theory**

Cloud computing provides on-demand computing resources such as servers, storage, and networking over the internet.

A Virtual Machine (VM) is a software-based computer that runs on cloud infrastructure. It allows users to perform computing tasks without owning physical hardware.

Cloud platforms such as AWS, Azure, and GCP provide scalable and flexible VM services. These services allow users to create, configure, monitor, and deploy applications efficiently.

Advantages of cloud VMs include:

* Scalability
* Cost efficiency
* High availability
* Remote access

---

# ⚙️ **Procedure**

---

# 🔵 **PART A — AMAZON WEB SERVICES (AWS EC2)**

---

### Step 1: Login

Open AWS Management Console and sign in.

---

### Step 2: Navigate

Go to **Services → EC2 (Elastic Compute Cloud)**.

---

### Step 3: Launch Instance

Click on **Launch Instance**.

---

### Step 4: Choose AMI

Select **Ubuntu 22.04 LTS** as the operating system.

---

### Step 5: Choose Instance Type

Select **t2.micro (Free Tier eligible)**.

---

### Step 6: Configure Key Pair

Create a new key pair and download the `.pem` file.

---

### Step 7: Configure Security Group

Allow:

* SSH (Port 22)

---

### Step 8: Launch Instance

Click **Launch Instance**.

---

### Step 9: Connect to Instance

```bash
ssh -i key.pem ubuntu@public-ip
```

---

### Step 10: Test VM

```bash
sudo apt update
```

---

### Output:

Successfully connected to AWS virtual machine.

---

# 🟢 **PART B — GOOGLE CLOUD PLATFORM (GCP)**

---

### Step 1: Login

Open Google Cloud Console.

---

### Step 2: Navigate

Go to **Compute Engine → VM Instances**.

---

### Step 3: Create Instance

Click **Create Instance**.

---

### Step 4: Configure Instance

* Name: gcelab
* Region: any region
* Machine Type: e2-medium
* OS: Debian / Ubuntu
* Disk Size: 10 GB

---

### Step 5: Enable HTTP Traffic

Allow HTTP traffic (port 80).

---

### Step 6: Create Instance

Click **Create**.

---

### Step 7: Connect via SSH

Click **SSH** button.

---

### Step 8: Install NGINX

```bash
sudo apt-get update
sudo apt-get install -y nginx
```

---

### Step 9: Verify

Open browser:

```
http://<external-ip>
```

---

### Output:

```
Welcome to nginx!
```

---

# 🟡 **PART C — MICROSOFT AZURE**

---

### Step 1: Login

Open Azure Portal.

---

### Step 2: Navigate

Go to **Virtual Machines → Create VM**.

---

### Step 3: Configure VM

* OS: Ubuntu
* Size: B1s / Basic
* Username & Password

---

### Step 4: Configure Networking

Allow:

* SSH (Port 22)

---

### Step 5: Create VM

Click **Create**.

---

### Step 6: Connect

```bash
ssh username@public-ip
```

---

### Output:

Successfully connected to Azure virtual machine.

---

# 📊 **Expected Output**

* Virtual machine created
* SSH connection established
* Commands executed successfully
* Web server (NGINX) running

---

# 🧾 **Result**

Cloud platforms such as AWS, Google Cloud Platform, and Microsoft Azure were successfully explored. Virtual machine instances were created and configured, and basic operations were performed successfully. 

---

# 🧠 ⚡ MEMORY TRICK

👉 Remember this flow:

**Login → Create → Configure → Connect → Test**

---
