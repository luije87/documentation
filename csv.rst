.. _csv:

CSV Upload
=================

The easiest way to get data into Handshake is using the CSV upload. 
Below you will find tips, requirements, and an explanation of the different files.

File Requirements
-----

- All headers are case-sensitive; Must be downcased
- All preset values are case-sensitive; Casing varies
- File must be exported in .CSV format
- File must be exported in Unicode (UTF-8) 
Note: Not exporting to UTF-8 can cause bad encoding issues, which can lead to poorly translated records or failure to sync/import correctly. For information on how to export or convert your file to UTF-8, please see: http://help.meetedgar.com/article/107-help-how-do-i-export-my-spreadsheet-to-a-utf-8-encoded-csv


Staff
-----


Required Fields
******************
================================= ======================================================================================
CSV Header Value                  Value Description
================================= ======================================================================================
email_address                   Staff member's email address. In general this should be a .edu address
username                        Staff member's username. This MUST be unique and should not be something that changes
user_type                       Should be "Career Services"
auth_identifier                   This is the identifier that is required if you use Single Sign On.
================================= ======================================================================================

Recommended Fields
******************
============================= ==========================================================================================
Header                        Value
============================= ==========================================================================================
preferred_name                The staff member's preferred name
middle_name                   The staff member's middle name
gender                        The gender of the user. One of "Male", "Female", "Other", or blank (Not specified)
bio                           The staff member's bio
mobile_number                 The staff member's bio
role_names                    Applications;Applications and Outcomes;Articles;Career Fair;Career Fairs;Career Plans;Employer Approvals;Events;Experiences;External Feeds;Interview Schedules;Jobs;Launch Check-in Kiosk;Manage All Appointments;Manage Labels;Manage Own Appointments;Manage Staff;Manage Students;Mass Emails;Mentorships;Outcomes;Pins;Posts;Reports;Request Access to Schools;Rooms;Student Reviews;Surveys;Upload Attachments;View as Student;View Shared Notes
============================= ==========================================================================================


For an example file of the required fields `[Click Here] <https://docs.google.com/spreadsheets/d/14zOpFGwVc69mfVCscUsVwT_a1fX9Q9o_Lq_hsZPA3IQ/edit#gid=0>`_


Students
-----

For an example file of the suggested fields `[Click Here] <https://docs.google.com/spreadsheets/d/12jCXVRVE6hyPKVT69uuQ1z7rqSJXzjXmkr0Lj2UPaUw/edit#gid=0>`_

Format: TIMESTAMP_users.csv OR users.csv

Where TIMESTAMP is a single integer representing the time with smaller units further to the right.
Ex: 9:00:15 on 7/14/2014 => 201471490015_users.csv

Timestamps are optional, but can be used to make sure only the latest users list will be synced if the network connection is unreliable and causes two files originally uploaded at different times to show up on our system at the same time.


Required Fields
******************
================================= ======================================================================================
CSV Header Value                  Value Description
================================= ======================================================================================
email_address                     Student’s email address. In general this should be a .edu address
username                          Student’s username. This MUST be unique and should not be something that changes
user_type                         Defaults to "Students", one of "Students", "Career Services", "Mentors". user_type is case sensitive so it must be "Students". 
auth_identifier                   This is the identifier that is required if you use Single Sign On.
================================= ======================================================================================

