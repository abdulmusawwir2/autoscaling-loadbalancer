# AWS VPC – 2 Subnets – 2 EC2 Instances – Application Load Balancer

This project demonstrates a simple, highly available AWS infrastructure using a custom VPC, two public subnets, two web servers, and an Application Load Balancer.  
Each EC2 instance displays its hostname and private IP, allowing you to verify load balancing visually.

---

## 📌 Architecture Diagram (High Level)

VPC (12.0.0.0/16)
│
├── Public Subnet A (12.0.1.0/24) — EC2 Instance 1
├── Public Subnet B (12.0.2.0/24) — EC2 Instance 2
│
└── Application Load Balancer (HTTP : 80)

yaml
Copy code

---

## 📸 **Screenshots**

### **1. VPC & Subnet Configuration**
![image](https://github.com/user-attachments/assets/e21f333e-c335-423e-a425-e15572a142d7)

---

### **2. EC2 Instances Running in Two AZs**
![image](https://github.com/user-attachments/assets/51614bf4-cee5-4b63-b551-602a21086e7b)

---

### **3. EC2 Webpage Showing Server Hostname & IP**
![image](https://github.com/user-attachments/assets/a3c76771-b8a5-4d75-b25f-beae780acbf5)

---

### **4. Application Load Balancer Target Group**
![image](https://github.com/user-attachments/assets/a06d834b-e31d-45f1-9cff-f837913260bc)

---

### **5. Second EC2 Instance Webpage**
![image](https://github.com/user-attachments/assets/2312f6c6-88f7-461e-8526-2d23d90d5b1a)

---

### **6. Public IP Opened (Direct EC2 Access)**
![image](https://github.com/user-attachments/assets/a7f80ae7-3cb1-4391-bab3-76db924d06ca)

---

## 🌐 Test URLs

### **Direct EC2 Instance**
http://3.110.162.25

markdown
Copy code

### **Load Balancer DNS**
http://my-practice-loadbalancer-49911312.ap-south-1.elb.amazonaws.com

php-template
Copy code

Refreshing the ALB page will alternate between:

- `ip-12-0-1-150`  
- `ip-12-0-1-240`

This confirms load balancing is working.

---

## 🏗️ Components

### ✔️ VPC
- CIDR: `12.0.0.0/16`
- DNS hostnames: ON  
- DNS resolution: ON  

### ✔️ Subnets
- Public Subnet A → `12.0.1.0/24` (ap-south-1a)
- Public Subnet B → `12.0.2.0/24` (ap-south-1b)

### ✔️ Route Table
- `0.0.0.0/0` → Internet Gateway  

### ✔️ Security Groups
- SG-ALB → Allow HTTP (80) from anywhere  
- SG-EC2 → Allow HTTP only from ALB SG  
