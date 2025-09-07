# Lab 1: Creating a Launch Template

In this lab, we will create a **Launch Template** that provisions EC2 instances with a web server enabled via User Data.

---

## Steps

1. **Navigate to Launch Templates**
   - Search for **EC2** in the AWS Management Console.
     ![](./media/launch-step1.png)
   - Under **Instances**, select **Launch Templates**.
   - Click **Create new launch template**.  
   ![](./media/launch-step2.png)

2. **Configure Template**
   - Enter **Launch Template Name**: `server-template`
   - (Optional) Add a description: *This template enables a web server on the EC2.*  
   ![](./media/launch-step3.png)

3. **Select AMI & Instance Type**
   - **AMI**: Amazon Linux
   - **Instance Type**: `t2.micro`  
   ![](./media/launch-step4.png)
   ![](./media/launch-step5.png)

4. **Add User Data**
   - Scroll to **Advanced Details** → expand → go to **User data** section.
   ![](./media/launch-step6.png) 
   - Paste the following script to install Apache web server:

   ```bash
   #!/bin/bash
   sudo yum install -y httpd 
   sudo systemctl start httpd
   sudo systemctl enable httpd
   echo "Hello from $(hostname)" | sudo tee /var/www/html/index.html
