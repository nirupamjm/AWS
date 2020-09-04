## AWS CLI for AWS IAM (Identity & Access Management)

  * Core AWS services,It enables us rules to access right resources at right time for the right reasons.
  * Helps for Authentication & Authorization

#### List IAM Users
 
      aws iam list-users

#### Create IAM Users

      aws iam create-user --user-name kochu

#### Create IAM Group

       aws iam create-group --group-name kochugroup

  Adding user to this IAM Group

        aws iam add-user-to-group --user-name kochu --group-name kochugroup

  Display the group details

        aws iam get-group --group-name kochugroup 

#### IAM Authentication Methods

1. Username/ password 

2. Application Programming Interface(API) Access Keys

3. Multifactor Tokens

        1. aws iam create-login-profile --user-name kochu --password kochu123

        2. aws iam create-access-key --user-name kochu

        2.1 aws iam delete-access-key --username kochu --access-key-id AKIATAUSHCASJKACAP

        2.2 aws iam create-access-key --user-name kochu >> key.txt

New Access Key is created and it is saved in key.txt file

#### IAM Users/Groups Policy

         aws iam attach-group-policy --policy-arn arn:aws:iam::aws::aws:policy/AdminAccess --group-name kochugrp

         aws iam remove-user-from-group -group-name kochugrp

         aws iam detach-group-policy --policy-arn arn:aws:iam::aws::aws:policy/AdminAccess --group-name kochugrp

         aws iam delete-group --group-name kochugrp
