
---

# 📄 🧪 EXPERIMENT 5 — APACHE SPARK DATAFRAME

---

# 🎯 **Aim**

To perform data processing using Apache Spark DataFrames and apply transformations like select, filter, and groupBy. 

---

# 🧠 **Theory (Write 5–6 lines only)**

Apache Spark is a fast distributed data processing framework used for big data analytics.

Spark DataFrame is a structured data abstraction similar to a table in a database.

It supports operations like:

* select → choose columns
* filter → filter rows
* groupBy → aggregation

These operations help analyze large datasets efficiently. 

---

# 🧩 **UNDERSTAND IN 30 SECONDS**

👉 You are analyzing a dataset like Excel:

| Operation | Meaning         |
| --------- | --------------- |
| select    | choose columns  |
| filter    | apply condition |
| groupBy   | summarize data  |

---

# 🔥 FLOW (REMEMBER THIS)

👉 **Load → Select → Filter → Group → Output**

---

# ⚙️ **PROCEDURE**

---

# 🔴 PART A: HDFS SETUP

---

### Step 1: Create Folder

```bash id="kdbb7l"
hdfs dfs -mkdir -p /data/spark
```

---

### Step 2: Upload Dataset

```bash id="h4lbb7"
hdfs dfs -put sales.csv /data/spark/
```

---

### Step 3: Verify

```bash id="l3v0qg"
hdfs dfs -ls /data/spark
```

---

# 🟡 PART B: SPARK EXECUTION

---

### Step 1: Start PySpark

```bash id="vd7f5k"
pyspark
```

---

### Step 2: Create SparkSession

```python id="n5lj5t"
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("Spark DataFrame Lab").getOrCreate()
```

---

### Step 3: Load Data

```python id="gh6yij"
df = spark.read.option("header", True).option("inferSchema", True) \
    .csv("hdfs:///data/spark/sales.csv")
```

---

# 🟢 PART C: TRANSFORMATIONS

---

## 🔹 SELECT

```python id="4kq0hl"
df.select("order_id", "customer", "city").show()
```

---

## 🔹 FILTER

```python id="3j3x0r"
from pyspark.sql.functions import col
df.filter((col("status") == "Delivered") & (col("amount") > 2000)).show()
```

---

## 🔹 GROUPBY

```python id="7n6z2g"
from pyspark.sql.functions import sum as _sum, avg as _avg, count as _count

df.groupBy("city").agg(
    _count("*").alias("total_orders"),
    _sum("amount").alias("total_sales"),
    _avg("amount").alias("avg_order_value")
).show()
```

---

# 🔵 PART D: OUTPUT

👉 Displays summarized data

Example:

```id="zj9z6z"
Hyderabad   2   25800   12900
Pune        2   33500   16750
```

---

# 🧾 **Result**

Spark DataFrame operations such as select, filter, and groupBy were successfully performed. 

---

# 🧠 ⚡ MEMORY TRICK

👉 Just remember:

**Load → Select → Filter → Group**

---

# 🎯 EXAM STRATEGY

👉 If system supports Spark:
✔ Run PySpark
✔ Show groupBy output

👉 If not:
✔ Write code
✔ Explain logic

---

# 🧠 VIVA QUESTIONS

👉 What is Apache Spark?
👉 What is DataFrame?
👉 Difference between Hadoop and Spark?
👉 What is transformation?
👉 What is action in Spark?

---




# EXp 5 Practical for lab 
---

# 🧪 🔥 EXPERIMENT 5 — FULL PRACTICAL (STEP-BY-STEP)

---

# 🟢 STEP 0: OPEN TERMINAL

👉 Press:

```text
Ctrl + Alt + T
```

---

# 🟢 STEP 1: START HADOOP (VERY IMPORTANT)

👉 Type:

```bash
start-dfs.sh
```

👉 Press **Enter**

---

👉 Check:

```bash
jps
```

