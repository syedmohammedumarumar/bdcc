Alright Professor 👨‍🏫 — here is your **EXPERIMENT 4 EXAM NOTES (crisp + high scoring + easy to revise)**

⚠️ This one looks big, but in exam you only write **structured + limited content**.

---

# 📄 🧪 EXPERIMENT 4 — HIVE & PIG

---

## 🎯 **Aim**

To analyze data stored in HDFS using Hive and Pig and compare the results. 

---

## 🧠 **Theory (Write 5–6 lines only)**

Apache Hive and Apache Pig are tools used to process data stored in HDFS.

* **Hive** uses SQL-like language (HiveQL) for querying data
* **Pig** uses Pig Latin for data processing
* Hive is suitable for structured data analysis
* Pig is suitable for data flow and ETL tasks

Both tools can produce the same results using different approaches. 

---

## ⚙️ **Procedure / Commands**

---

# 🔴 PART A: HDFS SETUP

### Create directory

```bash
hdfs dfs -mkdir -p /data/weblogs
```

---

### Upload dataset

```bash
hdfs dfs -put weblogs.tsv /data/weblogs/
```

---

### Verify

```bash
hdfs dfs -ls /data/weblogs
```

---

# 🟡 PART B: HIVE (SQL)

---

### Start Hive

```bash
hive
```

---

### Create Database

```sql
CREATE DATABASE lab;
USE lab;
```

---

### Create Table

```sql
CREATE EXTERNAL TABLE weblogs (
  ts STRING,
  user_id STRING,
  url STRING,
  status INT,
  bytes BIGINT
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY '\t'
STORED AS TEXTFILE
LOCATION '/data/weblogs';
```

---

### Query (Top URLs)

```sql
SELECT url, COUNT(*) AS hits
FROM weblogs
GROUP BY url
ORDER BY hits DESC
LIMIT 10;
```

---

# 🟢 PART C: PIG (Pig Latin)

---

### Start Pig

```bash
pig
```

---

### Load Data

```pig
weblogs =
LOAD '/data/weblogs/weblogs.tsv'
USING PigStorage('\t')
AS (ts:chararray, user_id:chararray, url:chararray, status:int, bytes:long);
```

---

### Query

```pig
g = GROUP weblogs BY url;
hits = FOREACH g GENERATE group AS url, COUNT(weblogs) AS hits;
sorted = ORDER hits BY hits DESC;
top10 = LIMIT sorted 10;
DUMP top10;
```

---

# 🔵 PART D: COMPARISON

👉 Compare outputs of Hive and Pig

👉 Both should give same results

---

## 📊 **Expected Output (Short)**

Hive Output:

```
/home   15420
/login  12011
```

Pig Output:

```
(/home,15420)
(/login,12011)
```

---

## 🧾 **Result**

Thus, the dataset stored in HDFS was successfully analyzed using Hive and Pig, and both produced equivalent results. 

---

# 🧠 ⚡ MEMORY TRICK

👉 Just remember:

**Upload → Hive → Pig → Compare**

---

# 🚨 IMPORTANT FOR YOU

👉 You CANNOT run this yet ❌
Because:

* Hive not installed
* Pig not installed

---






WEEK 4 BDACC Lab
Aim: To interact with a large dataset stored in HDFS using Apache Hive and Apache Pig, execute equivalent analytics using HiveQL and Pig Latin, and compare and analyze the query results from both tools on the same dataset.
Procedure
A) Dataset Setup in HDFS:
1. Create HDFS directory.
2. Upload dataset file (weblogs.tsv) to HDFS.
3. Verify file upload using HDFS commands.
B) Hive Procedure:
1. Start Hive shell.
2. Create database and external table.
3. Execute analysis queries (Top URLs, Error %, Total bytes per user).
C) Pig Procedure:
1. Start Pig shell.
2. Load dataset using PigStorage.
3. Execute equivalent queries using Pig Latin.
D) Comparison:
1. Store Hive and Pig outputs in HDFS.
2. Compare outputs using diff command.
Code:

HDFS Commands
hdfs dfs -mkdir -p /data/weblogs
hdfs dfs -put weblogs.tsv /data/weblogs/
hdfs dfs -ls /data/weblogs
Hive Code (HiveQL)
CREATE DATABASE IF NOT EXISTS lab;
USE lab;

CREATE EXTERNAL TABLE IF NOT EXISTS weblogs (
  ts STRING,
  user_id STRING,
  url STRING,
  status INT,
  bytes BIGINT
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY '\t'
STORED AS TEXTFILE
LOCATION '/data/weblogs';

-- Q1: Top URLs
SELECT url, COUNT(*) AS hits
FROM weblogs
GROUP BY url
ORDER BY hits DESC
LIMIT 10;
Pig Code (Pig Latin)
weblogs =
  LOAD '/data/weblogs/weblogs.tsv'
  USING PigStorage('\t')
  AS (ts:chararray, user_id:chararray, url:chararray, status:int, bytes:long);

g = GROUP weblogs BY url;
hits = FOREACH g GENERATE group AS url, COUNT(weblogs) AS hits;
sorted = ORDER hits BY hits DESC;
top10 = LIMIT sorted 10;
DUMP top10;
Output:
Sample Hive Output:
/home   15420
/login  12011
/about  10005
Sample Pig Output:
(/home,15420)
(/login,12011)
(/about,10005)
Result:
The dataset stored in HDFS was successfully analyzed using both Hive and Pig. Equivalent queries written in HiveQL and Pig Latin produced matching results. Hive is suitable for SQL-based structured analytics, while Pig is better for dataflow and ETL processing tasks.
