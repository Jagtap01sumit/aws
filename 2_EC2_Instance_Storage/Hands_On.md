# 🚀 AMI Hands-On Guide

## ✅ Step 1: Create a Virtual Machine for Apache Server (`httpd`)

1. Launch an EC2 instance (Amazon Linux 2).

![image](https://github.com/user-attachments/assets/5981da66-5a41-4aad-a65d-4143afe805e5)
![image](https://github.com/user-attachments/assets/7ffd71fd-f6ca-49dc-bd00-df1bc3559c31)
![image](https://github.com/user-attachments/assets/b952d156-3d42-43ba-8ed1-86baabc4d218)
![image](https://github.com/user-attachments/assets/2f97c55b-7cc4-4e7d-bd15-dd2269b83bb0)
2. In the **Advanced Settings**, add this to the **User data** section:
   ```bash
   #!/bin/bash
   yum update -y
   yum install -y httpd
   systemctl start httpd
   systemctl enable httpd
  ```
![image](https://github.com/user-attachments/assets/baba2a2b-1eb0-4b14-8f3f-8c7dba33a3f6)
3. Launch the instance.

![image](https://github.com/user-attachments/assets/bdc7a89e-b675-4dd5-8760-269e0f5e01ea)
4. Copy its Public IP and paste it into your browser — you’ll see your Apache welcome message!
![image](https://github.com/user-attachments/assets/73a1b649-c68d-4daa-9184-caa33b91455d)

***
## ✅ Step 2: Create an AMI from This Instance
![image](https://github.com/user-attachments/assets/c7f2f316-9f10-41e0-b090-b88cbef4fd61)

1. Go to EC2 Dashboard → Select your instance → Click Actions → Create Image.
![image](https://github.com/user-attachments/assets/a855c8c1-e793-49ce-8ea0-c5f026e3cb2e)
2. select AMIs from left menu , you able to see your AMI
![image](https://github.com/user-attachments/assets/c4f07b89-9a59-495f-a09e-c340632eaf07)

## ✅ Step 3: Launch a New EC2 Instance Using Your AMI
![image](https://github.com/user-attachments/assets/d8636efc-f68f-40fb-8bef-efa673e3019b)
1. Click Launch Instance → Choose My AMIs → Select the one you created.
![image](https://github.com/user-attachments/assets/0cdd72eb-c8b5-4337-a957-2335a0b0cb76)

2. In User data, you can skip installing httpd because it’s already included in your AMI.
You can just add a custom welcome message like:
```
#!/bin/bash
echo "<h1>Hello from custom AMI - $(hostname -f)</h1>" > /var/www/html/index.html
```
💡 No need to write these lines again:
```
#!/bin/bash

# Use this for your user data (script from top to bottom)

# install httpd (Linux 2 version)

echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html

```
> [!NOTE]
> here we eliminate the three line which are,Because they were already done in the AMI!
```

yum update -y

yum install -y httpd

systemctl start httpd

systemctl enable httpd

```

> [!NOTE]
>  We dont need to reinstall httpd because AMI already includes httpd

***

### 🖼️ AMI with Pre-installed Software (like `httpd`)

I created an **AMI (Amazon Machine Image)** from an EC2 instance where `httpd` (Apache web server) was already installed and configured.

Later, I launched a **new EC2 instance using that AMI**.  
➡️ This new instance already had `httpd` installed — no need to install it again manually!

#### ✅ Benefits:
- Saves setup time ⏱️
- Ensures consistency across environments 🧩
- Makes it easy to scale new instances with the same configuration 🚀

