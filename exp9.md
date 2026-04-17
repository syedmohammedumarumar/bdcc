
---

# 📄 🧪 EXPERIMENT 9 — SERVERLESS FUNCTION (AWS Lambda)

---

# 🎯 **Aim**

To develop and deploy a serverless function and configure triggers to execute it automatically. 

---

# 🧠 **Theory (Write 5–6 lines only)**

Serverless computing is a cloud model where the cloud provider manages infrastructure and automatically scales resources.

Users only write code, and execution happens based on triggers.

Popular platforms include AWS Lambda, Azure Functions, and Google Cloud Functions.

Triggers like HTTP, events, and schedules invoke functions automatically. 

---

# 🧩 **UNDERSTAND IN 30 SECONDS**

👉 You write a function
👉 Cloud runs it automatically

---

## 🔥 Flow:

👉 **Create Function → Add Trigger → Run → Get Output**

---

# ⚙️ **PROCEDURE (AWS LAMBDA)**

---

## 🔴 Step 1: Login

👉 Open AWS Console → Lambda

---

## 🔴 Step 2: Create Function

* Name → HelloServerless
* Runtime → Python
* Click Create

---

## 🔴 Step 3: Write Code

```python id="l5mh2n"
import json

def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": "Hello! Serverless Function Executed Successfully"
    }
```

👉 Click **Deploy**

---

# 🟡 STEP 4: ADD HTTP TRIGGER

👉 Add Trigger → API Gateway

👉 Copy URL → open in browser

---

## ✅ Output:

```id="6y4hbg"
Hello! Serverless Function Executed Successfully
```

---

# 🟢 STEP 5: EVENT TRIGGER (OPTIONAL)

👉 Example:

* S3 upload triggers function

---

# 🔵 STEP 6: SCHEDULE TRIGGER

👉 Example:

```id="5ns6rr"
rate(5 minutes)
```

👉 Function runs every 5 mins

---

# 🟣 STEP 7: TEST FUNCTION

```json id="4hbf7l"
{
  "message": "Test Event"
}
```

👉 Output → Status Code 200

---

# 🟤 STEP 8: MONITOR

👉 Check logs in CloudWatch

* Execution time
* Errors
* Usage

---

# 📊 **EXPECTED OUTPUT**

* Function created
* Trigger executed
* Output displayed
* Logs generated

---

# 🧾 **RESULT**

Serverless function was successfully created, deployed, and executed using triggers. 

---

# 🧠 ⚡ MEMORY TRICK

👉 Just remember:

**Function → Trigger → Execute → Monitor**

---

# 🎯 EXAM REALITY

👉 Most cases:

* You WON’T actually run AWS
* You will:

  * Write code
  * Explain triggers
  * Show flow

---

# 🧠 VIVA QUESTIONS

👉 What is serverless?
👉 What is Lambda?
👉 What is trigger?
👉 Types of triggers?
👉 Advantage of serverless?

---