Recommended Fields
******************
========================================= ==========================================================================================
Header                                    Value
========================================= ==========================================================================================
first_name                                Student’s first name
last_name                                 Student’s last name
school_year_name                          The name of student’s school year. For a list of acceptable values see the references section. Can only have one.
primary_education:education_level_name    This shows up on their main education on their profile. For a list of acceptable values see the references section.  Can only have one.
primary_education:cumulative_gpa          (Decimal) The student's cumulative GPA
primary_education:department_gpa          (Decimal) Decimal of student's departmental GPA
primary_education:major_names             (String Array) An array of major names for this student. Semicolon separated list. "major1";"major2";"major3" These must be majors configured in the school's majors list. 
primary_education:minor_names             (String Array) An array of minor names for this student. Semicolon separated list. "minor1";"minor2";"minor3" These must be minors configured in the school's minors list.
primary_education:college_name            (String) The college the student belongs to. Must be one of the colleges configured in the school's college list. Can only have one college
primary_education:start_date              (Date) The date the student started at the school in any standard date format. See references for date formats.
primary_education:end_date                (Date) The date the student graduated or plans to graduate school (can be blank if currently_attending is set). Must be after the education start date. See references for date formats.
primary_education:currently_attending     (Boolean) Should be set to true if education_end_date is blank. This signifies they are currently attending this school.
card_id                                   (String) Used for checking in students using a card swipe. This string must be contained in a card swipe output. Handshake can regex the direct output to match this value.
work_authorization_name                   One of "U.S. Citizen", "Student (F-1) Visa", "J-1 Visa (Exchange Program)", "Permanent U.S. Resident", "Employment (H-1) Visa", "TN Visa", "L1 Visa", "Work Card","H4 Visa"
ethnicity                                 The ethnicity of the user. Can only have one.  See the reference section for options.
gender                                    The gender of the user. One of "Male", "Female", "Other", or blank (Not specified)
========================================= ==========================================================================================

Optional Fields
******************************************************************************************************

Note: these fields generally add value to career services but are not required for normal operation.

========================================= ==================================================================
CSV Header Value                          Value Description
========================================= ==================================================================
preferred_name                            The student's preferred name
middle_name                               The student's middle name
recommended_authentication                One of "sso" or "standard". Allows you to suggest what type of authentication the user should use when logging in. (not currently active)
bio                                       A student's bio. Shown on the student profile. Visible to everyone who can see the profile.
skill_names                               Semi-colon separated list of skills. This generally should not be used in a sync.
external_link_urls                        Semi-colon separated list of external links for the profile
disabled                                  Pass true if this student should not be able to login and access Handshake.
work_study_eligible                       Pass true if this student is eligible for work study jobs
campus_name                               The name of the campus the student is at. Must be one of the campuses set up in your settings.
mobile_number                             The user's mobile phone number. The format should follow the following format: (999)999-9999 Ext:9999
system_label_names                        Semi-colon separated list of label names to apply to the user
profile_review_status                     This can be used to manage a students review status. Set this to "approved" if this student will not need a profile review. (Not relevant if profile review is not turned on for your school). All options: ['unsubmitted', 'pending', 'approved'].
document_review_status                    This can be used to manage a students document review status. Set this to "automatically_approved" if this student will not need documents approved. (Not relevant if document review is not turned on for your school). All options: ['no_pending_documents' 'pending_documents' 'automatically_approved']
========================================= ==================================================================


Training configuration fields
******************************************************************************************************

These are used only for trainings and demo setups.

============================== ==================================================================
role_names                     A semi colon separated list of roles to give to this user.
password                       Only used in demo environment for setting up trainings. Must match confirmation.
password_confirmation          Only used in demo environment for setting up trainings. Must match confirmation.
============================== ==================================================================

Mentor information params
******************************************************************************************************

These are nested inside of 'mentor_information_attributes' above

=================================== ==================================================================
Key                                 Value
=================================== ==================================================================
student_contact_preference          (String) Whether or not this mentor can be contacted by students. Either 'allowed' or 'not_allowed'
advice                              (String) Generic advice that this mentor has to offer
hobbies                             (String) Relevant hobbies that this mentor listed
expertise_names                     (String Array) An array of expertise that this mentor has. Will create if not already listed on school administrator page.
maximum_mentees                     (Integer) The maximum number of ongoing mentorships that this mentor is willing to do.
maximum_student_contacts_per_month  (Integer) The maximum number of messages that this mentor is willing to receive.
industry_name                       (String) The industry that this mentor is in. See references for possible values
=================================== ==================================================================


Handling Students who Graduate
******************************************************************************************************

+ Run a final sync before graduation that updates their school year status to Alumni


System Labels
******************************************************************************************************

System labels are labels that can only be applied during a sync, and can't be edited or removed on the UI. System labels are like private labels, and can only be seen by other staff members at the institution. System labels should be passed in as a semi-colon separated list of label names. If a label exists with the same name, it will be converted to a system label. If the system labels key is passed in but no label names are passed, it will remove all labels from the student. Similarly, if a student has a system label applied, but it is not present in the current sync, it will be removed from the student. If the system labels key is not passed, no existing labels will be removed from the student.

