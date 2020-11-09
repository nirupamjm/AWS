# AWS Best Practicses

## 01) EC2 Pratices

## 02) IAM Practices

## 03) S3 Practices

## 04) Security Practices

## 05) Billing Practices

## EC2 Best Practices

### 01) AMI Hardening- Hardeniung AMI means,it includes all the security best practices implemented on it

#### Just as any normal server, attacker can attempt to break into Amazon EC2 instance too.
#### Hardening is a process that prevents such possible attacks on the server. It involves disabling unwanted services, ports, restricting access on the instance, remove weak programs, etc.

![image](https://user-images.githubusercontent.com/54981984/98500941-d1b7d000-2273-11eb-8ad1-c020857c67e9.png)

### 02) VPC Port Lockdown - VPC allows to communicate different ec2 servers which is running same application

![image](https://user-images.githubusercontent.com/54981984/98501139-628eab80-2274-11eb-8145-9cb381b971de.png)

### 03) Private Subnets

![image](https://user-images.githubusercontent.com/54981984/98501696-fb71f680-2275-11eb-87a8-6f592fb14478.png)

### 04) Micro-services Architecture

Single minute of downtime causes millions of loss.But when you using Micro-services Architecture,you can scale vertically or Horizontally each micro services without worrying about downtime.

![image](https://user-images.githubusercontent.com/54981984/98501814-47bd3680-2276-11eb-85f2-fbac0de6a0db.png)

### 05) Environment Based Keys

Make sure every envirtonment got a diferent keys.There is no need to a developer to get access to prod env.(If a single keys for every env) --See below

![image](https://user-images.githubusercontent.com/54981984/98503037-9f10d600-2279-11eb-843f-8f64c008d5c9.png)

### 06) LDAP Authentication

Lightweight Directory Access Protocol
LDAP (Lightweight Directory Access Protocol) is an open and cross platform protocol used for directory services authentication. 

If we change one user credentials in one LDAP server,it will reflect across all the machines

![image](https://user-images.githubusercontent.com/54981984/98503748-51956880-227b-11eb-95a5-a399ad73b197.png)

## IAM Best Practices

### 01) Role for Teams - Specify roles based on the Team which 

![image](https://user-images.githubusercontent.com/54981984/98504180-53136080-227c-11eb-8055-5224e983340f.png)

### 02) Read Only Access - For eg :- Provide read only access for new joiness,so that they won't mess up things

![image](https://user-images.githubusercontent.com/54981984/98504208-658d9a00-227c-11eb-99ec-6b73ab776db0.png)

### 03) Service Specific Access

![image](https://user-images.githubusercontent.com/54981984/98504081-1182b580-227c-11eb-8273-55131538d179.png)

## S3 Best Practices

### 01) Have Content Specific Names

### 02) Create Bucket Polices

### 03) Archive buckets to 'Glacier' -- If you have tons of data

### 04) Version your Objects --So that you don't lose any version of that file

## Security Best Practices

### 01) Never Share Root Account Details

![image](https://user-images.githubusercontent.com/54981984/98504729-b81b8600-227d-11eb-8d83-013bc2add128.png)

### 02) Remove Unwanted Users

![image](https://user-images.githubusercontent.com/54981984/98504777-d7b2ae80-227d-11eb-9af0-d8c281143c77.png)

### 03) Enable 2-factor Authentication

![image](https://user-images.githubusercontent.com/54981984/98504830-f749d700-227d-11eb-9d17-d6817acd3cd2.png)

### 04) Use IAM Logins

![image](https://user-images.githubusercontent.com/54981984/98504878-0b8dd400-227e-11eb-8fd8-3f1590ad5bcb.png)

## Billing Best Practices

Every company needs to reduce their bills.Here AMAZON introduces BILLING BUDGETS,IAM access to  Billing,Multi Account Consolidation

![image](https://user-images.githubusercontent.com/54981984/98500715-31fa4200-2273-11eb-97ab-502b104540d1.png)


