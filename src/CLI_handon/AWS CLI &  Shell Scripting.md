### AWS CLI &  Shell Scripting

Launching an EC2 instances via AWS CLI

     Open ec2create.sh file & Paste it there

         aws ec2 run-instances --image-id ami-t5689772894 -count 1 --instance-type t2.micro --region ap-southeast-1 --iam-instance-profile Name="ecsInstanceRole" --subnet-id subnet-g23ey328u83

(This is the same cmd from previous lesson,just to show you the power of shell script to launch an EC2 over 7 or 8 clicks in console)

       sudo chmod 777 e2create.sh

 Now Execute

       ./ec2create.sh

#### Search all the running instances over every regions via AWS CLI using bash script

      sudo vim describeall-instances.sh 

Opening describeall-instances.sh

        #!/bin/bash
 
        for region in 'aws ec2 describe-regions --output text | cut -f3'

        do

        echo -e "\n Finding Instances in region :'&region'"

        aws ec2 describe-instances --region &region'"

        done

Setting Permissions

        sudo chmod 777 describeall-instances.sh

 Execute now 

        ./describeall-instances.sh

Will display all the EC2 instances running in each of the regions 

### Search AMI 

If we try to search AMI lists (From Community AMI's) it will take long time. 48,000 AMI's will be there. So it is difficult to find the AMI among this huge size.So we will use shell script to do the job easily.

      aws ec2 describe-images ,will display these 48,000 data

So we use AWS CLI & Bash script 

        sudo vim images.sh

Edit as below

        aws --region ap-southeast-2 ec2 describe-images --owners 099720109477 \
        --filters Name=root-device-type,Values=ebs \
        Name=architecture,Values=x86_64 \
        Name=name,Values='*hvm-ssd/Ubuntu-precise-12.04*' --query 'sort-by(Images, &Name) [-1].ImageId --output text

099720109477is the owner for canonical company which operates Ubuntu OS ,If we are using Windows AMI we should use owner id of Microsoft

We want the root vol value as ebs, 64 bit, exact version & latest one 

Save & Execute now 

       ./images.sh

        Output
        ami-f4654643

Will dispplay the exact AMI we need.
