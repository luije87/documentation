.. _data_transfer.rst:

Data Transfer FAQ
=================

Why do you use Amazon S3?
-------------------------
In order to best provide for the security of your sensitive data, we make sure of secure Amazon AWS S3 buckets. These buckets are heavily secured with a rigorous access control policy.


What sort of encryption is used with the data?
----------------------------------------------
We use server side 256 bit AES. "Amazon S3 Server Side Encryption employs strong multi-factor encryption. Amazon S3 encrypts each object with a unique key. As an additional safeguard, it encrypts the key itself with a master key that it regularly rotates. Amazon S3 Server Side Encryption uses one of the strongest block ciphers available, 256-bit Advanced Encryption Standard (AES-256), to encrypt your data."
All encryption is transferred over SSL


How should I format my [student/staff/alumni] data?
---------------------------------------------------
An up-to-date format for CSV files is included here: :doc:`csv`
If you have any questions about formatting, or we don't have a field included that you require, let us know and we are more than happy to work with you to ensure we meet all of your needs.

Our preferred format is with all users together in one CSV, and a user type field indicating if they are student, staff, alum, etc. If this is not possible, and they must be separate files, let us know.


How do I transfer the data to my secure bucket?
-----------------------------------------------
The easiest way to transfer data is with the AWS CLI (http://aws.amazon.com/cli/)  

Install the AWS CLI

You should have received an 'Access Key ID' and a 'Secret Access Key' from the Handshake team.  

Type "aws configure" and follow the prompts to enter your Key ID and Secret Key mentioned above. Unless otherwise instructed by the Handshake team, you should use "us-east-1" as your region.  

You may choose any default output format you wish.  

For more information see this article.  

Once you have the CLI set up, uploading your data is as simple as issuing the following command::

  aws s3api put-object --bucket [your_bucket] --key uploads/users_[yyyymmdd].csv --body [/path/to/your_local_file]  

For example::

  aws s3api put-object --bucket hudson_university --key uploads/users_20140410.csv --body /tmp/student_dump20140410.csv

The AWS S3 API will respond with a document ID if the file was successfully transferred, otherwise it will respond with an error.  

If you wish to do a test run, simply change the prefix on the destination file key from uploads/ to test/  
