
AWS Lambda is a **serverless computing service** that allows you to run code without provisioning or managing servers. It automatically scales based on demand and charges only for the compute time used. Lambda is event-driven, meaning it executes code in response to triggers from AWS services like **API Gateway, S3, DynamoDB, and CloudWatch**.

### **How AWS Lambda Works:**

1. **Create a Lambda Function** – Define the function and choose a runtime (e.g., Python, Node.js, Java).
    
2. **Trigger the Function** – AWS Lambda executes in response to events from services like HTTP requests (API Gateway), file uploads (S3), or database updates (DynamoDB).
    
3. **Execute the Code** – The function runs within a managed container and scales automatically.
    
4. **Return a Response** – The function processes the event and returns a result.
    
5. **Monitor & Optimize** – Use AWS CloudWatch for logging, monitoring, and debugging.



## 1. Create and Deploy an AWS Lambda Function



### **Steps:**

6. Log in to **AWS Lambda Console**.
    
7. Click **Create function**.
    
8. Choose **Author from scratch**.
    
9. Enter a function name (e.g., `hello_lambda`).
    
10. Select a runtime (e.g., **Python 3.x**).
    
11. Set the execution role to **cloudacademy-lab-lambda-role**.
    
12. Click **Create function**.
    
13. Modify the function code (example in Python):
    

```
import json

def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from AWS Lambda!')
    }
```

14. Click **Deploy** to save changes.
    

---

## 2. Invoke the Function Using the Test Feature

### **Steps:**

15. Open your function in the AWS Lambda Console.
    
16. Click **Test**.
    
17. Create a new test event:
    
    - Enter an event name (e.g., `haroon`).
        
    - Use the default JSON template.
        
18. Click **Invoke**.
    
19. Check the execution status and response.
    

---

## 3. Create an Alias and a Version of a Function

### **Publishing a New Version:**

20. Open your function in the AWS Lambda Console.
    
21. Click **Publish a new version**.
    
22. Add a description (e.g., `"Initial version"`).
    
23. Click **Publish**.
    

### **Creating an Alias:**

24. Go to the **Aliases** tab.
    
25. Click **Create alias**.
    
26. Enter an alias name (e.g., `prod`).
    
27. Select the version you published earlier.
    
28. Click **Create**.
    

---

## 4. Create an Environment Variable and Access It in Code

### **Adding an Environment Variable:**

29. Open your function in the AWS Lambda Console.
    
30. Scroll down to the **Environment Variables** section.
    
31. Click **Edit**, then **Add environment variable**.
    
32. Set **Key**: `GREETING`, and **Value**: `"Hello from Env Variable!"`.
    
33. Click **Save**.
    

### **Modifying the Lambda Code to Use Environment Variable:**

```
import os
import json

def lambda_handler(event, context):
    greeting = os.environ.get('GREETING', 'Hello from Lambda!')
    
    return {
        'statusCode': 200,
        'body': json.dumps(greeting)
    }
```

### **Deploy and Test:**

34. Click **Deploy**.
    
35. Run a test; the response should return the environment variable’s value.
    

---

## 5. Examine Metrics and Logs Using Amazon CloudWatch

### **Viewing Logs:**

36. Open your function in the AWS Lambda Console.
    
37. Click the **Monitor** tab.
    
38. Click **View logs in CloudWatch**.
    
39. You’ll see log streams for each function execution.
    

### **Checking Metrics:**

40. Open the **Monitor** tab in AWS Lambda.
    
41. Review metrics such as **Invocations, Duration, Errors, and Throttles**.
    
42. Optionally, create **CloudWatch Alarms** to notify you of issues.
    

---