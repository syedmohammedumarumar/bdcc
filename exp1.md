
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

















in lab if you face any issues use this 

---

# 🧪 🔥 EXPERIMENT 1 — FULL PRACTICAL (FRESH SYSTEM)

---

# 🟢 STEP 0: OPEN TERMINAL

👉 Press:

```
Ctrl + Alt + T
```

---

# 🔵 STEP 1: UPDATE SYSTEM

👉 Type:

```bash
sudo apt update
```

👉 Press **Enter**
👉 If asks password → type password (nothing shows) → press **Enter**

---

# 🔵 STEP 2: INSTALL JAVA

```bash
sudo apt install openjdk-8-jdk -y
```

👉 Press Enter
👉 Wait until installation completes

---

### 🔍 CHECK JAVA

```bash
java -version
```

👉 Press Enter
👉 You must see version → OK

---

# 🔵 STEP 3: SET JAVA_HOME

```bash
nano ~/.bashrc
```

👉 Press Enter

👉 Scroll DOWN using ↓ key

👉 Go to LAST LINE

👉 Type:

```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin
```

---

👉 Now SAVE:

* Press **Ctrl + X**
* Press **Y**
* Press **Enter**

---

👉 Apply:

```bash
source ~/.bashrc
```

---

👉 Check:

```bash
echo $JAVA_HOME
```

---

# 🔵 STEP 4: DOWNLOAD HADOOP

```bash
wget https://downloads.apache.org/hadoop/common/hadoop-3.3.6/hadoop-3.3.6.tar.gz
```

👉 Enter

---

```bash
tar -xvzf hadoop-3.3.6.tar.gz
```

👉 Enter

---

```bash
sudo mv hadoop-3.3.6 /usr/local/hadoop
```

👉 Enter

---

# 🔵 STEP 5: SET HADOOP PATH

```bash
nano ~/.bashrc
```

👉 Go to bottom

👉 Add:

```bash
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin
```

---

👉 Save:

* Ctrl + X
* Y
* Enter

---

👉 Apply:

```bash
source ~/.bashrc
```

---

👉 Check:

```bash
hadoop version
```

---

# 🔵 STEP 6: CONFIGURE HADOOP

```bash
cd $HADOOP_HOME/etc/hadoop
```

---

## 🔴 hadoop-env.sh

```bash
nano hadoop-env.sh
```

👉 Find:

```
export JAVA_HOME=
```

👉 Replace with:

```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
```

👉 Save → Ctrl+X → Y → Enter

---

## 🔴 core-site.xml

```bash
nano core-site.xml
```

👉 Delete existing content

👉 Paste:

```xml
<configuration>
  <property>
    <name>fs.defaultFS</name>
    <value>hdfs://localhost:9000</value>
  </property>
</configuration>
```

👉 Save

---

## 🔴 hdfs-site.xml

```bash
nano hdfs-site.xml
```

👉 Paste:

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

👉 Save

---

# 🔵 STEP 7: CREATE DIRECTORIES

```bash
mkdir -p /usr/local/hadoop/data/namenode
mkdir -p /usr/local/hadoop/data/datanode
```

---

# 🔵 STEP 8: FORMAT NAMENODE

```bash
hdfs namenode -format
```

👉 Wait → look for:

```
SUCCESS
```

---

# 🔵 STEP 9: INSTALL SSH (IMPORTANT)

```bash
sudo apt install ssh -y
```

---

# 🔵 STEP 10: SET PASSWORDLESS SSH

```bash
ssh-keygen -t rsa
```

👉 Press Enter 3 times

---

```bash
ssh-copy-id localhost
```

👉 Type password → Enter

---

```bash
ssh localhost
```

👉 If login → type:

```bash
exit
```

---

# 🔵 STEP 11: START HADOOP

```bash
start-dfs.sh
```

---

# 🔵 STEP 12: VERIFY

```bash
jps
```

👉 MUST show:

```
NameNode
DataNode
SecondaryNameNode
```

---

