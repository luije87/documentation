.. _csv:

CSV Upload
=================

The easiest way to get data into Handshake is using the CSV upload. Below you will find an explanation of the different files.

Users
-----

Note: Users are synced, not added.  The user list that is provided will replace your schools current users entirely.

Format: TIMESTAMP_users.csv OR users.csv

Where TIMESTAMP is a single integer representing the time with smaller units further to the right.
Ex: 9:00:15 on 7/14/2014 => 201471490015_users.csv

Timestamps are optional, but can be used to make sure only the latest users list will be synced if the network connection is unreliable and causes two files originally uploaded at different times to show up on our system at the same time.


Required Fields
******************
================================= ======================================================================================
CSV Header Value                  Value Description
================================= ======================================================================================
\*email_address                   Student’s email address. In general this should be a .edu address
\*username                        Student’s username. This MUST be unique and should not be something that changes
\*user_type                       Defaults to "Students", one of "Students", "Career Services", "Mentors"
auth_identifier                   This is the identifier that is required if you use Single Sign On.
================================= ======================================================================================

For an example file of the required fields [Click Here](https://drive.google.com/open?id=0B-F3sE2DoFa8LXo0dURaRTV6ODg&authuser=0)

Recommended Fields
******************
============================= ==========================================================================================
Header                        Value
============================= ==========================================================================================
first_name                    Student’s first name
last_name                     Student’s last name
school_year_name              The name of student’s school year. For a list of acceptable values see the references section.
cumulative_gpa                Decimal of student’s cumulative GPA
major_names                   Semi-colon separated list of major. These match on the majors that have been imported previously.
education_start_date          The date the student started at the school in any standard date format.
education_end_date            The date the student finished at the school (can be blank if currently_attending is set)
override_disabled_field       This field tells Handshake to ignore this user in future syncs and is used to transition a student to an alumni.
============================= ==========================================================================================

For an example file of the suggested fields [Click Here](https://drive.google.com/open?id=0B-F3sE2DoFa8WE9oSVlpN1FGWXc&authuser=0)

Optional Fields
******************************************************************************************************

Note: these fields generally add value to career services but are not required for normal operation.

============================= ==================================================================
CSV Header Value              Value Description
============================= ==================================================================
preferred_name                Coming Soon: The student's preferred name
middle_name                   Coming Soon: The student's middle name
work_authorization_name       One of "U.S. Citizen", "Student (F-1) Visa", "J-1 Visa (Exchange Program)", "Permanent U.S. Resident", "Employment (H-1) Visa"
card_id                       Used for checking in students using a card swipe
ethnicity                     The ethnicity of the user. See the reference section for options.
gender                        The gender of the user. One of "Male", "Female", "Other", or blank (Not specified)
department_gpa                Decimal of student’s departmental GPA
bio                           A student's bio. Shown on the student profile. Visible to everyone who can see the profile.
primary_college_name          The college the student belongs to. Must be one of the colleges configured in the school's college list.
minor_names                   Semi-colon separated list
skill_names                   Semi-colon separated list of skills
external_link_urls            Semi-colon separated list of external links for the profile
time_zone                     The time zone that this user is in. See time zones section for more details.
disabled                      Pass true if this student should not be able to login
is_public                     Pass false if this student's profile should not be viewable by approved employers. Used for students who have set "not contact" as on.
education_currently_attending Boolean. Should be true if education_end_date is blank, false otherwise
work_study_eligible           Pass true if this student is eligible for work study jobs
campus_name                   The name of the campus the student is at. Must be one of the campuses set up in your settings.
============================= ==================================================================

For an example file with all possible fields [Click Here](https://drive.google.com/open?id=0B-F3sE2DoFa8eWFkMDBxcXNlUVE&authuser=0)

Handling Students who Graduate
--------

Recommended option

+ Run a final sync before graduation that updates their school year status to Alumni

+ The file should Also include ‘override_disabled_field’ set to true to say don’t auto archive them
 
Alternative Option

+ Don’t do anything upon graduation and allow recent graduates to disappear from the sync. 

+ When they're no longer included in the sync they will be archived. 

+ When they next sign in they will see the ability to request reactivation of their account. 

+ Career services will get the request to reactive their account and be able to set them as alumni (or ask them to set themselves to alumni) and send them any info you want. 

+ This request will mark them as excluded from sync. Staff can easily filter by grad date and alumni year to email recently converted alumni


Contacts
--------

Contacts in Handshake are used to keep track of employers, alumni, and other individuals who may not have a username and password for Handshake. The most common use for importing
contact is to bring over employer relationships. Contacts can be labeled, sorted, tried to a Handshake employer, and more.

\*Params**

================ ==================================================================
Header           Value
================ ==================================================================
\*first_name     The first name of the contact (String)
\*last_name      The last name of the contact (String)
\*email_address  The email of the contact (String)
title            The title of the contact (String)
description      A description of the contact (Text)
employer_id      The Handshake id of the employer that you want to list the contacts for (int)
employer_name    The name of the employer that you want to list the contacts for (String)
location_name    The name of the location of the contact
phone            The contact's phone number
cell_phone       The contact's cell number
fax              The contact's fax machine number
================ ==================================================================

\* Required


Appointments
------------

You can import historical appointment records from appointments with students.

\*Params**

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


Events
------

You can import historical events

\*Params**

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


Jobs
----

File name: jobs.csv

Schools may import jobs using the legacy job bucket. The legacy_employer_name can
be used to set a display name for the job.
Employers may import jobs and post them to schools that they have permission to 
post to using the school_id

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
\*title                             The jobs's title (string)
description                         Description of the job (String)
legacy_employer_name                Schools: Set a display name for imported jobs
start_date                          When the job begins (Date - see reference section)
import_identifier                   This is an identifier that can be used later for adding labels or notes. MUST be unique across all jobs.
government                          Is this job a government-only job (Boolean)
remote                              Does this job support remote work (Boolean)
desired_skills                      The desired skills for this job. (String)
responsibilities                    The responsibilities for this job. (String)
\*job_type_name                     The type of job. Must be one of the system job types defined in the references section (String)
\*employment_type_name              The type of job. Must be one of the system job types defined in the references section (String)
external_apply_link                 An optional link to send the applicants to when they click apply.
\*application_medium                The method a student should use to apply. One of ['handshake', 'external_link', 'offline', 'handshake_and_external']
salary_type_name                    The salary type. Must be one of the system salary types described in the references section.
expiration_date                     The date the posting should expire. Should be in yyyy-mm-dd format.
division_code                       The code corresponding to the division this job belongs to
school_id                           Employers: The ID of the school you want to post the job to.
job_function_names                  A semicolon separated list of job function names which must be one of the system job functions.
document_notes                      Notes shown to the applicant while they apply
document_type_names                 Specifies which documents are required. Comma separated numbers, selected based on this list: Resume, Cover Letter, Transcript, Work Sample, Other Document
contacts:display                    What information about the contact should be displayed? One of: name_and_email, name_only, none
contacts:email_application_packages Should the contact receive an email for each applicant when they apply? (Boolean)
contacts:send_summary_when_expired  Should the contact receive an email summary when the job expires? (Boolean)
contacts:email                      The email address of the contact
=================================== ==================================================================

\* Required fields


Notes
-----

File name: notes.csv

Schools may import notes onto various items in Handshake.
The items can be a contact, user, job, appointment, or event.

=================================== ==================================================================
Header                              Value
=================================== ==================================================================
\*identifiable_type                 One of [User, Contact, Job, Appointment, Event]. Case sensitive.
\*identifier                        If the identifiable_type is a User or contact, this is email. Otherwise it is the import_identifier
\*user_type                         If the identifiable_type is a User, the user_type must be specified.
content                             The note contents
privacy_preference                  If this is a personal note or shared with staff. [personal, institution]
reminder_date                       If there should be a reminder associated with the note. See reference section for date formats.
=================================== ==================================================================

\* Required fields


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
\*identifier                        If the identifiable_type is a User or contact, this is email. Otherwise it is the import_identifier
\*user_type                         If the identifiable_type is a User, the user_type must be specified.
name                                The label name to apply.
=================================== ==================================================================

* Required fields

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

* Required fields


Majors/Minors
-------------

File name: majors.csv OR minors.csv

Majors: Each row should contain the name and a semi-colon separated list of major_group_names.
Minors: Each row should contain the name.

Major and minor files should be separate.
