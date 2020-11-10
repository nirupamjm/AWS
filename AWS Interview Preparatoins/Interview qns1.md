## Qn) EBS vs EFS vs S3

The main differences between EBS and EFS is that EBS is only accessible from a single EC2 instance in your particular AWS region, while EFS allows you to mount the file system across multiple regions and instances. Finally, Amazon S3 is an object store good at storing vast numbers of backups or user files.

![image](https://user-images.githubusercontent.com/54981984/98623479-c75c0b80-2331-11eb-87eb-1b724e8d45bf.png)

## Qn)
![image](https://user-images.githubusercontent.com/54981984/98623744-59fcaa80-2332-11eb-9dfb-d92a8055ba7b.png)

## Qn)
![image](https://user-images.githubusercontent.com/54981984/98624015-e4450e80-2332-11eb-9044-d9ef910af444.png)

Used when same components are used in multiple templates,instead of repeating same configuration we can reference it using Nested CF

Special Plolicy - Deletion policy of the nested stack is set to Retain

## Qn) 
![image](https://user-images.githubusercontent.com/54981984/98624393-b7ddc200-2333-11eb-8339-417f6201b8fc.png)

## Qn)
![image](https://user-images.githubusercontent.com/54981984/98624958-d1333e00-2334-11eb-9b69-b425d87c5150.png)

To create a metric filter using the CloudWatch console 

For more info to create metric in CloudWatch- https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/FindCountMetric.html

## Qn)  How Can  we prevent DDos attacks in AWS

Ans : -  To protect your web application against DDoS attacks, you can use AWS Shield, a DDoS protection service that AWS provides automatically to all AWS customers at no additional charge

There are two tiers of AWS Shield - Standard and Advanced.

All AWS customers benefit from the automatic protections of AWS Shield Standard, at no additional charge. AWS Shield Standard defends against most common, frequently occurring network and transport layer DDoS attacks that target your web site or applications. When you use AWS Shield Standard with Amazon CloudFront and Amazon Route 53, you receive comprehensive availability protection against all known infrastructure (Layer 3 and 4) attacks.

For higher levels of protection against attacks targeting your applications running on Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator and Amazon Route 53 resources, you can subscribe to AWS Shield Advanced


## Qn) 
![image](https://user-images.githubusercontent.com/54981984/98625753-45baac80-2336-11eb-9774-a6ebba326b34.png)

![image](https://user-images.githubusercontent.com/54981984/98625783-51a66e80-2336-11eb-83f4-a62a565e8ee4.png)

