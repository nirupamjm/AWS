# Copy S3 bucket objects across AWS accounts

## Prerequisites
## •	Two AWS accounts (One for source s3 bucket and another for destination s3 bucket)
## •	Create an IAM user in destination AWS account
## •	Configure AWS CLI in local machine with previously created IAM user credentials 

### Step 1: Get the 12 digit destination AWS account number 
Sign in to the destination AWS account .Go to SupportSupport Center and copy account number from there 

### Step 2: Set up the source S3 bucket 
Sign in to the source AWS account. Create a bucket in s3. Upload some test files which are meant to be copied automatically to destination account .Attach the following policy to the bucket.

`{`
	    `"Version": "2012-10-17",`
	    `"Statement": [`
	        `{`
	            `"Sid": "DelegateS3Access",`
	            `"Effect": "Allow",`
	            `"Principal": {`
	                `"AWS": "arn:aws:iam::DESTINATION_BUCKET_ACCOUNT_NUMBER:root"`
	            `},`
	            `"Action": [`
	                `"s3:ListBucket",`
	                `"s3:GetObject"`
	            `],`
	            `"Resource": [`
	                `"arn:aws:s3:::SOURCE_BUCKET_NAME/*",`
	                `"arn:aws:s3:::SOURCE_BUCKET_NAME"`
	            `]`
	        `}`
	    `]`
	`}`

### Step 3: Set up destination s3 bucket
Sign in to the destination AWS account. Create a bucket in s3

## Step 4: Attach policy to IAM user in destination AWS account
Attach the following policy to the IAM user created previously in the destination account.
`	{`
	    `"Version": "2012-10-17",`
	    `"Statement": [`
	        `{`
	            `"Effect": "Allow",`
	            `"Action": [`
	                `"s3:ListBucket",`
	                `"s3:GetObject"`
	            `],`
	            `"Resource": [`
	                `"arn:aws:s3:::SOURCE_BUCKET_NAME",`
	                `"arn:aws:s3:::SOURCE_BUCKET_NAME/*"`
	            `]`
	        `},`
	        `{`
	            `"Effect": "Allow",`
	            `"Action": [`
	                `"s3:ListBucket",`
	                `"s3:PutObject",`
	                `"s3:PutObjectAcl"`
	            `],`
	            `"Resource": [`
	                `"arn:aws:s3:::DESTINATION_BUCKET_NAME",`
	                `"arn:aws:s3:::DESTINATION_BUCKET_NAME/*"`
	            `]`
	        `}`
	    `]`
	`}`
### Step 5: Sync s3 objects to destination 
If above steps are completed, we can copy s3 bucket objects from source account to destination account by using the following AWS CLI command.

`aws s3 sync s3://SOURCE-BUCKET-NAME s3://DESTINATION-BUCKET-NAME --source-region SOURCE-REGION-NAME --region DESTINATION-REGION-NAME`

Note : 
The above command should be executed with destination AWS IAM user account credentials only otherwise the copied objects in destination S3 bucket will still have the source account permissions and won’t be accessible by destination account users.



 




 
