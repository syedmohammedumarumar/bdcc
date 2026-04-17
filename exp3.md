
---

# 📄 🧪 EXPERIMENT 3 — MAPREDUCE PROGRAMS

---

# 🎯 **Aim (WordCount)**

To develop and execute a MapReduce program for Word Count using Hadoop. 

---

# 🧠 **Theory (Write 5 lines only)**

MapReduce is a programming model used in Hadoop for processing large datasets.

* Mapper → processes input and generates key-value pairs
* Reducer → aggregates results

It works in distributed environment and processes data in parallel. 

---

# 🧩 **UNDERSTAND SIMPLY**

👉 Input text → count words

Example:

```
hadoop hadoop big data
```

👉 Output:

```
hadoop 2
big 1
data 1
```

---

# ⚙️ **PROCEDURE (IMPORTANT)**

---

# 🔴 STEP 1: Start Hadoop

```bash id="q1x5b9"
start-dfs.sh
start-yarn.sh
jps
```

---

# 🔴 STEP 2: Create Input File

```bash id="a2knpn"
nano input.txt
```

Paste:

```id="4qch0h"
hadoop mapreduce hadoop
big data hadoop
mapreduce is parallel
hadoop is distributed
big data analytics
```

---

# 🔴 STEP 3: Upload to HDFS

```bash id="8l7vdw"
hdfs dfs -mkdir -p /mr/input
hdfs dfs -put input.txt /mr/input/
hdfs dfs -ls /mr/input
```

---

# 🔴 STEP 4: Compile Program

```bash id="k6x0ea"
mkdir -p classes
javac -classpath "$(hadoop classpath)" -d classes WordCount.java
jar -cvf wordcount.jar -C classes/ .
```

---

# 🔴 STEP 5: Run Job

```bash id="pd1jyy"
hdfs dfs -rm -r /mr/output_wc
hadoop jar wordcount.jar WordCount /mr/input /mr/output_wc
```

---

# 🔴 STEP 6: View Output

```bash id="6e7gxx"
hdfs dfs -cat /mr/output_wc/part-r-00000
```

---

# 📊 **EXPECTED OUTPUT**

```id="6d8lqf"
hadoop       4
big          2
data         2
mapreduce    2
```

---

# 🧾 **Result**

MapReduce WordCount program executed successfully and word frequencies were generated. 

---

# 🟡 PART B — SORTING

---

## 🎯 Aim

To observe sorting in MapReduce output

---

## 🧠 Concept

👉 Hadoop automatically sorts output by key

---

## 🔴 Command

```bash id="z8txiy"
hdfs dfs -cat /mr/output_wc/part-r-00000
```

👉 Output is already sorted

---

## 🧾 Result

Sorting observed successfully in MapReduce output.

---

# 🟢 PART C — FILTER PROGRAM

---

## 🎯 Aim

To filter records using MapReduce

---

## 🔴 Run Job

```bash id="zj2ydn"
hdfs dfs -rm -r /mr/output_filter
hadoop jar filter.jar FilterByKeyword /mr/input /mr/output_filter hadoop
```

---

## 🔴 View Output

```bash id="j3b7wx"
hdfs dfs -cat /mr/output_filter/part-m-00000
```

---

## 📊 Output

```id="j3g96u"
hadoop mapreduce hadoop
big data hadoop
hadoop is distributed
```

---

# 🌐 STEP: YARN UI (IMPORTANT)

Open:

```id="f0o7lo"
http://localhost:8088
```

👉 Shows:

* Map tasks
* Parallel execution

---

# 🧾 Result

Filtering performed successfully and parallel execution observed. 

---

# 🧠 ⚡ MEMORY TRICK

👉 Just remember:

**Input → Map → Reduce → Output**

---

# 🎯 VERY IMPORTANT FOR YOU

👉 This experiment is:

* Coding-based
* Execution-heavy

---

# 🚨 REAL EXAM STRATEGY

👉 If time less:

✔ Do only WordCount
✔ Show output
✔ Explain sorting & filtering

👉 Enough for good marks

---

# 🧠 VIVA QUESTIONS

👉 What is MapReduce?
👉 What is Mapper?
👉 What is Reducer?
👉 Why Hadoop is parallel?
👉 What is shuffle phase?

---

