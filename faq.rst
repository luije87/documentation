.. _faq:

Frequently Asked Questions
============================
How safe, reliable and secure is your application?
--------------------------------------------------
We have had a strong focus on reliability and security since the beginning. We've worked with industry experts for the last two years to ensure we are building the application to a very high standard of excellence in security and reliability.

A quick overview of a few of our features:

* 99.9% Uptime Policy
* Automatic horizontal scaling and load balancing
* Distributed across multiple regions for high availability
* Granular level access control
* Globally distributed content delivery network
* Specific disaster response team designated to handle any incidents
* Backed up daily with redundant follower databases
* Backup restoration is regularly tested
* DDoS mitigation
* Caching across the application
* Over 1000 automated tests verify features are working and system is continuously secure
* SSL Security on all client to app and inter-app communications
* All production deployments pass through a rigorous change management process and testing procedure
* We do monthly exhaustive penetration tests against our application
* Production access is strictly controlled, logged and regulated
* Our infrastructure provider is compliant or has been audited under the following:

  * ISO 27001
  * SOC 1 and SOC 2/SSAE 16/ISAE 3402 (Previously SAS 70 Type II)
  * PCI Level 1
  * FISMA Moderate
  * Sarbanes-Oxley (SOX)

* The data centers we use are ISO 27001 and FISMA certified 
* Firewalls, port scanning protection, DDoS mitigation, etc is in place
* We offer at-rest encryption for all data in the system for an additional fee if this is required.
 

What SSO systems do you support out of the box?
-----------------------------------------------
We support SAML (and Shibboleth), LDAP and CAS. We are also more than happy to work with your to support your specific SSO solution if we do not already offer it.
More information: :doc:`sso`


How do we get student data into the system?
-------------------------------------------
There are two primary ways to get student data into the system, depending on your needs.

1. API 
   If you want to have a stronger degree of control over our data and when it is updated in the system, we have a RESTful API that you may use to update, delete, create and synchronize student/staff/alumni accounts.
   :doc:`api`

#. Simple CSV dump
   With the Simple CSV dump, we ask for an export of data from your student information system (ie Banner, DataTel, etc). We then have you push the data to our secured and sandboxed S3 environment. Pushing data to S3 is simple and over a secure connection with the AWS CLI or our small python script that uses the REST S3 API.
   All of your data that you send us on S3 is not readable by anybody except for a single account that we tightly monitor and control. Even if your own credentials are compromised, an attacker will not be able to access the data.
   Student sync data is encrypted in transit and at reset with AES 256 bit encryption

#. No student data import
   If you don't want to integrate with your student data, that is fine as well. Students can create their profiles from scratch, and can still parse resumes to help them build robust profiles quickly. 

For more information, see this document: :doc:`data_transfer`

 
Can we import data into the system?
-----------------------------------
We can work with you to help you export your data into a CSV format, and we can consume data from a CSV format into our system.

 
Do I need to dedicate any of my infrastructure for Handshake?
-------------------------------------------------------------
Handshake is provided as SaaS, so you do not need to dedicate any infrastructure to the application, besides what you need to send us up-to-date student data.

 
Does Handshake use SSL?
-----------------------
Yes, the production application forces SSL / TLS 1.2 to ensure that all interactions with the Handshake application are as secure as possible. The demo version of the application does not force SSL, and only test data should be used on the demo version.


Where can I find your terms of service and privacy policy?
----------------------------------------------------------
`Terms of Service <https://joinhandshake.com/tos/>`_

`Privacy Policy <https://joinhandshake.com/privacy/>`_
