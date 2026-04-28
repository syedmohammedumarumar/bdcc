
---

# 📄 🧪 EXPERIMENT 8 — CLOUD BIG DATA CLUSTER

---

# 🎯 **Aim**

To deploy and execute Big Data workloads by launching and configuring a cluster using cloud-managed services such as Amazon EMR, Azure HDInsight, or Google Cloud Dataproc. 

---

# 🧠 **Theory**

Cloud-managed Big Data services provide platforms to process large datasets without manual setup of clusters.

These services offer:

* Automatic cluster provisioning
* Scalability
* Integrated storage
* Support for frameworks like Hadoop, Spark, and Hive

They simplify the deployment and execution of Big Data workloads in distributed environments. 

---

# ⚙️ **Procedure**

---

# 🔵 **PART A — AMAZON EMR**

---

### Step 1: Login

Open AWS Console → Go to **EMR**

---

### Step 2: Create Cluster

Click **Create Cluster** and configure:

* Cluster Name → BigDataLabCluster
* Applications → Hadoop, Spark
* Instances → 3

---

### Step 3: Configure Storage

Create S3 bucket and upload dataset (`sample.txt`)

---

### Step 4: Launch Cluster

Click **Create Cluster** and wait until status = Running

---

### Step 5: Run Job

```bash id="emr1"
spark-submit --class org.apache.spark.examples.JavaWordCount \
/usr/lib/spark/examples/jars/spark-examples.jar \
s3://bucket-name/sample.txt
```

---

### Step 6: Monitor

Check job status in EMR dashboard

---

### Step 7: View Output

Output stored in S3 bucket

---

# 🟢 **PART B — AZURE HDINSIGHT**

---

### Step 1: Login

Open Azure Portal

---

### Step 2: Create Cluster

Go to **Create Resource → HDInsight Cluster**

* Cluster Type → Spark
* Cluster Name → bigdatalabcluster

---

### Step 3: Upload Dataset

Upload file to Azure Blob Storage

---

### Step 4: Run Job

```bash id="az1"
spark-submit wordcount.py sample.txt
```

---

### Step 5: Monitor

Use YARN UI to check job execution

---

# 🟡 **PART C — GOOGLE CLOUD DATAPROC**

---

### Step 1: Login

Open Google Cloud Console

---

### Step 2: Create Cluster

Go to Dataproc → Create Cluster

* Master Node → 1
* Worker Nodes → 2

---

### Step 3: Upload Dataset

Upload file to Cloud Storage

---

### Step 4: Run Job

```bash id="gcp1"
gcloud dataproc jobs submit spark \
--cluster bigdata-cluster \
--class org.apache.spark.examples.JavaWordCount \
--jars file:///usr/lib/spark/examples/jars/spark-examples.jar \
gs://bucket/sample.txt
```

---

### Step 5: Monitor

Check job status in Dataproc dashboard

---

# 📊 **Expected Output**

Example Word Count result:

```
Cloud   2  
Data    2  
Big     2  
cluster 1  
```

---

# 🧾 **Result**

Big Data cluster was successfully deployed using cloud-managed services, and the workload was executed using Hadoop/Spark frameworks. 

---

# 🧠 ⚡ MEMORY TRICK

👉 **Cluster → Upload → Run → Monitor → Output**

---

