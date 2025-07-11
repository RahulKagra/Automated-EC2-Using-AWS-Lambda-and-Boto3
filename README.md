# Automated-EC2-Using-AWS-Lambda-and-Boto3
Automated Instance Management Using AWS Lambda and Boto3

## Objective
This project demonstrates the use of **AWS Lambda** and **Boto3 (Python 3.13)** to automatically **start and stop EC2 instances based on tags**. It is a hands-on assignment for learning AWS automation using serverless functions.

---

## EC2 Setup

1. Created two **t2.micro** EC2 instances.
2. Applied the following **tags**:
   - Instance 1:
     - `Key`: Action
     - `Value`: Auto-Stop
   - Instance 2:
     - `Key`: Action
     - `Value`: Auto-Start

---

## IAM Role for Lambda

- Created an IAM Role named `LambdaEC2ControlRole`
- Attached policy: `AmazonEC2FullAccess` (for demo; in real projects, use least privilege)
- Assigned this role to the Lambda function

---

##  Lambda Function

- Runtime: **Python 3.x**
- Timeout: Increased from default 3 seconds to **30 seconds**
- Function Logic:
  - Uses Boto3 to query EC2 instances based on tag `Action`
  - Stops instances tagged `Auto-Stop` if they are running
  - Starts instances tagged `Auto-Start` if they are stopped

---

##  Lambda Code
   - Please refer "lambda_function.py"
---

##  ScreenShots

## 📸 ScreenShots

| Description                | Screenshot |
|---------------------------|------------|
| EC2 Tags - Auto Start     | ![](ScreenShots/EC2%20Instances%20with%20tags_Auto_Start.png) |
| EC2 Tags - Auto Stop      | ![](ScreenShots/EC2%20Instances%20with%20tags_Auto_Stop.png)  |
| IAM Role Permissions      | ![](ScreenShots/IAM%20Role%20permissions.png)                 |
| Instance State Transitions| ![](ScreenShots/instance%20state%20transitions.png)          |
| Lambda Function           | ![](ScreenShots/Lambda%20Function.png)                       |
| Manual Test               | ![](ScreenShots/Manual%20test.png)                           |

# Testing and Output

- Created a test event in Lambda and invoked it manually.

  Confirmed:

  - Auto-Stop instance transitions to stopped
  
  - Auto-Start instance transitions to running
  
  - Verified instance state changes from the EC2 Dashboard 
