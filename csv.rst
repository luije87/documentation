.. _csv:

CSV Upload
=================

Users
-----

Fields
******

========================== ==================================================================
Key                        Value
========================== ==================================================================
*First Name:               First name of user
*Last Name:                Last name of user
*Email:                    Email of user
*SSO Identifier:           Username of user 
Work Authorization         One of "U.S. Citizen", "Student (F-1) Visa", "J-1 Visa (Exchange Program)", "Permanent U.S. Resident", "Employment (H-1) Visa"
Mobile Number:             Mobile number. Optionally used for notifications.
Bio:                       Mostly used for staff members and mentors.
School Year:               One of "First Year", "Sophomore", "Junior", "Senior", "Graduate", "Post Graduate", "Alumni"
Work Study:                One of "true", "false"
Majors:                    semi-colon separated strings
Minors:                    semi-colon separated strings
Departmental GPA:          Decimal value
Cumulative GPA:            Decimal value
Time Zone:                 The time zone that this user is in. See time zones section for more details.
Disabled:                  Pass true if this student should not be able to login
Work Study Eligible:       Pass true if this student is eligible for work study jobs
Is Public:                 Pass false if this student's profile should not be viewable by approved employers
========================== ==================================================================

*required