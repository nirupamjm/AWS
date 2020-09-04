## AWS SNS & SQS

#### Simple Notification Service (SNS)

* Fast,Flexible global messaging - Can deliver notification to any device or b/w various AWS resources
* Push Messaging Service 
* Publisher-Subscriber Model - Multiple publishing applications can talk to multiple subscribing applications
* Broadcast   - can send msgs to individual devices or broadcast mutiple destinations at once
* Supports Transport protocols- HTTP,HTTPS,emails,sms,Can push notifications to mobile apps

### AWS SNS Components

1. Topics : Identifies the content

2. Owners : Creators of the Topics

3. Subscribers : called Clients,Want to receive notification on specific topic. 

4. Publishers : called notification carrier.They send msg to topics,SNS matches the topic with the list of subscribers interested in the topic & delivers the msg to each one of them.

Syntax:

        aws sns create-topic --name kochu-topic

 A topic will be created & topic-arn will be displayed

        aws sns subscribe --topic-arn arn:aws:sns:sncfkljdsfks;ldfk;dsl --protocol email --notification-endpoint kochu123@gmail.com

A subscription mail will go the above mail

       aws sns list-subscriptions

will get all the subscription lists

       aws sns publish --topic-arn arn:aws:sns:sncfkljdsfks;ldfk;ds --message "This  is great"

Unsubscription 

     aws sns unsubscribe --subscription-arn arn:aws:sns:kmndfkjkdfldkflkdfl,flty

     aws sns list-topics 

     aws sns delete-topic --topic-arn arn:aws:sns:sncfkljdsfks;ldfk;ds

#### Simple Queuing Service (SQS)

* Distributed Queue System

* Supports both Standard & FIFO queues

* Reliable Service

* Simple - 3 imp API's called Send ,Receive & Delete msgs

* Secure - Secure Authentication & Authorization mechanisms

* Flexible & Scalable - can send /receive msgs at the same time

       aws sqs create-queue --queue-name kochuqueue --attributes file://createqueue.json

created a json file called createqueue.json already & add retentionperiod in there,explains the max time

#### Sending a msg in to our new queue

       aws sqs list-queues 

will list the queue list & it displays the queue url - https://sndfjsdfkjlfgkfdl;g

       aws sqs send-message --queue-url https://sndfjsdfkjlfgkfdl;g --message-body "This is example1"

Receive Message
      
       aws sqs receive-message --queue-url https://sndfjsdfkjlfgkfdl;g

Output:

        Messages

        {
 
        ReceiptHanldle:" nsfjnkdlgjklkgldfmgl,fdmg,mdflgm,dfmgmdfkgmkdfg"

          }

can not delete the messasge once it has been received to the received system. Receiver can delete the message before the visibility timeout

      aws sqs delete-message --queue-url https://sndfjsdfkjlfgkfdl;g --receipt-handle  nsfjnkdlgjklkgldfmgl,fdmg,mdflgm,dfmgmdfkgmkdfg

So that message will be deleted

Using Delay message attribute 

       aws sqs send-message --queue-url https://sndfjsdfkjlfgkfdl;g --message-body "This is example2" --delay-seconds 10

Delete queue

      aws sqs delete-queue --queue-url https://sndfjsdfkjlfgkfdl;g
