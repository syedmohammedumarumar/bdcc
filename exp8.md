
---

# 📄 🧪 EXPERIMENT 8 — CLOUD BIG DATA CLUSTER (EMR / Dataproc)

---

# 🎯 **Aim**

To deploy and execute Big Data workloads by launching and configuring a cluster using cloud-managed services. 

---

# 🧠 **Theory (Write 5–6 lines only)**

Cloud-managed services like Amazon EMR, Azure HDInsight, and Google Dataproc provide platforms to run Big Data frameworks like Hadoop and Spark.

These services automate cluster setup, provide scalability, and reduce manual configuration effort.

They are used to process large datasets efficiently in distributed environments. 

---

# 🧩 **UNDERSTAND IN 30 SECONDS**

👉 Instead of installing Hadoop manually (Exp 1)
👉 Cloud does it automatically for you

---

## 🔥 Flow:

👉 **Create Cluster → Upload Data → Run Job → Get Output**

---

# ⚙️ **PROCEDURE (AWS EMR — MAIN)**

---

## 🔴 Step 1: Login

👉 Open AWS Console → EMR

---

## 🔴 Step 2: Create Cluster

* Cluster Name → BigDataLabCluster
* Applications → Hadoop, Spark
* Instances → 3

👉 Click Create Cluster

---

## 🔴 Step 3: Upload Data

👉 Upload file (`sample.txt`) to S3 bucket

---

## 🔴 Step 4: Run Job

```bash id="0i9xvc"
spark-submit --class org.apache.spark.examples.JavaWordCount \
/usr/lib/spark/examples/jars/spark-examples.jar \
s3://bucket-name/sample.txt
```

---

## 🔴 Step 5: Monitor

👉 Check job status in EMR dashboard

---

## 🔴 Step 6: View Output

👉 Output stored in S3

---

# 🟢 OPTIONAL (GCP DATAPROC)

```bash id="kz6f5g"
gcloud dataproc jobs submit spark \
--cluster bigdata-cluster \
--class org.apache.spark.examples.JavaWordCount \
--jars file:///usr/lib/spark/examples/jars/spark-examples.jar \
gs://bucket/sample.txt
```

---

# 📊 **EXPECTED OUTPUT**

Example:

```id="3z3uee"
Cloud 2
data 2
Big 2
cluster 1
```

---

# 🧾 **RESULT**

Big Data cluster was successfully created and workload was executed using cloud-managed services. 

---

# 🧠 ⚡ MEMORY TRICK

👉 Just remember:

**Cluster → Upload → Run → Output**

---

# 🎯 WHAT HAPPENS IN EXAM

👉 Mostly:

* You WON’T actually create cluster (time + internet issue)
* You just:

  * Write steps
  * Explain flow
  * Show command

---

# 🧠 VIVA QUESTIONS

👉 What is EMR?
👉 What is cluster?
👉 Difference between local Hadoop and EMR?
👉 What is Spark?
👉 What is distributed processing?

---

