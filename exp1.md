Got it, Professor 👨‍🏫 — now I’ll give you **FULL DETAILED Experiment 1 (ALL 3 PARTS)** exactly how you should:

👉 **Understand + Write in exam + Execute (where needed)**
👉 Clean, structured, and scoring format

---

# 📄 🧪 EXPERIMENT 1 — COMPLETE (ALL PARTS)

---

# 🟢 **PART A — INSTALL UBUNTU USING VMWARE**

---

## 🎯 **Aim**

To install Ubuntu Linux OS on a virtual machine using VMware Workstation Pro. 

---

## 🧠 **Theory (Write 4–5 lines)**

A virtual machine (VM) is a software-based system that runs an operating system on top of another OS.

VMware Workstation allows users to create and run multiple operating systems on a single machine.

Ubuntu is a Linux-based open-source operating system widely used for development and big data environments. 

---

## ⚙️ **Procedure**

---

### 🔹 Step 1: Launch VMware

* Open VMware Workstation Pro
* Click **Create New Virtual Machine**

---

### 🔹 Step 2: Choose Configuration

* Select **Typical (Recommended)**
* Click Next

---

### 🔹 Step 3: Select ISO File

* Choose **Installer disc image (ISO)**
* Select Ubuntu ISO file

---

### 🔹 Step 4: Enter Details

* Username → MTIS
* Password → 123456

---

### 🔹 Step 5: Name VM

* Name → Ubuntu 64-bit
* Choose location

---

### 🔹 Step 6: Disk Configuration

* Disk size → 20 GB
* Select **Split disk into multiple files**

---

### 🔹 Step 7: Finish Setup

* Click Finish
* Installation starts automatically

---

### 🔹 Step 8: Login

* Enter username and password
* Ubuntu desktop opens

---

## 🧾 **Result**

Ubuntu OS was successfully installed on VMware.

---

# 🔵 **PART B — SINGLE NODE HADOOP (MAIN PRACTICAL)**

---

## 🎯 **Aim**

To install and configure a Single Node Hadoop Cluster in pseudo-distributed mode. 

---

## 🧠 **Theory (Write 5–6 lines)**

Hadoop is an open-source framework used to store and process large datasets.

HDFS is the storage system of Hadoop.

* NameNode → manages metadata
* DataNode → stores data

In a single-node cluster, both run on the same system. 

---

## ⚙️ **Procedure**

---

### 🔴 Step 1: Install Java

```bash
sudo apt update
sudo apt install openjdk-8-jdk -y
java -version
```

---

### 🔴 Step 2: Set JAVA_HOME

```bash
nano ~/.bashrc
```

Add:

```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin
```

Apply:

```bash
source ~/.bashrc
```

---

### 🔴 Step 3: Install Hadoop

```bash
wget https://downloads.apache.org/hadoop/common/hadoop-3.3.6/hadoop-3.3.6.tar.gz
tar -xvzf hadoop-3.3.6.tar.gz
sudo mv hadoop-3.3.6 /usr/local/hadoop
```

---

### 🔴 Step 4: Set Hadoop Path

```bash
nano ~/.bashrc
```

Add:

```bash
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin
```

Apply:

```bash
source ~/.bashrc
```

---

### 🔴 Step 5: Configure Hadoop

```bash
cd $HADOOP_HOME/etc/hadoop
```

#### hadoop-env.sh

```bash
nano hadoop-env.sh
```

Set:

```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
```

---

#### core-site.xml

```xml
<configuration>
  <property>
    <name>fs.defaultFS</name>
    <value>hdfs://localhost:9000</value>
  </property>
</configuration>
```

---

#### hdfs-site.xml

```xml
<configuration>
  <property>
    <name>dfs.replication</name>
    <value>1</value>
  </property>

  <property>
    <name>dfs.namenode.name.dir</name>
    <value>file:/usr/local/hadoop/data/namenode</value>
  </property>

  <property>
    <name>dfs.datanode.data.dir</name>
    <value>file:/usr/local/hadoop/data/datanode</value>
  </property>
</configuration>
```

---

### 🔴 Step 6: Create Directories

```bash
mkdir -p /usr/local/hadoop/data/namenode
mkdir -p /usr/local/hadoop/data/datanode
```

---

### 🔴 Step 7: Format NameNode

```bash
hdfs namenode -format
```

---

### 🔴 Step 8: Start Hadoop

```bash
start-dfs.sh
```

---

### 🔴 Step 9: Verify

```bash
jps
```

Expected:

* NameNode
* DataNode
* SecondaryNameNode

---

### 🔴 Step 10: Check HDFS

```bash
hdfs dfs -ls /
```

---

### 🔴 Step 11: Web UI

👉 [http://localhost:9870](http://localhost:9870)

---

## 🧾 **Result**

Single Node Hadoop Cluster was successfully installed and verified. 

---

# 🔴 **PART C — MULTI NODE HADOOP (THEORY + STEPS)**

---

## 🎯 **Aim**

To configure a Multi Node Hadoop Cluster using master and slave nodes. 

---

## 🧠 **Theory**

In a multi-node cluster:

* Master Node → NameNode
* Slave Nodes → DataNodes

It allows distributed processing across multiple systems. 

---

## ⚙️ **Procedure**

---

### 🔹 Step 1: Install Java (All nodes)

```bash
sudo apt install openjdk-8-jdk -y
```

---

### 🔹 Step 2: Install Hadoop (All nodes)

Same as single node

---

### 🔹 Step 3: Configure SSH

```bash
ssh-keygen -t rsa
ssh-copy-id slave1
ssh-copy-id slave2
```

---

### 🔹 Step 4: Configure core-site.xml

```xml
<configuration>
  <property>
    <name>fs.defaultFS</name>
    <value>hdfs://master:9000</value>
  </property>
</configuration>
```

---

### 🔹 Step 5: Configure hdfs-site.xml

```xml
<configuration>
  <property>
    <name>dfs.replication</name>
    <value>2</value>
  </property>
</configuration>
```

---

### 🔹 Step 6: Configure Workers

```bash
nano workers
```

Add:

```bash
slave1
slave2
```

---

### 🔹 Step 7: Format & Start

```bash
hdfs namenode -format
start-dfs.sh
```

---

### 🔹 Step 8: Verify

```bash
jps
```

---

## 🧾 **Result**

Multi-node Hadoop cluster configured successfully. 

---
