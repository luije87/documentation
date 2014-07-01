.. _csv:

CSV Upload
=================

Users
-----

Fields
******
=========================  ==================================================================
Key                        Value
=========================  ==================================================================
*email_address:            Student’s email address
*username:                 Student’s username
*user_type:                 Defaults to "Students", one of "Students", "Career Services", "Mentors"
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
*required