.. _application_checkin_kiosk:

Checkin Kiosk
=============

The Checkin Kiosk allows for students and attendees to checkin to events, career fairs, interviews, and appointments. Checkins are recorded in the system and can be reported on. Using the Checkin Kiosk requires the 'Launch Kiosk' permission.

Logging Out
-----------

When starting a checkin kiosk you will be prompted to either log out or stay logged in. Logging out ensures that the checkin kiosk can not be used to access the logged in user's details since the user who launches the checkin kiosk will be logged out immediately. We always recommend logging out when launching.

Drop-in Appointments
--------------------

In addition to normally scheduled appointments, drop-in appointments can and must be claimed and checked into using the checkin kiosk. For more information on drop-in appointments, see the :ref:`appointments <application_appointments>` page.

Waiting Room
------------

The Waiting Room feature can be used to display upcoming appointments, the staff member for that appointment, when the appointment is, and whether or not the student is checked in. This can be displayed in an advising waiting room for students to see.

Card Swipe Configuration
------------------------

Checkin Kiosks can be configured to read in card swipe data. Setting up card swipes is considered advanced configuration and may require contacting the Handshake team.

**Salting the Card Data**: We allow card data to be salted before hashing and doing the lookup.

**Card Regex**: In order to know which input is a card swipe and which is a normal username or email lookup, specify a regex for matching card swipes. If the input at a checkin kiosk matches this regex we will assume it is a card and only send the card data.

**Card Substring Regex**: An optional second regex used to determine what data to send to the server for matching. If specified, only the first string match of the swiped card data will be sent.

Security
--------
To securely look students up with possibly sensitive card ID's - Handshake and the University first agree on a salt to append to the card_id and when the card is swiped.  Handshake's application then appends this salt, hash the results, and then looks the student up based on that value.  This supposes that the university is also salting and hashing the card_id's they are sending to Handshake in there student sync.  Throughout the whole process the card id is never stored and security transmitted.  

+------+--------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+--------------------+
| Step | Process                                                                                                                                                | Where it Happens   | Security           |
+======+========================================================================================================================================================+====================+====================+
| 1    | With the kiosk page open, a user swipes their card and Handshake’s client side code applies a regex to the input validate that is indeed a card output | End User's Browser | Sent via HTTPS     |
+------+--------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+--------------------+
| 2    | Handshake applies a second regex to the output of first to get the card_id from the string                                                             | Handshake Server   | Card ID not stored |
+------+--------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+--------------------+
| 3    | Handshake’s server then appends the pre-defined salt and SHA-512 hashes the result (optional)                                                          | Handshake Server   | Card ID not stored |
+------+--------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+--------------------+
| 4    | Handshake then looks up the value returned on all the user’s card_ids. The card_id is not logged only the hash.                                        | Handshake Server   | Card ID not stored |
+------+--------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+--------------------+


Nametag Printing
----------------

Checking into an attendable allows for nametag printing and can be configured on a per-attendable basis. To use nametag printing for an attendable, enable name tag printing and specify the XML layout you'd like to use on the edit page. Label fields named 'Name', 'FirstName', 'LastName', 'Major', 'GradDate', and 'MajorGradDate' are supported. When the student checks in a nametag will automatically be printed.

.. note:: Nametag printing integrates with Dymo printers only at this time. For more information about Dymo printers please visit http://dymo.com.
