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
