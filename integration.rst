.. _integration:

Third Party Integration
===========

Handshake can be used as an identity provider for your application. This means that you can let Handshake users sign in to your application via their Handshake Account.
This documentation page is very early stage, and subject to change at any time.

Overview
--------
In order to integrate with Handshake, a secret key must be shared between Handshake and your application. Contact support@joinhandshake.com to discuss registering your application with the Handshake ecosystem and to receive your secret key.

It is important that you protect your secret key. This key is what your application uses to determine that the request is valid and from Handshake. If you ever feel there is a chance this key has been compromised, contact the Handshake team to be issues a new secret key for your application.

Handshake uses signed JTW tokens to pass directory information about users to your application.
You can read more about JWT at the following website:

`http://jwt.io/ <http://jwt.io/>`_

`JWT Spec <http://self-issued.info/docs/draft-ietf-oauth-json-web-token.html>`_

`JSON Web Token: The Useful Little Standard You Haven't Heard About <http://www.intridea.com/blog/2013/11/7/json-web-token-the-useful-little-standard-you-haven-t-heard-about>`_

Format
------
The decoded web token will contain the following data and keys::

  {  
    first_name: "Handshake",
    last_name: "User",
    email_address: "handshake_user@joinhandshake.com",
    id: "gid://handshake/User/1",
    institution_id: "gid://handshake/School/1",
    iat: xxxxx,
    exp: xxxxx
  }  

Offering your application to only a subset of users
---------------------------------------------------
Using the users's id, and institution_id, your application can make determinations about who it will offer its services to.
If you plan to do this, the Handshake team can work with you to provide special instructions when a user or institution enables their connection to your service, in order to have them provide their id to your system in a trusted way.
