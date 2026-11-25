# AWS-LOAD-BALANCER
# REG NUMBER: 212225040241
# NAME: MOHAMED MUBEEN A
# AIM
To use Elastic Load Balancing (ELB) and Auto Scaling services to load balance and automatically scale an AWS infrastructure.

# ALGORITHM
Step 1: Create an AMI for Auto Scaling
Open the EC2 console, confirm that Web Server 1 is running (2/2 status checks passed), select the instance, and choose Actions → Image and templates → Create image. Name it "WebServerAMI" and create it. This AMI will be used to launch identical instances later.

Step 2: Create a Target Group and Load Balancer
Create a Target Group named "LabGroup" (type: Instances, VPC: Lab VPC) without registering targets yet. Then create an Application Load Balancer named "LabELB" under Lab VPC, mapped to Public Subnet 1 and Public Subnet 2, using the Web Security Group, with the HTTP:80 listener forwarding to LabGroup.

Step 3: Create a Launch Template and Auto Scaling Group
Create a Launch Template named "LabConfig" using the WebServerAMI, instance type t2.micro, key pair "vockey", the Web Security Group, and Detailed CloudWatch monitoring enabled. Using this template, create an Auto Scaling group named "Lab Auto Scaling Group" attached to Private Subnet 1 and Private Subnet 2, linked to the LabGroup target group, with desired/minimum/maximum capacity of 2/2/6 and a target tracking scaling policy set to maintain 60% average CPU utilization.

Step 4: Verify Load Balancing
Confirm that two new "Lab Instance" EC2 instances were launched by Auto Scaling and that both show a "healthy" status in the LabGroup target group. Copy the Load Balancer's DNS name and open it in a browser to confirm the application is being served correctly through the load balancer.

Step 5: Test Auto Scaling
Lower the scaling policy's target CPU value to 50% to make scaling trigger sooner, then use the application's "Load Test" feature to generate high CPU load across the instances. Monitor the CloudWatch alarms (AlarmLow/AlarmHigh) until AlarmHigh enters the "In alarm" state, then verify in the EC2 console that additional instances were automatically launched to handle the load.

Step 6: Terminate the Original Web Server
Select Web Server 1 (the original instance used to create the AMI) and terminate it, since it is no longer needed once the Auto Scaling group is managing instances independently.

# OUTPUT
<img width="1882" height="957" alt="Screenshot 2026-11-25 151931" src="https://github.com/user-attachments/assets/cb51cf36-9cc4-4775-b3d1-d1914ed37d87" />

<img width="1887" height="937" alt="Screenshot 2026-11-25 152044" src="https://github.com/user-attachments/assets/399c5bb5-8956-4608-afbc-abb4b1a83fe7" />

<img width="1892" height="930" alt="Screenshot 2026-11-25 152622" src="https://github.com/user-attachments/assets/0f066bf6-cbb4-46a1-83d6-bc30e267553c" />

<img width="1895" height="951" alt="Screenshot 2026-11-25 152654" src="https://github.com/user-attachments/assets/14f21291-1e06-46ad-9cf4-6f6f1df1dd01" />

<img width="1882" height="902" alt="Screenshot 2026-11-25 152906" src="https://github.com/user-attachments/assets/450e11d4-22a7-4351-8334-975ccc61ec29" />

<img width="1886" height="943" alt="Screenshot 2026-11-25 153658" src="https://github.com/user-attachments/assets/e474d82e-3a4c-49a3-98b4-6514f298ad38" />

<img width="1892" height="950" alt="Screenshot 2026-11-25 153920" src="https://github.com/user-attachments/assets/b04822bf-dd5f-4a29-a5f1-62f1e5871592" />

<img width="1887" height="957" alt="Screenshot 2026-11-25 154108" src="https://github.com/user-attachments/assets/19e4b696-5b37-4fe4-b37b-108cd4d8352f" />

<img width="1888" height="960" alt="Screenshot 2026-11-25 154506" src="https://github.com/user-attachments/assets/789d1669-5072-4294-a97a-992146183048" />

<img width="1898" height="962" alt="Screenshot 2026-11-25 155450" src="https://github.com/user-attachments/assets/dfc6a0cf-e7c9-4f4a-8fea-5809c55d12be" />

<img width="1890" height="932" alt="Screenshot 2026-11-25 155438" src="https://github.com/user-attachments/assets/83ef7011-23db-40af-958e-d342c59b57a6" />

<img width="1901" height="966" alt="Screenshot 2026-11-25 155901" src="https://github.com/user-attachments/assets/e1c23740-661f-4b2e-9e47-2d1171d9fdb4" />

<img width="1917" height="968" alt="Screenshot 2026-11-25 160053" src="https://github.com/user-attachments/assets/e2aaf4cd-6f1e-48b0-bacb-5c4d9a992712" />

<img width="1902" height="952" alt="Screenshot 2026-11-25 160435" src="https://github.com/user-attachments/assets/04caead4-b100-45ff-8c95-7e6f38208f05" />



<img width="410" height="561" alt="Screenshot 2026-11-25 160535" src="https://github.com/user-attachments/assets/fa09b750-2708-4227-9a0c-681688894fdb" />





# RESULT
Thus, an AMI was created from a running EC2 instance, a Load Balancer was configured to distribute traffic across multiple instances, an Auto Scaling group was set up with a target tracking scaling policy, and the infrastructure was verified to automatically scale out under increased load using CloudWatch alarms.

