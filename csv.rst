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
department_gpa                Decimal of student’s departmental GPA
bio                           A student's bio. Shown on the student profile. Visible to everyone who can see the profile.
minor_names                   Semi-colon separated list
skill_names                   Semi-colon separated list of skills
external_link_urls            Semi-colon separated list of external links for the profile
time_zone                     The time zone that this user is in. See time zones section for more details.
disabled                      Pass true if this student should not be able to login
is_public                     Pass false if this student's profile should not be viewable by approved employers. Used for students who have set "not contact" as on.
education_currently_attending Boolean. Should be true if education_end_date is blank, false otherwise
work_study_eligible           Pass true if this student is eligible for work study jobs
============================= ==================================================================

For an example file with all possible fields [Click Here](https://drive.google.com/open?id=0B-F3sE2DoFa8eWFkMDBxcXNlUVE&authuser=0)


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
address_city     The city the contact is in
address_state    The state the contact is in
address_zip      The zip the contact is in
address_country  The country the contact is in
phone            The contact's phone number
cell_phone       The contact's cell number
fax              The contact's fax machine number
================ ==================================================================

\* Required

Jobs
----

File name: jobs.csv

Schools may import jobs using the legacy job bucket. The legacy_employer_name can
be used to set a display name for the job.
Employers may import jobs and post them to schools that they have permission to 
post to using the school_id

================================== ==================================================================
Header                             Value
================================== ==================================================================
\*title                            The jobs's title (string)
description                        Description of the job (String)
legacy_employer_name               Schools: Set a display name for imported jobs
start_date                         When the job begins (Date - see reference section)
government                         Is this job a government-only job (Boolean)
remote                             Does this job support remote work (Boolean)
desired_skills                     The desired skills for this job. (String)
responsibilities                   The responsibilities for this job. (String)
\*job_type_name                    The type of job. Must be one of the system job types defined in the references section (String)
\*employment_type_name             The type of job. Must be one of the system job types defined in the references section (String)
external_apply_link                An optional link to send the applicants to when they click apply.
\*application_medium               The method a student should use to apply. One of ['handshake', 'external_link', 'offline', 'handshake_and_external']
salary_type_name                   The salary type. Must be one of the system salary types described in the references section.
expiration_date                    The date the posting should expire. Should be in yyyy-mm-dd format.
division_code                      The code corresponding to the division this job belongs to
school_id                          Employers: The ID of the school you want to post the job to.
job_function_names                 A semicolon separated list of job function names which must be one of the system job functions.
document_notes                     Notes shown to the applicant while they apply
document_type_names                Specifies which documents are required. Comma separated numbers, selected based on this list: Resume, Cover Letter, Transcript, Work Sample, Other Document
contacts:display                    What information about the contact should be displayed? One of: name_and_email, name_only, none
contacts:email_application_packages Should the contact receive an email for each applicant when they apply? (Boolean)
contacts:send_summary_when_expired  Should the contact receive an email summary when the job expires? (Boolean)
contacts:email                      The email address of the contact
================================== ==================================================================

* Required fields


Majors/Minors
-------------

File name: majors.csv OR minors.csv

Each row should contain one major/minor name. A header is optional.

Major and minor files should be separate.
