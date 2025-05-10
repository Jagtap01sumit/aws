## 🚀 Application Load Balancer - Hands On Guide

### 🔧 Step 1: Create Two EC2 Instances
![image](https://github.com/user-attachments/assets/ad1a3e07-6e86-4d9d-9c1e-50b910790464)
#### - After launch, rename the second instance to distinguish them.
![image](https://github.com/user-attachments/assets/b514968c-ba33-4c50-b4e0-89603ac24040)

#### - Both instances will have different **public IPs**, even if launched from the same AMI.
![image](https://github.com/user-attachments/assets/cd8d0201-8038-481f-bcea-23bec64c7402)
***
### 🎯 Goal

We want **one single URL** to access both EC2 instances, and load should be balanced automatically between them.

---

### 🌀 Step 2: Create Application Load Balancer (ALB)
* Left menu -> Load Balancing -> Load Balancers -> create Load Balancer 
* Click **Create Load Balancer** → choose **Application Load Balancer**
![image](https://github.com/user-attachments/assets/4cc0eb27-047c-4527-b571-4c402f619dff)


#### Load Balancer Configuration:
- **Name**: `my-app-load-balancer`
- **Scheme**: Internet-facing
- **IP type**: IPv4
- **Listeners**: HTTP (port 80)
- **Availability Zones**: Choose at least 2 AZs (e.g., `eu-north-1a`, `1b`, `1c`)

---

We select Load balancer IP address type : IPV4
We select Availble zone of subent : eu-north-1a (eun1-az1), 
eu-north-1b (eun1-az2), eu-north-1c (eun1-az3)
### 🔐 Step 3: Configure Security Group
#### Add security group -> inbound rules
![image](https://github.com/user-attachments/assets/0cf80815-0be4-47bb-8c1d-f380ef4003ba)

#### click on add security group

![image](https://github.com/user-attachments/assets/eac70709-88c6-4aa4-b86e-5b13ad3b042c)
- Add a **new security group** that allows:
  - **HTTP (port 80)** from **Anywhere (0.0.0.0/0)**

---
### 🎯 Step 4: Create Target Group

1. Go to **Target Groups** > Click **Create Target Group**
2. Select:
   - **Target type**: Instances
   - **Protocol**: HTTP
   - **Port**: 80
   - **VPC**: Same VPC as your instances

3. Register both EC2 instances in this target group
4. Click **Create target group**

---
![image](https://github.com/user-attachments/assets/fd325f53-dec4-437d-a000-e9b72b8a6f3d)
 ### click on next
![image](https://github.com/user-attachments/assets/c3074a39-b060-4848-b5b5-2abf0dcc69a2)

### Inclucde them as pending and Click on create target group

![image](https://github.com/user-attachments/assets/d7d2b241-778f-47a0-9aae-9e6a19ab37b2)
### 🔗 Step 5: Attach Target Group to Load Balancer

- Go back to the ALB creation page
- Choose the newly created **target group**
- Complete and **create the Load Balancer**

---
### Click on create load balancer
### 🌐 Step 6: Access via ALB DNS

- After creation, your ALB will provide a **DNS URL**
- Paste this URL in your browser
- Each time you refresh, the load balancer will **alternate between your EC2 instances**

✅ You now have **one URL** that serves traffic from **multiple EC2 instances**!

![image](https://github.com/user-attachments/assets/29b5ee51-ff47-493d-a65e-38ce9be97253)
### we get one url for both instances using load balancer
### copy the dns and paste in browser 
### whenever you refresh the page you can able to see it switch ip address to both instances
---
![image](https://github.com/user-attachments/assets/bc29af2a-bd67-43e8-a918-a9cb9ab91622)

![image](https://github.com/user-attachments/assets/164594e0-621e-436b-a0d3-5968663094ed)

### same url with two diff instances 

### 🧠 Benefits of Application Load Balancer

- Auto-distributes incoming traffic across multiple instances
- Increases availability and fault tolerance
- One central URL to manage multiple servers
