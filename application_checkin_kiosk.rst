.. _application_checkin_kiosk:

Checkin Kiosk
=============

The Checkin Kiosk allows for students and attendees to checkin to events, career fairs, interviews, and appointments. Checkins are recorded in the system and can be reported on.

Logging Out
-----------

When starting a checkin kiosk you will be prompted to either log out or stay logged in. Logging out ensures that the checkin kiosk can not be used to access the logged in user's details since the user who launches the checkin kiosk will be logged out immediately. We always recommend logging out when launching.

Drop-in Appointments
--------------------

In addition to normally scheduled appointments, walk-in appointments can and must be claimed and checked into using the checkin kiosk. For more information on drop-in appointments, see the :ref:`appointments <application_appointments>` page.

Waiting Room
------------

The Waiting Room feature can be used to display upcoming appointments, the staff member for that appointment, when the appointment is, and whether or not the student is checked in. This can be displayed in an advising waiting room for students to see.

Card Swipe Configuration
------------------------

Checkin Kiosks can be configured to read in card swipe data. Setting up card swipes is considered advanced configuration and may require contacting the Handshake team.

**Salting the Card Data** We allow card data to be salted before hashing and doing the lookup.
**Card Regex** In order to know which input is a card swipe and which is a normal username or email lookup, specify a regex for matching card swipes. If the input at a checkin kiosk matches this regex we will assume it is a card and only send the card data.
**Card Substring Regex** An optional second regex used to determine what data to send to the server for matching. If specified, only the first string match of the swiped card data will be sent.

