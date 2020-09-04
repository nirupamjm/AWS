## AWS CLI & AWS ELB (Elastic Load Balancer)

Monitor healthy EC2 instances and route the traffic accordingly

Types of ELB

1. Classic Load Balancer -Works at Transport Layer 
2. Application Load Balancer - Works at Application Layer ,Support only http,https protocol
3. Network Load Balancer - Works at Network Layer,Supports TCP,TLS

### Application Load Balancer

 After the load balancer receives a request, it evaluates the listener rules in priority order to determine which rule to apply, and then selects a target from the target group for the rule action. You can configure listener rules to route requests to different target groups based on the content of the application traffic

       aws elbv2 create-load-balancer --name kochuLoad1 --subnets subnet-bdf23234534 --security-group sg-2sgvdhgsdfhsdh

### Target Groups 

Entity within the AWS Cloud Infrastructure.Which groups all the targets that are present in the backend of the LB.The LB routes the req to the target, registered with the target group based on the LB Rules.Target could be an EC2/ECS Container service or any services which can accept req frm ELB.

 The load balancer also monitors the health of its registered targets and ensures that it routes traffic only to healthy targets. You configure your load balancer to accept incoming traffic by specifying one or more listeners, which are configured with a protocol and port number for connections from clients to the load balancer.

        aws elbv2 create-target-group --name kochutargetgroup --protocol HTTP --port 80 --vpc-id vpc-4cdjsdfn

Next we have to register target group using regsiter-target command with created arn of the target group

         aws elbv2 register-targets --target-group-arn arn:aws:sdjfhsjhfiejkfls

### Listener

Process that check for connection req,using the protocol and port that you configure. The rules that you define for a listener determine how the load balancer routes requests to its registered targets. 

For Classic ELB, listener supports HTTP,HTTPS,TCP,SSL

For Application ELB, listener supports HTTP,HTTPS

While creating Application LB ,Listener create separately and register them without LB

       aws elbv2 create-listener --load-balancer-arn arn:aws:ddfdfdffsfsdfdsgdf --protocol HTTP --port 80 --default Type=forward,TargetGroupArn=arn:aws:sdvdfgdfgfd

   Target group health status checking 
   
        aws elbv2 describe-target-health --target-group-arn arn:aws:sdfdgdfgdfgdf

Delete ELB

        aws elbv2 delete-load-balancers --load-balancer-arn arn:aws:sdbfsjdfhjsdh

Delete TargetGroup

       aws elbv2 delete-target-group --target-group-arn arn:aws:egwruwhfjknekf

### Classic Load Balancer

While creating Create LB ,we can create listener with them .

Syntax:

       aws elb create-load-balancer --load-balancer-name kochulb --listeners "Protocol=HTTP,LoadBalancerPort=80,InstanceProtocol=HTTP,InstancePort=80" --subnets subnet-3bdjnsdfjsd --security-groups sg-3shgdkjsdf

Protocol & LoadBalancerPort are frontend protocol - Connection b/w client to LB via HTTP & 80

InstanceProtocol & InstancePort are backend protocols- Connection b/w elb & the instance will be via HTTP & Port 80 

      aws elb describe-load-balancers

will display all the classic LB

### Internal Classic Load Balancers - It will route traffic internally

When you create a load balancer in a VPC, you must choose whether to make it an internal load balancer or an Internet-facing load balancer.

The nodes of an Internet-facing load balancer have public IP addresses. The DNS name of an Internet-facing load balancer is publicly resolvable to the public IP addresses of the nodes. Therefore, Internet-facing load balancers can route requests from clients over the Internet

The nodes of an internal load balancer have only private IP addresses. The DNS name of an internal load balancer is publicly resolvable to the private IP addresses of the nodes. Therefore, internal load balancers can only route requests from clients with access to the VPC for the load balancer.

Syntax:

       aws elb create-load-balancer --load-balancer-name elbkochuinternal --listeners "protocol=HTTP,LoadBalancerPort=80,InstanceProtocol=HTTP,InstancePort=80" --scheme --internal --subnets subnet-3bdjnsdfjsd --security-groups sg-3shgdkjsdf
       
An internal LB has been created & name starts like "internal" as DNS name

### Register /Deregister Instances to Internal or external LB

      aws elb register-instances-with-load-balancer --load-balancer-name elbkochuinternal --instances i-7bgjj4bjd 
      
 Instance has been registered
 
     aws elb deregister-instances-from-load-balancer --load-balancer-name elbkochuinternal --instances i-7bgjj4bjd
     
 Instance has been deregistered
 
 Delete LB (same syntax for both Internal/Exernal Load Balancers)
 
      aws elb delete-load-balancer --load-balancer-name elbkochuinternal
      
