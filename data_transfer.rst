.. _data_transfer.rst:

Data Transfer FAQ
=================

Why do you use Amazon S3?
-------------------------
AWS S3 is an industry standard for data storage and transfer.  In order to provide the best security of your sensitive data, we use a rigorous access control policy and encryption in transit and at rest.  Data can only be uploaded not read from AWS s3 and will only sit there for a short time before it is ingested into Handshake by an automated process.  

What setup do I have do on my end?
----------------------------------
You do not have to setup an s3 bucket or interact with amazon in any way other then using one of the many tools avaiable to upload to Handshake's s3 bucket and folder for your team.  We will provide you with the bucket, access id, secret key, and required prefix for uploding your file.  

What if I cant install python to use the aws cli?
-------------------------------------------------
The AWS cli is just interacting with the AWS s3 rest api, if you like, you can use any tool that can talk to a RESTful service such as curl.  This isnt recommended because it opens up more opportunities for errors.  See here for an example: http://tmont.com/blargh/2014/1/uploading-to-s3-in-bash 


What sort of encryption is used with the data?
----------------------------------------------
We use server side 256 bit AES. "Amazon S3 Server Side Encryption employs strong multi-factor encryption. Amazon S3 encrypts each object with a unique key. As an additional safeguard, it encrypts the key itself with a master key that it regularly rotates. Amazon S3 Server Side Encryption uses one of the strongest block ciphers available, 256-bit Advanced Encryption Standard (AES-256), to encrypt your data."
All data sent in transit is transferred over TLS. 


How should I format my [student/staff/alumni] data?
---------------------------------------------------
An up-to-date format for CSV files is included here: :doc:`csv`
If you have any questions about formatting, or we don't have a field included that you require, let us know and we are more than happy to work with you to ensure we meet all of your needs.


How do I transfer the data to my secure bucket?
-----------------------------------------------
The easiest way to transfer data is with the AWS CLI (http://aws.amazon.com/cli/)  

Install the AWS CLI

You should have received an 'Access Key ID' and a 'Secret Access Key' from the Handshake team.  

Type "aws configure" and follow the prompts to enter your Key ID and Secret Key mentioned above. Unless otherwise instructed by the Handshake team, you should use "us-east-1" as your region.  

You may choose any default output format you wish.  

For more information see this article.  

Once you have the CLI set up, uploading your data is as simple as issuing the following command::

  aws s3 cp [/path/your_local_file] s3://handshake-importer-uploads/[your folder]/[yyyymmdd]_users.csv] 

Hanshake has one aws bucket 'handshake-importer-uploads' and every school has a unique folder which comes after the bucket which they only have write access to upload files.

example upload::

  aws s3 cp 20140410_users.csv s3://handshake-importer-uploads/importer-production-hudson_university/20140410_users.csv 

example response::

  upload: to s3://handshake-importer-uploads/importer-production-hudson_university/20140410_users.csv

The AWS S3 API will respond with the document ID if the file was successfully transferred, otherwise it will respond with an error.  You can also check the command exit code to determine it it was successful.

If you wish to do a test run, simply send a file and our data team will verify that it is recieived and ready for production.


Can I whitelist s3 though my firewall?
--------------------------------------

There are a lot of IPs for s3 but they are updated here on a regular basis: https://ip-ranges.amazonaws.com/ip-ranges.json  (we only use the us-east-1 region)

If you do want to whitelist by domain: 

* ``https://s3.amazonaws.com/*``
