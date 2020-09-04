# Task : Create a dynamodb table to store sensor values and fetch those data via Lambda and pass it through API Gateway
## Step 1: Create a dynamodb table to store sensor values like below

![image](https://user-images.githubusercontent.com/54981984/88796702-b858af80-d1bf-11ea-8252-c0a754b5562c.png)

### Solution: 
Creating Dynamodb table as below

![image](https://user-images.githubusercontent.com/54981984/89729677-a5629c80-da55-11ea-843c-d1a960e88e72.png)
![image](https://user-images.githubusercontent.com/54981984/91409849-a53f0b00-e863-11ea-8657-c6246ab8ede5.png)

### You can edit or add the values as "select any row --> select Actions-->Duplicate
![image](https://user-images.githubusercontent.com/54981984/89729690-c7f4b580-da55-11ea-837c-3ea118d453ab.png)

## Step 2: LAMBDA- Attaching Dynamodb via Lambda
Lambda fetches the table details from dynamodb using python code (in our case)
- Create Lambda function and attach IAM role which we already created
- IAM role should have below policies

   - Lambda_basic_execution
   
   - Dynamodb_read_access
   
![image](https://user-images.githubusercontent.com/54981984/89729697-de9b0c80-da55-11ea-8af8-1d34ab3a11bd.png)

-and add below code to the lambda function,so it will display the output from the table based on the condition which we have given

![image](https://user-images.githubusercontent.com/54981984/89729815-cd9ecb00-da56-11ea-9e0d-70f24669d837.png)

## Step 3: Trigerring API Gateway
In the design page of Lambda , there is an option called 'Add trigger' --> Select it

![image](https://user-images.githubusercontent.com/54981984/91474709-33dd7780-e8b8-11ea-8ab7-1dbc508fe5d6.png)
![image](https://user-images.githubusercontent.com/54981984/91474793-553e6380-e8b8-11ea-8a0a-22b9038ec3ec.png)

--Add required details there
![image](https://user-images.githubusercontent.com/54981984/91475020-9c2c5900-e8b8-11ea-9df7-a04c446f7f4f.png)

--Copy the endpoint url and paste it on browser

![image](https://user-images.githubusercontent.com/54981984/91475235-e9102f80-e8b8-11ea-99cc-d5e9d2a9e1d7.png)

![image](https://user-images.githubusercontent.com/54981984/91475338-1066fc80-e8b9-11ea-8d7a-a2fcfcef5cf7.png)

PS:- Below is the Python Lambda code which we used here

    import json
    import boto3
    from boto3.dynamodb.conditions import Key

    def lambda_handler(event, context):

	client = boto3.resource('dynamodb')
	table = client.Table('Sensor')
  
	response = table.get_item(
		Key = {
			'Sensor_id' : 3
        
		}
	)
	
	list = response['Item']
	print(list)
	R = list["Rainsensor"]
	H = list["Humidity sensor"]
	W = list["Waterlevel"]
	if (H > 50) and (W < 1005) and R ==5 :
		switch = 'on'
	else:
		switch = 'off'
  
	return(switch)

