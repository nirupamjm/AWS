## AWS SSM Session Manager for Shell Access to EC2 Instances | Temporary SSH Credentials | Security 

### Step 1: Launch an instance with SSM agent preinstalled and attach an IAM role with AmazonSSMManagedInstanceCore permissions

![image](https://user-images.githubusercontent.com/54981984/96077386-4a25ae00-0ecd-11eb-90f7-a66750eabc99.png)

### Step 2: So that we can see the EC2 instance in SSM page under SESSION MANAGER

![image](https://user-images.githubusercontent.com/54981984/96077496-94a72a80-0ecd-11eb-9363-e07b28245a88.png)

### Step 3: We can access the EC2 by doing start session 

### Step 4: You can see the IP of the EC2 instance

![image](https://user-images.githubusercontent.com/54981984/96081167-5d894700-0ed6-11eb-88f8-6988c58ba62d.png)

#### We can edit preference like below and able to see session history 

![image](https://user-images.githubusercontent.com/54981984/96081799-b4435080-0ed7-11eb-8b50-001f114d6701.png)

![image](https://user-images.githubusercontent.com/54981984/96081830-c4f3c680-0ed7-11eb-969d-c8d10a75c338.png)

![image](https://user-images.githubusercontent.com/54981984/96081969-fff5fa00-0ed7-11eb-893e-52629cad4a7b.png)

### Step 5: Done with this. Next,we can just check it out more

![image](https://user-images.githubusercontent.com/54981984/96081090-316dc600-0ed6-11eb-9b63-34ca1702ead4.png)

We can see the list of s3 buckets or Ec2 instances if we attached the appropriate policies to the ec2 role,without configure iam user credentials

![image](https://user-images.githubusercontent.com/54981984/96080905-cf14c580-0ed5-11eb-8268-c7dc228ff70f.png)

![image](https://user-images.githubusercontent.com/54981984/96080982-f1a6de80-0ed5-11eb-8aa9-dbc9fe46a031.png)
