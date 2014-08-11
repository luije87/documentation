.. _csv:

CSV Upload
=================

Users
-----

Note: Users are synced, not added.  The user list that is provided will replace your schools current users entirely. 

Format: TIMESTAMP_users.csv OR users.csv

Where TIMESTAMP is a single integer representing the time with smaller units further to the right.
Ex: 9:00:15 on 7/14/2014 => 201471490015_users.csv

Timestamps are optional, but can be used to make sure only the latest users list will be synced if the network connection is unreliable and causes two files originally uploaded at different times to show up on our system at the same time.


Fields
******
=========================  ==================================================================
Header                     Value
=========================  ==================================================================
\*email_address:           Student’s email address
\*username:                Student’s username
\*user_type:               Defaults to "Students", one of "Students", "Career Services", "Mentors"
first_name:                Student’s first name
last_name:                 Student’s last name
school_year_name:          The name of student’s school year
work_authorization_name:   One of "U.S. Citizen", "Student (F-1) Visa", "J-1 Visa (Exchange Program)", "Permanent U.S. Resident", "Employment (H-1) Visa"
department_gpa:            Decimal of student’s departmental GPA
cumulative_gpa:            Decimal of student’s cumulative GPA
bio:                       A student bio
major_names:               Semi-colon separated list
minor_names:               Semi-colon separated list
time_zone:                 The time zone that this user is in. See time zones section for more details.
disabled:                  Pass true if this student should not be able to login
work_study_eligible:       Pass true if this student is eligible for work study jobs
is_public:                 Pass false if this student's profile should not be viewable by approved employers
=========================  ==================================================================
\*required



Employers
---------

File name: employers.csv

Fields
******
====================== ==================================================================
Header                 Value
====================== ==================================================================
\*name:                Name of employer
email_domain:          Email domain of the company. For example, 'acmecorp.com'.
industry_name:         The name of the company's industry.
institution_type_name: The type of employer.
institution_size_name: The size of the employer.
description:           The description of the employer.
website:               A url directing to the employer's website.
email:                 A general email address for contacting the employer.
phone:                 A geenral phone number for contacting the employer.
blog_rss:              A url directing to the employer's career blog feed.
location_name:         The name of the city of the employer headquarters.
address:               The address of the employer headquarters.
zipcode:               The zipcode of the employer headquarters.
====================== ==================================================================
\*required



Contacts
--------
Allows managing contacts at your employers.

\*Params**

================ ==================================================================
Header           Value
================ ==================================================================
\*employer_id:   The id of the employer that you want to list the contacts for.
\*employer_name: The name of the employer that the contact represents
\*first_name:    ..
\*last_name:     ..
\*email_address: ..
location_id      ..
phone            ..
cell_phone       ..
fax              ..
================ ==================================================================
* Required
\* At least either employer_id or employer_name must be provided



Jobs
----

File name: jobs.csv

===================== ==================================================================
Header                Value
===================== ==================================================================
\*title:              The jobs's title
\*job_type_name:      The type of job. Must be one of the system job types 
\*application_method: The method a student should use to apply. One of handsake, external_link, offline
department_code:      The code corresponding to the department this job belongs to 
description:          Description of the job
job_function_name:    The job function name. Must be one of the system job functions.
location:             The location of the job
salary_type:          The salary type. Must be one of the system salary types
contact_email:        The email of the contact to be associated with the job. Must match with an existing contact
expiration_date:      The date the posting should expire. yyyy-mm-dd
job_function_names:   A semicolon separated list of job function names which must be one of the system job functions.
===================== ==================================================================

* Required fields


Majors/Minors
-------------

File name: majors.csv OR minors.csv

Each row should contain one major/minor name

Major and minor files should be separate.
