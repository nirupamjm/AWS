## AWS CLI 
### 1. Intro
* Filter- Server side
* Query-Client side
* Dry run-Checking status of the expected output(fail or success)
#### 1. JMESPath terminal- Shows specific output as needed
## filter command (server side)
        
        aws ec2 describe-instances --filter Name=instance-type,Values=t2.micro


## query command (client side/universal)

        aws ec2 describe-regions --query 'Regions[?RegionName==`eu-west-1`]'


## dry run

        aws ec2 describe-regions --dry-run


## --output 
        aws ec2 describe-regions --output table



## jmespath terminal 
        
        aws ec2 describe-regions | jpterm

exit -> ctrl+c


aws ec2 describe-instances --query 'Reservations[].Instances[].PrivateIpAddress'
### 2. AWS CLI- EC2 (Elastic Compute Cloud)
### * AWS EC2 Key Pair : Creating Key pair for data security
       
 Syntax :

      aws ec2 create-key-pair --key-name mykeypair --output text > mykeypair.pem
Output:

A key will be generate named mykeypair.pem

### * AWS EC2-Security Groups : Acts like firewall for EC2 instances

    * To create a security group for EC2-Classic

This example creates a security group named MySecurityGroup.

Command:

         aws ec2 create-security-group --group-name MySecurityGroup --description "My security group"

Output:
        
        {
        "GroupId": "sg-903004f8"
        }       
   *  To create a security group for EC2-VPC

This example creates a security group named MySecurityGroup for the specified VPC.

Command:

         aws ec2 create-security-group --group-name MySecurityGroup --description "My security group" --vpc-id vpc-1a2b3c4d

Output:
 
        {
        "GroupId": "sg-903004f8"
        }

 ### * AWS AMI & AWS VPC

   Amazon Machine Image(AMI) is the template of the EC2 instances that we intend to launch. It includes the template for root volumes for the instance (OS-linux/windows,Applications etc)

### Virtual Private Cloud(VPC) & Subnet-  Basic building block of the AWS Network Infrastructure
   (Refer AWS Networking class)

### *  Deploy AWS EC2 Instances using AWS CLI

Command:

        aws ec2 run-instances --image-id ami-0701e7be9b2a77600 --count 1 --instance-type t2.micro --subnet-id subnet- 1cecd954  --key-name awsclikey --security-group-id sg-0d29b119999959828

(ami-id)- ami of the EC2 Which we intend to launch 

(Subnet -id - Take the default VPC's subnet)

(Keyname & SG)- Which we created above

### AWS Elastic IP Address

Command:
        
        aws ec2 allocate-address

Output:

         `{`

         `"publicIp":"52.76.177.252",`

         `"Domain":"vpc",`

         `"AllocationId":"eipalloc-od422568"`

         `}`

#### Associate this Elastic IP to the instances
 
Command :

        aws ec2 associate-address --instance-id i-0a02e2f124e1a7449 --allocation-id eipalloc-od422568

Output:
       
        {
         "AssocaitionId":"eipassoc-e17e4385"
         }

#### Terminate EC2 Instances

       aws ec2 terminate-instances --instance-ids i-0a02e2f124e1a7449

       aws ec2 stop-instances --instance-ids i-0a02e2f124e1a7449

       aws ec2 start-instances --instance-ids i-0a02e2f124e1a7449