Contacts
--------

Contacts in Handshake are used to keep track of employers, alumni, and other individuals who may not have a username and password for Handshake. The most common use for importing
contact is to bring over employer relationships. Contacts can be labeled, sorted, tried to a Handshake employer, and more.

**Params**

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
\*first_name                        The first name of the contact (String)
\*last_name                         The last name of the contact (String)
\*email_address                     The email of the contact (String)
title                               The title of the contact (String)
description                         A description of the contact (Text)
employer_id                         The Handshake id of the employer that you want to list the contacts for (int)
employer_name                       The name of the employer that you want to list the contacts for (String)
location_attributes:name            The name of the location of the contact. NOTE: creates only.
phone                               The contact's phone number
cell_phone                          The contact's cell number
fax                                 The contact's fax machine number
=================================== ==================================================================

\* Required

For an example file of the suggested fields `[Click Here] <https://docs.google.com/spreadsheets/d/1cBeVJg9SEuFqpUImho_gLi2DrEiBCI-OYwcglFpumTc/edit#gid=664140494>`_

Appointments
------------

You can import historical appointment records from appointments with students.

**Params**

========================= ==================================================================
Header                    Value
========================= ==================================================================
\*appointment_medium_name The name of the appointment medium. Case sensitive, must be one of the configurable appointment mediums on your school.
\*appointment_type_name    The name of the appointment type. Case sensitive, must be one of the configurable appointment types on your school.
\*staff_member_email       The email of the staff member involved. Must be a staff member in the system.
\*student_email            The email of the student involved. Must be a student in the system.
\*start_date               The start date and time
\*end_date                 The end date and time
description                A description of the appointment (Text)
status                     [cancelled, requested, approved, rejected, no_show, started, completed] (String)
walkin                     Was this appointment a walk-in? (Boolean)
import_identifier          This identifier must be completely unique, used if you are importing notes or labels on this appointment.
========================= ==================================================================

\* Required


Appointment Types
-----------------

You can import appointment types to be used within Handshake.

**Params**

========================================================== ==================================================================
Header                                                     Value
========================================================== ==================================================================
\*name                                                     The name of the appointment type
\*length                                                   The length of the appointment type in minutes (Integer)
description                                                A description of the appointment type
pre_survey_id                                              The ID of a Handshake survey that the student will fill out as part of their appointment request
post_survey_id                                             The ID of a Handshake survey that will be sent to the student following their appointment
advisor_survey_id                                          The ID of a Handshake survey that the staff member may fill out once the appointment has started
pre_message                                                A message that will be sent to the student prior to their appointment
post_message                                               A message that will be sent to the student following their appointment
drop_in_enabled                                            Whether or not you would like students to be able to select this appointment type when checking into Drop In appointments (Boolean)
appointment_category_names                                 Names of appointment categories that this appointment type should be used for
student_screen_attributes:department_gpa_required          Whether or not a minimum department GPA is required to schedule this appointment type (Boolean)
student_screen_attributes:department_gpa                   The minimum department GPA that a student must have to schedule this appointment type (Decimal)
student_screen_attributes:cumulative_gpa_required          Whether or not a minimum cumulative GPA is required to schedule this appointment type (Boolean)
student_screen_attributes:cumulative_gpa                   The minimum cumulative GPA that a student must have to schedule this appointment type (Decimal)
student_screen_attributes:major_names                      Names of majors that a student must be a part of to schedule this appointment type
student_screen_attributes:major_group_names                Names of major groups that a student must be a part of to schedule this appointment type
student_screen_attributes:school_year_names                Names of school years that a student must be a part of to schedule this appointment type
student_screen_attributes:institution_label_names          Names of labels that a student must have to schedule this appointment type
student_screen_attributes:college_names                    Names of colleges that a student must be a part of to schedule this appointment type
========================================================== ==================================================================

\* Required


Events
------

You can import historical events

**Params**

============================ ==================================================================
Header                       Value
============================ ==================================================================
\*student_registration_start When students can register  (DateTime)
\*student_registration_end   When students can no longer register (DateTime)
\*name                       The name of the event
\*start_date                 When the event starts (DateTime)
\*end_date                   When the event ends (DateTime)
\*event_type_name            The type of event. [Workshop, Info Session, Other]
status                       [pending, in_progress, approved, declined]
description                  The description of the event
import_identifier            This identifier must be completely unique to the system, used if you are importing notes, attendees or labels on this event.
invite_only                  Don't show the event to non-invited students? (Boolean)
attendee_limit               A limit for the number of attendees (Integer)
============================ ==================================================================

