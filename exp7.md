

---

# 📄 🧪 EXPERIMENT 7 — CLOUD STORAGE + CRUD

---

# 🎯 **Aim**

To use cloud storage and perform CRUD operations using a cloud-based SQL database. 

---

# 🧠 **Theory (Write 5 lines only)**

Cloud storage allows storing files on remote servers (like S3, Blob, GCS).

Cloud SQL databases are managed databases provided by cloud platforms.

CRUD operations include:

* Create → Insert data
* Read → Retrieve data
* Update → Modify data
* Delete → Remove data 

---

# 🧩 **UNDERSTAND SIMPLY**

👉 This experiment has **2 parts**:

### 🔵 Part 1 → Upload file to cloud (S3)

### 🔴 Part 2 → Perform SQL operations

---

# ⚙️ **PROCEDURE**

---

# 🔵 PART A: CLOUD STORAGE (AWS S3)

---

### Step 1: Login AWS

👉 Go to AWS Console

---

### Step 2: Open S3

👉 Click **Create Bucket**

---

### Step 3: Create Bucket

* Enter bucket name
* Select region
* Click Create

---

### Step 4: Upload File

👉 Upload any file (example: `student.csv`)

---

### ✅ Output:

👉 File stored in cloud successfully

---

# 🔴 PART B: CLOUD SQL (RDS)

---

### Step 1: Create Database

👉 Go to **RDS**

* Engine → MySQL
* Template → Free tier
* Username → admin
* Password → set

👉 Click Create

---

### Step 2: Connect

```bash id="c6rnxg"
mysql -h <endpoint> -u admin -p
```

---

# 🟢 PART C: CRUD OPERATIONS (IMPORTANT)

---

## 🔹 CREATE

```sql id="v8n1cx"
CREATE DATABASE college;
USE college;

CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50)
);
```

---

## 🔹 INSERT (Create Data)

```sql id="1hg8yw"
INSERT INTO student VALUES (1, 'Anita', 'CSE');
INSERT INTO student VALUES (2, 'Rahul', 'ECE');
```

---

## 🔹 READ

```sql id="v4tyeq"
SELECT * FROM student;
```

---

## 🔹 UPDATE

```sql id="a9tt8i"
UPDATE student 
SET department = 'IT'
WHERE id = 2;
```

---

## 🔹 DELETE

```sql id="82i6gk"
DELETE FROM student WHERE id = 1;
```

---

## 🔹 VERIFY

```sql id="xppg7s"
SELECT * FROM student;
```

---

# 📊 **EXPECTED OUTPUT**

👉 Table data displayed
👉 Insert, update, delete successful

---

# 🧾 **RESULT**

Cloud storage and cloud SQL database were successfully created and CRUD operations were performed. 

---

# 🧠 ⚡ MEMORY TRICK

👉 Just remember:

**Upload → Connect → CRUD**

---

# 🎯 IMPORTANT FOR YOU

👉 You CANNOT run this locally easily ❌
👉 In exam:

### Case 1: Cloud available

→ Perform steps

### Case 2: No cloud

→ Write commands + explain

---

# 🧠 VIVA QUESTIONS (VERY IMPORTANT)

👉 What is CRUD?
👉 What is S3?
👉 What is RDS?
👉 Difference between local DB and cloud DB?
👉 What is bucket?

---

