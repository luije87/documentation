.. _application_appointments:

Appointments
============

Appointments can be scheduled, tracked, and reported on in Handshake. We provide an interface for students to request appointments within constraints specified by advisors. Advisors can override constraints and manage appointments with students. Appointments can be restricted to a subset of students using :ref:`student permissions <application_student_permissions>`.

..note:: Appointments have a one-click report download option. Filter down to the relevant items and click the download button to quickly generate a report.

Settings
--------

Categories and Types
####################

As an administrator you can configure the categories and types of appointments. Categories are the first level of categorization of appointments. If you have no categories, the option will be removed in the interface. Otherwise students will be prompted to choose a category before choosing a type.

Each appointment is associated with an appointment type. Appointment types can belong to many categories.

.. note::  Common examples of appointment types are 'Resume Review', 'Mock Interview' or 'Career Exploration'

Advisors each are required to specify the type of appointments that they are able to schedule appointments for.

Media
#####

Appointment media specify how the appointment takes place. Examples may be 'Face to Face' or 'Phone Call'.

Scheduled vs. Drop-in Appointments
----------------------------------

There are core types of appointments in Handshake: Scheduled and Drop-in appointments. Scheduled appointments are scheduled and requested before the student arrives. Scheduled appointments have reminders sent out ahead of the appointment to the student and shows on their calendar for reference. They can also be cancelled, if needed. Drop-in appointments cannot be scheduled ahead of time and as a result do not have reminders. Drop-in appointments are recorded as a full appointment record, similarly to scheduled appointments.

Appointment Blocks
------------------

Appointment blocks specify an advisor's availability. Students will only be allowed to book appointments during availability.

Options
#######

When setting up appointment blocks, options include:

**Day of Week** What day of week is this block for?
**Start and End Time** For the day of week picked, what is the start and end time for this block?
**Drop-in** Is this a drop-in appointment? Drop-in appointments cannot be scheduled ahead of time.
**Repeating** Is this a repeating (weekly) block?
**Start and End Date** If it is repeating, specify when the repeating starts and ends. The block will not be repeated outside of those dates.


Notifications
-------------

Throughout the appointment scheduling process and leading up to the appointment, notifications are sent to the student. Notifications are sent:

* When the appointment is successfully scheduled.
* A 24 hour warning
* A one hour warning
* If the appointment is recorded as a 'no show'.