\* Required


Notes
-----

File name: notes.csv

Schools may import notes onto various items in Handshake.
The items can be a contact, user, job, appointment, or event.

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
\*identifiable_type                 One of [User, Contact, Job, Appointment, Event]. Case sensitive.
\*\*identifiable_id                 The id of the identifiable.
\*\*identifier                      If the identifiable_type is a User or contact, this is email. Otherwise it is the import_identifier
\*user_type                         If the identifiable_type is a User, the user_type must be specified.
content                             The note contents
privacy_preference                  If this is a personal note or shared with staff. [personal, institution]
reminder_date                       If there should be a reminder associated with the note. See reference section for date formats.
=================================== ==================================================================

\* Required fields
\*\* Either identifier or identifiable_id must be provided.


Labels
-----

File name: labels.csv

Schools may import labels onto various items in Handshake.
The items can be a contact, user, job, appointment, or event.
This will simply apply labels. If a label already exists it will not apply a duplicate. It will not remove labels

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
\*identifiable_type                 One of [User, Contact, Job, Appointment, Event]. Case sensitive.
\*\*identifiable_id                 The id of the identifiable.
\*\*identifier                      If the identifiable_type is a User or contact, this is email. Otherwise it is the import_identifier
\*user_type                         If the identifiable_type is a User, the user_type must be specified.
label_type                          Either 'normal' or 'public'. Defaults to 'normal'.
name                                The label name to apply.
=================================== ==================================================================

\* Required fields
\*\* Either identifier or identifiable_id must be provided.


Campuses
--------

File name: campuses.csv

Schools may import campuses into Handshake.

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
\*name                              The name of the campus. This must be unique across your school.
description                         A description of the campus.
location_name                       The address of the campus.
=================================== ==================================================================

\* Required fields

For an example file of the suggested fields `[Click Here] <https://docs.google.com/spreadsheets/d/1XWknxaJg38mJ3W9yZ4WcSIfzVIRhXifBdztzWVIctj0/edit#gid=0>`_

Majors
-------------

File name: majors.csv

Schools may import majors into Handshake. The columns DO matter - name should be column 1, major group names should be column 2.

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
\*name                              The name of the major. This must be unique across your school.
major_group_names                   A semi-colon separated list of major group names that the major belongs to. Leave this blank to leave the major groups as-is.
=================================== ==================================================================

\* Required fields

For an example file of the suggested fields `[Click Here] <https://docs.google.com/spreadsheets/d/19xT5IszvZtazVNlAe9mJI2xIMfclDT2LnjzJmgZyu40/edit#gid=0>`_

Minors
-----------

File name: minors.csv

Each row should contain the name.

For an example file of the suggested fields `[Click Here] <https://docs.google.com/spreadsheets/d/1jLmG5jYxA5_HDCtVPl5KpU6zBCkDUPh2if_d-pVbXOM/edit#gid=0>`_

Buildings
---------

File name: buildings.csv

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
name                                The name of the building
location_attributes:location_name   The location the building is in. This should be a geo-codeable address
=================================== ==================================================================

Rooms
-----

File name: rooms.csv

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
name                                The name of the room
building_name                       The name of the building. Must be a building already existing at the school.
capacity                            The room's capacity (integer)
available_start                     When the room becomes available (datetime)
available_end                       When the room is no longer available (datetime)
=================================== ==================================================================

Attendees
---------

File name: attendees.csv

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
student_email_address               The email address of the student to be checked in
registered                          Boolean - Mark this student as pre registered?
checked_in                          Boolean - Mark this student as checked in at the event?
\*identifiable_type                 Must be one of: Event or CareerFair (no space between words). Case sensitive.
\*\*identifiable_id                 The id of the identifiable.
\*\*identifier                      If the identifiable_type is a User or contact, this is email. Otherwise it is the import_identifier
=================================== ==================================================================

\* Required fields
\*\* Either identifier or identifiable_id must be provided.
