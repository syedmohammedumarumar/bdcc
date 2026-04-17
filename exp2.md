
---

# 📄 🧪 EXPERIMENT 2 — HDFS FILE OPERATIONS (REVISION NOTES)

---

## 🎯 **Aim**

To perform file operations such as upload, read, replication, and deletion in HDFS using Hadoop. 

---

## 🧠 **Theory (Write 4–5 lines only)**

HDFS (Hadoop Distributed File System) is used to store large data across distributed systems.

* Files are divided into blocks
* Stored in DataNodes
* Managed by NameNode

HDFS supports operations like upload, read, replication, and deletion of files. 

---

## ⚙️ **Procedure / Commands**

---

### 🔹 Step 1: Start Hadoop

```bash
start-dfs.sh
jps
```

---

### 🔹 Step 2: Create Local File

```bash
nano sample.txt
```

Content:

```
HDFS File Operations Experiment
Upload Read Delete Replication
```

---

### 🔹 Step 3: Create Directory in HDFS

```bash
hdfs dfs -mkdir /user
hdfs dfs -mkdir /user/hadoop
```

---

### 🔹 Step 4: Upload File

```bash
hdfs dfs -put sample.txt /user/hadoop/
hdfs dfs -ls /user/hadoop
```

---

### 🔹 Step 5: Read File

```bash
hdfs dfs -cat /user/hadoop/sample.txt
```

---

### 🔹 Step 6: Check Replication

```bash
hdfs fsck /user/hadoop/sample.txt -files -blocks
```

---

### 🔹 Step 7: Change Replication

```bash
hdfs dfs -setrep 2 /user/hadoop/sample.txt
```

---

### 🔹 Step 8: Delete File

```bash
hdfs dfs -rm /user/hadoop/sample.txt
```

---

## 📊 **Expected Output (Write short)**

* `jps` → NameNode, DataNode, SecondaryNameNode
* `ls` → sample.txt
* `cat` → file content
* `fsck` → replication info
* `rm` → file deleted

---

## 🧾 **Result**

Thus, file operations such as upload, read, replication, and deletion were successfully performed in HDFS. 

---

# 🧠 ⚡ SUPER FAST MEMORY TRICK

👉 Just remember:

**Start → Create → Upload → Read → Replicate → Delete**

---
