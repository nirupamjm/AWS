## AWS CLI & AWS SES

### Simple Email Service(SES)

Traditional soln :- Purchase a server & load some mail server s/w on it

AWS SES :-

*  You only Pay For What You Use ...PAY-AS-YOU-GO

* Sending/Receiving email via AWS SES

* Cost effective Bulk Email Service :- Cost based on the number of emails send

* Requires Verified Email Addresses

* Send Rate of 1 Email/sec

* Send Quota of 200 Email per 24hr

* Available only in 3 AWS regions

       aws ses verify-email-identity --email-address teena@123 --region eu-west-1

A mail will go the above mail,once it got approved then the mail addresses verified.

        aws ses list-identities --region eu-west-1

will list the verified identities 

        aws ses send-email --from teena@123.com --to rikku@143.com --subject "Test Subject" --text "This is ses Demo"--region eu-west-1

An email will send from teena@123.com to rikku@143.com & msg is This is ses Demo

        aws ses get-send-quota --region eu-west-1

Will display the details of remaining mail left out (Total only 200 mails) 

