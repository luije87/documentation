.. _email_delivery:

Email Delivery
==============

Handshake maintains highly reputable emailing domains to ensure that emails are delivered. However, email delivery can sometimes fail due to the various systems in between Handshake and students which are designed to prevent email abuse. In order to maintain high deliverability, Handshake monitors and acts on spam scores, blacklisting, IP throttling and more.


Email Delivery Guidelines
-------------------------

Google
######

We recommend whitelisting all IP addresses in your google apps console for gmail as this will ensure no messages are flagged as spam.  Here are some general guidelines for bulk emailing from google: https://support.google.com/mail/answer/81126

Whitelisting
------------

Handshake sends a large amount of email notifications and depending on your school's use of the mass email feature, you should consider whitelisting handshake for more reliable email delivery. Whitelisting can better assure that emails sent to students and staff are received.

Whitelist by Domain
###################

Domain:  ``*.joinhandshake.com``

Whitelist by IP
###############

We send notifications from a dedicated set of IP addresses, you can whitelist these.

Regular Notifications are sent from: (notifications.joinhandshake.com)

* ``192.237.158.52``

Mass emails are sent from (mail.joinhandshake.com)

* ``192.237.159.131``
* ``192.237.159.132``

Whitelist by Email Address
##########################

We send from:

* ``handshake@notifications.joinhandshake.com``
* ``handshake@mail.joinhandshake.com``

It is possible to configure a custom reply-to email address, by default it is set to

* ``handshake@mail.joinhandshake.com``
* ``handshake@notifications.joinhandshake.com``
