## AWS CLI & AWS ECS

### Elastic Container Service (ECS)

Amazon Elastic Container Service (ECS) is a cloud computing service in Amazon Web Services (AWS) that manages containers and allows developers to run applications in the cloud without having to configure an environment for the code to run in. It enables developers with AWS accounts to deploy and manage scalable applications that run on groups of servers -- called clusters -- through application program interface (API) calls and task definitions. Amazon ECS is a scalable service that is accessible through the AWS Management Console and software development kits (SDKs).

 ECS supports Docker, an open source Linux container service.

Amazon ECS allows developers to define their application by pulling the necessary Docker images and resources from Amazon ECR or other repositories. Once all the appropriate containers have been gathered, they are deployed, either on EC2 or AWS Fargate. Finally, Amazon ECS scales the application and continuously manages the availability of containers.

Amazon ECS involve managing microservices and handling batch jobs.

Amazon ECS has been helping systems managers and administrators sleep at night by providing automated deployment and rollback solutions, on demand scalability, and disaster recovery simplified.

#### ECS Clusters

       aws ecs create-cluster --cluster-name kochucluster

       aws ecs list-clusters

Before run any containers, we first have to create & register EC2 Instance into our cluster.AWS ECS uses EC2 instances as a underlying capacity to host our docker containers.

       aws ec2 run-instances --image-id ami-t5689772894 -count 1 --instance-type t2.micro --region ap-southeast-1 --iam-instance-profile Name="ecsInstanceRole" --subnet-id subnet-g23ey328u83

iam-instance-profile will pass the role info when the EC2 starts

Container instances that run agent requires an iam policy & role for the service to know the agents belong to you.This instance profile attached the appropriate role to our EC2 instance which gives it necessary permissions to interact with the ECS Service

Our Preferred AMI(ECS optimized image) is provided by AWS & it has preconfigured everything includes AWS ECS Container Agent & all the components necessary to run the EC2 instances & register it to the EC2 cluster. 

Otherwise if we use any other ami id ,we have to manually create an EC2 instance to host ECS containers- includes Installing AWS ECS Container Agent & some other configurations

       aws ecs list-container-instances --cluster default

Since we assigned the ECS role to our EC2 instance,AWS will automatically register our EC2 with the default ECS Cluster

#### Register an EC2 instance to a Custom Cluster - kochucluster in our case

    we should add user data value

      sudo vim mycluster

mycluster file 

       #!/bin/bash
       echo ECS_CLUSTER=kochucluster >> /etc/ecs/ecs.config

Syntax:

          aws ec2 run-instances --image-id ami-t5689772894 -count 1 --instance-type t2.micro --region ap-southeast-1 --iam-instance-profile Name="ecsInstanceRole" --subnet-id subnet-g23ey328u83 --user-data file://mycluster

           aws ecs list-container-instances --cluster kochucluster

           O/P - arn:aws:va7sf76d897g9dfujgbkdfjg9

Due to our user data configuration changes,the EC2 instances has been registered to the ECS Cluster

            aws ecs describe-container-instances --cluster kochucluster --container-instances va7sf76d897g9dfujgbkdfjg9

O/P shows the container instances registered in our cluster

Task definition

Defines containers which we want to run together.It allow us to specify CPU & Memory as well as docker concepts.Which containers to use & the repositories in which they are located? Which port should be open ?
Task definition is a Text file in json format which describes one or more containers that form our application

sudo vim taskdef.json

Opening taskdef.json

         {
        "containerDefinitions": [
          {
          "name": "sample-app",
          "image": "123456789012.dkr.ecr.us-west-2.amazonaws.com/aws-nodejs-sample:v1",
          "memory": 200,
          "cpu": 10,
           "essential": true
             }
            ],
            "family": "example_task_3",
           }

Task definition creation

        aws ecs register-task-definition --cli-input-json file://taskdef.json

Now the task definition created
   
       aws ecs list-task-definitions

       O/P : taskdefinition/example_task_3

####  Run a task in our ECS Cluster   

       aws ecs run-task --cluster default --task-definition example_task_3 --count 1

   List the tasks in cluster default

       aws ecs list-tasks --cluster default

Delete cluster

       aws ecs deregister-container-instance --container-instance snjdfkdjfgksdf --cluster kochucluster

snjdfkdjfgksdf is the container instance id which we copied from the console

Instance has been deregistered & INACTIVE state,Now we can delete the cluster

      aws ecs delete-cluster --cluster kochucluster 

will delete the cluster
