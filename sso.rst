.. _sso:

Single Sign On
===================

CAS:

=========== ==================================================== ============================================
Item        Description                                          Example
=========== ==================================================== ============================================
Login Path  The path a user should be sent to for authentication https://cashost:8443/cas-server-webapp/login
=========== ==================================================== ============================================

SAML:

==================== ===================================================== ======================================================
Item                 Description                                           Example
==================== ===================================================== =======================================================
Login Path           The path that a user should be sent to from our       https://idp.testshib.org/idp/profile/SAML2/Redirect/SSO 
                     application (the Service Provider) for authentication
name_id_format       See this article: http://stackoverflow.com/questions/ urn:oasis:names:tc:SAML:2.0:nameid-format:transient
                     11693297/what-are-the-different-nameid-format-used-fo
                     r
identifier           Which field in the user's record should we use to loo
                     k them up in the database? This field's value should 
                     correspond with the username of the Handshake user ui
                     d
IDP Cert Fingerprint A certificate of the public key for your IDP          0e82a794ce98b4c0e084fff4fc9514270cdb941a
==================== ===================================================== =======================================================

LDAP:

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
