### AWS CLI & AWS S3 (Simple Storage Service) : 

   1. Internet Accessible Storage

   2. Region Level Storage

   3. Almost Unlimited Scalability

   4. No File Locking Mechanisms

   5. Supports REST and SOAP API'sD

* Durability : 99.9999%

* Availability : 99.99%

* As small as 1 Byte and as large as 5 TB

* AWS S3 does not encrypt object's metadata

* Buckets contain a group of Objects/Files

* Unique Bucket Name across AWS S3

### Create Bucket 

        aws s3 mb s3://MyBucket

### Upload Objects in Bucket

        aws s3 cp C:\Desktop\testfile s3://MyBucket --recursive

        aws s3 cp C:\Desktop\testfile s3://MyBucket --storage-class STANDARD_IA

### List Buckets

        aws s3 ls s3://MyBucket

### Moving S3 Objects

      aws s3 mv s3://MyBucket . --recursive

      aws s3 mv . s3://MyBucket --recursive --exclude '*' --include '*.txt'

### Sync S3 Objects

      aws s3 sync . s3://MyBucket 

### Delete objects 

      aws s3 sync . s3://MyBucket --delete (delete the objects if we delete it from local system)

### Permission Granting - ACL 
 
      touch test.txt    - Create a file named "test.txt"

      aws s3 sync . s3://MyBucket --acl public-read  - Granting permission for everyone to read the objects

### Remove Objects(rm)/Remove Bucket(rb)

     aws s3 rm s3://MyBucket/test

     aws s3 rb s3://MyBucket --force - Remove all the objects & finally remove the bucket 


### S3 Storage types

Standard Storage

Reduced Redudancy Storage

S3 Standard-Infrequent Access

Amazon S3 Glacier Deep Archive
