# Day Report: Advanced Cloud and DevOps Setup with Problem-Solving Insights  

Today, I successfully tackled a series of advanced tasks in cloud computing, virtualization, and DevOps, overcoming multiple challenges along the way:    

### 1. AWS Account Setup  

- Created and secured an AWS account, linking it with my **debit card** for billing and resource management.    

### 2. EC2 Instance Creation and Web Hosting  

- Launched an EC2 instance and deployed a functional **website**, configuring security groups, networking, and server setup for seamless operation.    

### 3. Linux Integration with Windows using WSL  

- Recognized the need for a Linux environment for enhanced compatibility with cloud tools.    
- Installed and configured Ubuntu via WSL (Windows Subsystem for Linux) on Windows, ensuring it was optimized for cloud operations.    

### 4. Overcoming Ubuntu Challenges  

- Got stuck while trying to create a root user and set up a password in Ubuntu. After troubleshooting, I configured the system correctly for full administrative access.    

### 5. SSH Connection to EC2 Instance  

- Faced challenges while trying to connect to the EC2 instance using the **.pem key**.    
- After identifying and correcting the key's file permissions and usage, I established a secure SSH connection between the WSL environment and the EC2 instance.    

### 6. Learning AWS Regional Specificity  

- Encountered issues while trying to list running EC2 instances.    
- Discovered that AWS services operate region-wise, and adjusted my configurations to select the correct region, enabling accurate instance management.    

### 7. IAM User Creation and Configuration  

- Created and configured an IAM user, assigned tailored permissions, and set it up to manage AWS resources efficiently.    
- Configured the AWS CLI on Ubuntu, enabling direct command-line interaction with AWS services.    

### 8. Full CLI Access and Validation  

- Assigned granular permissions to the IAM user, granting comprehensive control over the CLI.    
- Successfully logged in with the IAM credentials, validating control over AWS services through the CLI environment.

---------------------
### Here is your list of commands:
### **AWS Setup and Configuration**

1. **Install AWS CLI**:
   ```bash
   sudo apt install awscli
   ```

2. **Describe EC2 Instances** in the `eu-north-1` region:
   ```bash
   aws ec2 describe-instances --region eu-north-1
   ```

3. **Get the Caller Identity** (useful for verifying the AWS credentials):
   ```bash
   aws sts get-caller-identity
   ```

4. **Configure AWS CLI** (set up your AWS credentials):
   ```bash
   aws configure
   ```

---

### **Connecting to EC2 Instance**

- **Connect to EC2 Instance via SSH**:
   ```bash
   ssh -i mine.pem ec2-user@51.20.255.74
   ```

- **Public IP for connecting**:
   ```
   http://51.20.255.74/
   ```

---

### **Instance Management Commands**

1. **Check EC2 Instance ID**:
   ```bash
   aws ec2 describe-instances --region eu-north-1 --query "Reservations[].Instances[].InstanceId" --output text
   ```

2. **Stop the EC2 Instance** (using the instance ID):
   ```bash
   aws ec2 stop-instances --region eu-north-1 --instance-ids i-067d6390649e04d34
   ```

   **Response Example**:
   ```json
   {
     "StoppingInstances": [
       {
         "InstanceId": "i-067d6390649e04d34",
         "CurrentState": {
           "Code": 64,
           "Name": "stopping"
         },
         "PreviousState": {
           "Code": 16,
           "Name": "running"
         }
       }
     ]
   }
   ```

3. **Start the EC2 Instance Again**:
   ```bash
   aws ec2 start-instances --region eu-north-1 --instance-ids i-067d6390649e04d34
   ```

---

These commands are now properly formatted and organized to guide you through managing AWS EC2 instances.
