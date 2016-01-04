.. _sso:

Single Sign On
===================
If you are attempting to do single sign on with Handshake, please check your Teamwork account for the form link to submit the Single Sign on Details we need.

CAS
---

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
----

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
----

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

