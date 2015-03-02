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
\*username                        Student’s username. This should be unique and should not be something that changes
\*user_type                       Defaults to "Students", one of "Students", "Career Services", "Mentors"
================================= ======================================================================================

For an example file of the required fields [Click Here](https://drive.google.com/open?id=0B-F3sE2DoFa8LXo0dURaRTV6ODg&authuser=0)

Recommended Fields
******************
============================= ==========================================================================================
Header                        Value
============================= ==========================================================================================
auth_identifier               This is the identifier that should be used if you use Single Sign On.
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
employer_id      The Handshake id of the employer that you want to list the contacts for (int)
employer_name    The name of the employer that you want to list the contacts for (String)
location_name    The location, in the form "City, State" or "Country"
phone            The contact's phone number
cell_phone       The contact's cell number
fax              The contact's fax machine number
================ ==================================================================

\* Required

Jobs
----

File name: jobs.csv

The process of bringing in jobs from a legacy system is possible using the legacy job importer. The file below

===================== ==================================================================
Header                Value
===================== ==================================================================
\*title               The jobs's title (string)
\*job_type_name       The type of job. Must be one of the system job types defined in the references section (String)
\*application_medium  The method a student should use to apply. One of ['handshake', 'external_link', 'offline', 'handshake_and_external']
division_code         The code corresponding to the division this job belongs to
description           Description of the job (String)
desired_skills        The desired skills for this job. (String)
responsibilities      The responsibilities for this job. (String)
job_function_name     The job function name. Must be one of the system job functions described in the references section.
location_name         The location of the job in the format "City, State" or "Country"
salary_type_name      The salary type. Must be one of the system salary types described in the references section.
contact_email         The email of the contact to be associated with the job. Used to match the job to a employer when they register.
expiration_date       The date the posting should expire. Should be in yyyy-mm-dd format.
job_function_names    A semicolon separated list of job function names which must be one of the system job functions.
work_study_job        Boolean. True if this is a work study job
document_type_ids     Specifies which documents are required. Comma separated numbers, selected based on this list: [[1, "Resume"], [2, "Cover Letter"], [3, "Transcript"], [4, "Work Sample"], [5, "Other Document"]]
===================== ==================================================================

* Required fields


Majors/Minors
-------------

File name: majors.csv OR minors.csv

Each row should contain one major/minor name. A header is optional.

Major and minor files should be separate.
