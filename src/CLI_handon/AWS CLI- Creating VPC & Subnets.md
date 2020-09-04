## Creating VPC & Subnets

It is to show you the power of shell script to launch an VPC & Subnets over 7 or 8 clicks in console 

        sudo vim createvpc.sh

Add below

        vpcid='aws ec2 create-vpc --cidr-block 10.0.0.0/16 --output text | cut -f7'

        echo -e "$vpcid"

        aws ec2 create-subnet --vpc-id "$vpcid" --cidr-block 10.0.1.0/24

        aws ec2 create-subnet --vpc-id "$vpcid" --cidr-block 10.0.2.0/24

& Run 

       ./createvpc.sh

It will create the new subnets under the VPC which created now