👉 Press Enter

✔ Must see:

```
NameNode
DataNode
SecondaryNameNode
```

---

# 🟢 STEP 2: LEAVE SAFE MODE

👉 Type:

```bash
hdfs dfsadmin -safemode leave
```

👉 Press Enter

---

# 🟢 STEP 3: CREATE HDFS FOLDER

```bash
hdfs dfs -mkdir -p /data/spark
```

👉 Press Enter

---

# 🟢 STEP 4: CREATE DATASET

👉 Type:

```bash
nano sales.csv
```

👉 Press Enter

---

👉 Paste:

```
order_id,customer,city,category,amount,status
101,Ravi,Hyderabad,Electronics,25000,Delivered
102,Neha,Pune,Fashion,1500,Returned
103,Arjun,Hyderabad,Grocery,800,Delivered
104,Rahul,Pune,Electronics,32000,Delivered
105,Sneha,Delhi,Fashion,2200,Delivered
```

---

👉 Save:

* Ctrl + X
* Y
* Enter

---

# 🟢 STEP 5: UPLOAD FILE TO HDFS

```bash
hdfs dfs -put sales.csv /data/spark/
```

👉 Press Enter

---

👉 Verify:

```bash
hdfs dfs -ls /data/spark
```

---

# 🔴 STEP 6: INSTALL SPARK

👉 Type:

```bash
cd ~
wget https://downloads.apache.org/spark/spark-3.5.1/spark-3.5.1-bin-hadoop3.tgz
```

👉 Enter

---

```bash
tar -xvzf spark-3.5.1-bin-hadoop3.tgz
```

👉 Enter

---

```bash
sudo mv spark-3.5.1-bin-hadoop3 /usr/local/spark
```

👉 Enter password

---

# 🔴 STEP 7: SET SPARK PATH

```bash
nano ~/.bashrc
```

👉 Go to bottom

👉 Add:

```bash
export SPARK_HOME=/usr/local/spark
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
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

# 🔴 STEP 8: VERIFY SPARK

```bash
spark-shell
```

👉 If opens → SUCCESS

👉 Exit:

```bash
exit
```

---

# 🔴 STEP 9: START PYSPARK

```bash
pyspark
```

👉 Wait until:

```
>>>
```

---

# 🟢 STEP 10: CREATE SESSION

```python
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("Spark DataFrame Lab").getOrCreate()
```

👉 Press Enter

---

# 🟢 STEP 11: LOAD DATA

```python
df = spark.read.option("header", True).option("inferSchema", True).csv("hdfs:///data/spark/sales.csv")
```

👉 Enter

---

# 🟢 STEP 12: DISPLAY DATA

```python
df.show()
```

---

# 🟢 STEP 13: SELECT

```python
df.select("order_id", "customer", "city").show()
```

---

# 🟢 STEP 14: FILTER

```python
from pyspark.sql.functions import col
df.filter((col("status") == "Delivered") & (col("amount") > 2000)).show()
```

---

# 🟢 STEP 15: GROUPBY

```python
from pyspark.sql.functions import sum as _sum, avg as _avg, count as _count

df.groupBy("city").agg(
    _count("*").alias("total_orders"),
    _sum("amount").alias("total_sales"),
    _avg("amount").alias("avg_order_value")
).show()
```

---

# 🎯 DONE — FULL EXPERIMENT COMPLETE

---

# 🧠 WHAT TO SAY WHILE DOING

👉 Say step-by-step:

* “Starting Hadoop services”
* “Creating HDFS directory”
* “Uploading dataset”
* “Installing Spark”
* “Running PySpark”
* “Performing DataFrame operations”

---

# 🚨 IMPORTANT EXAM SHORTCUT

👉 If time less:

✔ Skip Spark install
✔ Write code
✔ Explain logic

---

# 🧠 MEMORY TRICK

👉 **HDFS → Spark → Load → Select → Filter → Group**

---

