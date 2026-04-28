
---

# 📄 🧪 EXPERIMENT 9 — SERVERLESS APPLICATION

---

# 🎯 **Aim**

To develop and deploy a serverless function in a cloud platform and configure triggers such as HTTP, event-based, and scheduled triggers. 

---

# 🧠 **Theory**

Serverless computing is a cloud computing model where the cloud provider manages infrastructure automatically.

Users only write code, and execution is triggered by events.

Popular serverless platforms include:

* AWS Lambda
* Azure Functions
* Google Cloud Functions

A trigger is an event that automatically invokes the function, such as HTTP requests, file uploads, or scheduled time events. 

---

# ⚙️ **Procedure (AWS Lambda)**

---

### 🔴 Step 1: Login

Open AWS Console → Navigate to **Lambda**

---

### 🔴 Step 2: Create Function

* Click **Create Function**
* Select **Author from Scratch**
* Function Name → HelloServerless
* Runtime → Python

---

### 🔴 Step 3: Write Code

```python id="srv1"
import json

def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": "Hello! Serverless Function Executed Successfully"
    }
```

👉 Click **Deploy**

---

# 🟡 **Step 4: Add HTTP Trigger**

* Click **Add Trigger**
* Select **API Gateway**
* Create new API

---

### Output:

```id="srv2"
Hello! Serverless Function Executed Successfully
```

---

# 🟢 **Step 5: Event-Based Trigger**

* Add Trigger → S3
* Event → Object Created

👉 Function runs when file is uploaded

---

# 🔵 **Step 6: Scheduled Trigger**

* Add Trigger → EventBridge
* Example:

```id="srv3"
rate(5 minutes)
```

👉 Function runs every 5 minutes

---

# 🟣 **Step 7: Test Function**

```json id="srv4"
{
  "message": "Test Event"
}
```

👉 Output:

* Status Code: 200
* Execution successful

---

# 🟤 **Step 8: Monitoring**

* Go to Monitoring → Logs
* View logs in CloudWatch

---

# 📊 **Expected Output**

* Function created
* Trigger executed
* Output displayed
* Logs generated

---

# 🧾 **Result**

The serverless application was successfully developed and deployed using serverless functions and triggers. 

---

# 🧠 ⚡ MEMORY TRICK

👉 **Function → Trigger → Execute → Monitor**

---

