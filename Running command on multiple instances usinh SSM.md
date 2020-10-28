## Running command on multiple instances usinh SSM

### Launch multiple instances with required permission in IAM role (AmazonSSMManagedInstanceCore) . So that those are available in System Manager under RUN COMMAND option

![image](https://user-images.githubusercontent.com/54981984/96219667-f1c1df80-0fa4-11eb-9d90-aa037de53ea4.png)

### Select required document to run

![image](https://user-images.githubusercontent.com/54981984/96219767-29308c00-0fa5-11eb-814d-2b0f32f59775.png)

### We have to open port 80 to the inbound rule of the attached instances (In our case: default SG is attached to all instances)

without 80 port

![image](https://user-images.githubusercontent.com/54981984/96220187-e7ecac00-0fa5-11eb-9fc9-52cd12db2e45.png)

attach port 80, so that we can see the command working via browser

![image](https://user-images.githubusercontent.com/54981984/96220035-a3f9a700-0fa5-11eb-9bed-ea21cb6670f1.png)

OPTIONAL 

Targets & Errors 

![image](https://user-images.githubusercontent.com/54981984/96220411-503b8d80-0fa6-11eb-8a7b-f595f35514d5.png)

command which have to run on our ec2 instances

![image](https://user-images.githubusercontent.com/54981984/96220567-9133a200-0fa6-11eb-90e7-117be9f26541.png)

s3 and cloudwatch

![image](https://user-images.githubusercontent.com/54981984/96220821-1ae36f80-0fa7-11eb-9e41-84f91ec32d28.png)

CLI 

![image](https://user-images.githubusercontent.com/54981984/96220979-60a03800-0fa7-11eb-8cf9-15b1c38837e5.png)

CMD RERUN and open the instance IP in browser now. We can see that Apache is installed in our EC2 instances

![image](https://user-images.githubusercontent.com/54981984/96221368-1ff4ee80-0fa8-11eb-8e82-7a6da7673190.png)

page is running-just have to open port 80 & write command properly





