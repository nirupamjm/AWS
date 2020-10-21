## Lambda for sending mail with attachment using SES 

### Step 1: Create an IAM role with AWS SES full access and AWSLambdaExecute(which enable cloudwatch logs by default) permission

![image](https://user-images.githubusercontent.com/54981984/96745972-51285100-13e4-11eb-87a2-0368b09f5015.png)

### Step 2: Create a Lambda Function by attaching the IAM role which we created and use the below code in the function
     
  Refer below link for accessing same code if you have any doubt in this 
      
  https://github.com/srcecde/aws-tutorial-code/blob/master/lambda/lambda_s3_event_ses_attach_email.py
      
    import boto3
    from email.mime.multipart import MIMEMultipart
    from email.mime.text import MIMEText
    from email.mime.application import MIMEApplication

    def lambda_handler(event, context):
    
    ses = boto3.client("ses")
    s3 = boto3.client("s3")

    for i in event["Records"]:
        action = i["eventName"]
        ip = i["requestParameters"]["sourceIPAddress"]
        bucket_name = i["s3"]["bucket"]["name"]
        object = i["s3"]["object"]["key"]

    fileObj = s3.get_object(Bucket = bucket_name, Key = object)
    file_content = fileObj["Body"].read()

    sender = "mail@mail.com"
    to = "mail@mail.com"
    subject = str(action) + 'Event from ' + bucket_name
    body = """
        <br>
        This email is to notify you regarding {} event.
        The object {} is uploaded.
        Source IP: {}
    """.format(action, object, ip)

    msg = MIMEMultipart()
    msg["Subject"] = subject
    msg["From"] = sender
    msg["To"] = to

    body_txt = MIMEText(body, "html")

    attachment = MIMEApplication(file_content)
    attachment.add_header("Content-Disposition", "attachment", filename=object)

    msg.attach(body_txt)
    msg.attach(attachment)

    response = ses.send_raw_email(Source = sender, Destinations = [to], RawMessage = {"Data": msg.as_string()})
    
    return "Thanks"
    
  Save or Deploy this code 
    
 ## Step 3: Create a bucket and add event notification as our requirement by selecting our lambda function which we created. eg: if we enable PUT and delete any object ,it will make you notify you by email)
 
 ![image](https://user-images.githubusercontent.com/54981984/96747909-80d85880-13e6-11eb-9d2b-c266302c7bc4.png)
 
 ## Step 4: Try it by uploading and deleting some object from the particular bucket and it will trigger lambda to send mail to the owners
 
 -------------------------------------------------------------------------------------------------------------------------------------------------------------
 
 ## Same usecase by sending simple mail to the user by invoking Lambda function with SES by Test'ing lambda (Without triggering it)
 
 ## Step 1: Create an IAM role with AWS SES full access and AWSLambdaExecute(which enable cloudwatch logs by default) permission
 
 ## Step 2: Create a Lambda Function by attaching the IAM role which we created and use the below code in the function
 
    import boto3
    def lambda_handler(event, context):
    ses = boto3.client('ses')

    body = """
        Hello Teena , Hope you are doing great!
 
        Thanks,
        Kochu
     
    """
    ses.send_email(
        Source = 'teenasusan09@gmail.com',
        Destination ={
            'ToAddresses': [
                'teenakochu@gmail.com',
            ]
        
        },
        Message={ 
            'Subject': {
                'Data': 'SES Demo',
                'Charset': 'UTF-8'
            },
            'Body': {
                'Text': {
                    'Data': body,
                    'Charset': 'UTF-8'
                }
            }
        }
    )
    
    ## Step 3: Deploy and Test the lambda function and you can check the inbox for your simple mail which we created via lambda
    
