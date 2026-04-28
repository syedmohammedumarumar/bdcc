
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

