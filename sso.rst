.. _sso:

Single Sign On
==============
If you are attempting to do single sign on with Handshake, please check your Teamwork account for the form link to submit the Single Sign on Details we need.

Integration Guide 
-----------------

Getting Started
***************

Fill out our survey here and start the conversation with one of our integration engineers: https://joinhandshake.wufoo.com/forms/handshake-single-sign-on-information/

FAQs
****

Do we support SAML?

- Yes

Do we support InCommon, and if so, is it required?

- No it is not required, but prefered

Do we support LDAP?

- Yes

Do we support CAS?

- Yes 

Who are the users?  

- Students, Career Services, and sometimes faculty

Is the scope is limited to a certain group of users, how does Handshake determine authorization?  By provisioning, attribute check, or group membership?

- We limit access based on provisioning, we do not use group membership or any other attributes other then a uid to look the user up

What are the required attributes?

- The attribute value sent must match the user's username or auth_identifier 

How are users provisioned for Handshake?

- Users can be provisioned in three ways:

1. Imported vs CSV upload
2. Via the API
3. Have accounts created and approved in the Handshake UI via user signup process

What is our entityID? 

- https://app.joinhandshake.com/sp

Where can I get a copy of Handshake's Metadata?

- If you are on InCommon, see the metadata extract: http://md.incommon.org/InCommon/InCommon-metadata.xml
- If you are not on Incommon, you can download here: https://drive.google.com/file/d/0B-83VSAMe8ddNUhiTjVTUUx4V1U/view

How can I setup SSO with Handshake?

- Start by filling out the form and someone will be in contact with you

Supported Integrations
----------------------

CAS
***

=========== ==================================================== ============================================
Item        Description                                          Example
=========== ==================================================== ============================================
Login Path  The path a user should be sent to for authentication https://cashost:8443/cas-server-webapp/login
=========== ==================================================== ============================================

If you need to whitelist our 'service' or 'system', please whitelist:

*  ``*app.joinhandshake.com/*``
*  ``*yourschoolname.joinhandshake.com/*``

If you can not whitelist our domains and require a static IP address, please reach out and we can get this setup for you but this configuration is very rare.

SAML
****

If you are an Incommon Member you can use our entityID https://app.joinhandshake.com/sp

==================== ===================================================== =======================================================
Item                 Description                                           Example
==================== ===================================================== =======================================================
Login Path           The path that a user should be sent to from our       https://idp.testshib.org/idp/profile/SAML2/Redirect/SSO 
                     application (the Service Provider) for authentication
name_id_format       See this article:                                     urn:oasis:names:tc:SAML:2.0:nameid-format:transient 
                     http://stackoverflow.com/questions/11693297
identifier           Which field in the user's record should we use to loo
                     k them up in the database? This field's value should 
                     correspond with the username of the Handshake user ui
                     d
IDP Cert Fingerprint A certificate of the public key for your IDP          0e82a794ce98b4c0e084fff4fc9514270cdb941a
==================== ===================================================== =======================================================

LDAP
****

================ ================================================================================================== =====================================
Item             Description                                                                                        Example
================ ================================================================================================== =====================================
Host             The LDAP server host                                                                               https://ldap.myserver.com
Port             The port that LDAP is using for incoming requests                                                  636
Service Username The user our system should be using to perform LDAP searches                                       CN=Handshake,CN=Users,dc=test,DC=edu
Service Password The password for authenticating the above user                                                     dontuseaweakpassword
Base DN          The DN we should search in for the user that is logging in                                         OU=Students,dc=test,dc=edu
Filter           Which field should correspond with the login name they use                                         (uid={{login}})
Firewall?        Is your system behind a firewall that will need us to provide a static IP for whitelisting?        yes/no
================ ================================================================================================== =====================================

You may need to whitelist Handshake's IP addresses to access your ldap server please allow the following IPs:

*  ``54.88.136.216``
*  ``54.84.188.199``