# 🔵 STEP 13: CHECK HDFS

```bash
hdfs dfs -ls /
```

---

# 🔵 STEP 14: WEB UI

👉 Open browser

👉 Type:

```
http://localhost:9870
```

---

# 🎯 DONE ✅

You successfully completed **Experiment 1**

---



# for multinode 

⚠️ I’ll be honest first:
👉 In your lab, you **don’t actually have multiple machines**
👉 So we’ll do **“pseudo multi-node” (exam-friendly method)**

👉 This is EXACTLY what you should do in exam 💯

---

# 🧪 🔴 MULTI-NODE HADOOP (EXAM PRACTICAL SCRIPT)

---

# 🟢 STEP 0: OPEN TERMINAL

👉 Press:

```
Ctrl + Alt + T
```

---

# 🟢 STEP 1: GO TO HADOOP CONFIG

👉 Type:

```bash
cd $HADOOP_HOME/etc/hadoop
```

👉 Press **Enter**

---

# 🟢 STEP 2: EDIT workers FILE

👉 Type:

```bash
nano workers
```

👉 Press **Enter**

---

👉 You will see something like:

```
localhost
```

---

👉 Now understand:

✔ Single node → only `localhost`
✔ Multi node → add more nodes

---

👉 For exam (since only one system), type:

```
localhost
node1
node2
```

👉 (Even if fake, it's OK for exam explanation)

---

👉 Now SAVE:

* Press **Ctrl + X**
* Press **Y**
* Press **Enter**

---

# 🟢 STEP 3: CONFIGURE core-site.xml

👉 Type:

```bash
nano core-site.xml
```

👉 Press Enter

---

👉 Replace value:

```
hdfs://localhost:9000
```

👉 With:

```
hdfs://master:9000
```

---

👉 Save:

* Ctrl + X
* Y
* Enter

---

# 🟢 STEP 4: CONFIGURE hdfs-site.xml

👉 Type:

```bash
nano hdfs-site.xml
```

👉 Press Enter

---

👉 Change replication:

```
<value>1</value>
```

👉 To:

```
<value>2</value>
```

---

👉 Save:

* Ctrl + X
* Y
* Enter

---

# 🟢 STEP 5: SET HOSTNAME (IMPORTANT FOR MULTI NODE DEMO)

👉 Type:

```bash
hostname
```

👉 Press Enter

---

👉 If it shows:

```
umar
```

👉 Say in exam:

> “This is master node”

---

# 🟢 STEP 6: FORMAT NAMENODE

```bash
hdfs namenode -format
```

👉 Press Enter

---

# 🟢 STEP 7: START HADOOP

```bash
start-dfs.sh
```

👉 Press Enter

---

# 🟢 STEP 8: VERIFY

```bash
jps
```

👉 Press Enter

---

# 🟢 STEP 9: EXPLAIN (VERY IMPORTANT)

👉 While showing, say:

> “In real multi-node setup, worker nodes are different systems connected via network. Here we simulate using localhost entries.”

---

# 🧠 WHAT YOU JUST DID

✔ Edited workers file
✔ Changed replication
✔ Changed master reference
✔ Started cluster

👉 This is what examiner expects

---

# 🚨 VERY IMPORTANT (DON’T MAKE MISTAKE)

❌ Don’t try real multi-node (needs multiple systems)
❌ Don’t get stuck in networking

✔ Just simulate + explain

---

# 🎯 DIFFERENCE YOU MUST SAY

👉 Say confidently:

> “Single node runs on one machine, while multi-node distributes data across multiple machines using worker nodes.”

---

# 🧠 MEMORY TRICK

👉 **Single Node:**

```
localhost
```

👉 **Multi Node:**

```
master + workers
```

---

# 🚀 FINAL EXAM STRATEGY

| Question    | What you do            |
| ----------- | ---------------------- |
| Single Node | Full install + run     |
| Multi Node  | Edit workers + explain |

---

# 🔥 FINAL LINE

You don’t need real cluster
👉 You need **clear explanation + small demo**

---



