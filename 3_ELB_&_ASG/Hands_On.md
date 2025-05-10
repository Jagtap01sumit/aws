## Application Load Balancer

#### We creating two instances using security group launch vizar 1 which provides
![image](https://github.com/user-attachments/assets/ad1a3e07-6e86-4d9d-9c1e-50b910790464)
#### Here 2 ec2 instances are created with same name, so just change 2nd instnace name
![image](https://github.com/user-attachments/assets/b514968c-ba33-4c50-b4e0-89603ac24040)

#### Here two instances are launch with diff ip address
![image](https://github.com/user-attachments/assets/cd8d0201-8038-481f-bcea-23bec64c7402)
***
### We want one URL to access two diff instances
* Left menu -> Load Balancing -> Load Balancers -> create Load Balancer -> Application Load Balancer

![image](https://github.com/user-attachments/assets/4cc0eb27-047c-4527-b571-4c402f619dff)

We select Load balancer IP address type : IPV4
We select Availble zone of subent : eu-north-1a (eun1-az1), 
eu-north-1b (eun1-az2), eu-north-1c (eun1-az3)

#### Add security group -> inbound rules
![image](https://github.com/user-attachments/assets/0cf80815-0be4-47bb-8c1d-f380ef4003ba)

#### click on add security group

![image](https://github.com/user-attachments/assets/eac70709-88c6-4aa4-b86e-5b13ad3b042c)

### Create target group
![image](https://github.com/user-attachments/assets/fd325f53-dec4-437d-a000-e9b72b8a6f3d)
 ### click on next
![image](https://github.com/user-attachments/assets/c3074a39-b060-4848-b5b5-2abf0dcc69a2)

### Inclucde them as pending and Click on create target group

![image](https://github.com/user-attachments/assets/d7d2b241-778f-47a0-9aae-9e6a19ab37b2)

### Click on create load balancer

![image](https://github.com/user-attachments/assets/29b5ee51-ff47-493d-a65e-38ce9be97253)
### we get one url for both instances using load balancer
### copy the dns and paste in browser 
### whenever you refresh the page you can able to see it switch ip address to both instances

![image](https://github.com/user-attachments/assets/ee04f1b6-ac2f-4835-a095-3dbab3c390cc)
![image](https://github.com/user-attachments/assets/164594e0-621e-436b-a0d3-5968663094ed)

### same url with two diff instances 
