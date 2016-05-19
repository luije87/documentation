.. _api:

API Documentation
=================

Introduction
------------

The Handshake API allows users to make RESTful calls using JSON for sending and receiving data.

The API root URL is : `https://app.joinhandshake.com/api/v1/ <https://app.joinhandshake.com/api/v1/>`__

Tokens
----------

API Calls must use an API token to authenticate with the service. API Tokens can be managed in the school administration page. To create an API token, simply specify the purpose (description) of the token and click create. API tokens can be removed at any time.

Please safeguard the API token like you would for password. Never include or check-in the API token into any publicly hosted repositories (such as GitHub), nor post it to any publicly accessible pages.

If you believe that an API token has been compromised, immediately delete it from the administration page and it will no longer be active.

When making API calls, the API token needs to be passed via an HTTP header. Set the authorization header to have your API token. An example curl request would be::

    curl https://app.joinhandshake.com/api/v1/users/create -H 'Authorization: Token token="token_goes_here"'

Requests
-----------------
POST, PUT and DELETE requests take JSON as the request payload. A normal request would look something like the below hash::

    {
      user: {
        attr1: “value”,
        attr2: “value2”
      }
    }

Responses
------------------
The Handshake API has a consistent response format. API responses are always returned as JSON hash. Each response has a 'success' attribute on that hash which will be set to either true or false. This is an easy way to know if the call succeeded.

In addition, there is at least one other attribute which contains the bulk of the data. This will either be a single object (ex. after creating a user), a list (ex. a search) or errors. An example response for each is below.

**Single Object**
::

    {
      success: true,
      user: {
        attr: “value”
      }
    }

**List**

The individual objects within the 'objects' list will typically contain the same data as a single object response would::

    {
      success: true,
      users: [
        { ... }, { ... }
      ]
    }

**Error**

The 'errors' attribute is a hash with attributes as keys and values as arrays of errors on that attribute::

    {
      success: false,
      errors: {
        “attribute”: [“error 1 on attribute”, “error 2 on attribute”],
        “attribute2”: [“error 1 on attribute2”]
      }
    }

User Management
---------------
Handshake allows users to manage users at their school via the API. This can be useful when integrating with other systems at the university which hold student data in order to keep Handshake up to date.

This can also be used to add system labels to students. System labels are labels that can only be applied during a sync, and can't be edited or removed on the UI. System labels are like private labels, and can only be seen by other staff members at the institution. System labels should be passed in as an array of label names. If a label exists with the same name, it will be converted to a system label. If the system labels key is passed in but no label names are passed, it will remove all labels from the student. Similarly, if a student has a system label applied, but it is not present in the current sync, it will be removed from the student. If the system labels key is not passed, no existing labels will be removed from the student.

[GET] /users
************
Allows administrators to search for students at their school.

**Params**

=========  ==================================================================
Key        Value
=========  ==================================================================
query      A simple string query to search with
=========  ==================================================================

**Sample Response**
::

    {
      success: true,
      users: [
        {
          email_address: “sgringwe@mtu.edu”,
          username: “sgringwe”,
          first_name: “Scott”,
          …
        },
        {...}, {...}
      ]
    }

.. _post-users:

[POST] /users
*************
Allows administrators to add a student.

**Params**

============================== ==================================================================
Key                            Value
============================== ==================================================================
\*email_address                (String) Student's email address
\*username                     (String) Student's username
\*user_type                    (String) Defaults to "Students", one of "Students", "Career Services", "Mentors"
auth_identifier                (String) This is the identifier that is required if you use Single Sign On.
recommended_authentication     (String) One of "sso" or "standard". Allows you to suggest what type of authentication the user should use when logging in.
card_id                        (String) A card id that can be used for card swipe checkins.
first_name                     (String) Student's first name
last_name                      (String) Student's last name
school_year_name               (String) The name of student's school year. See references for possible values.
preferred_name                 (String) The student's preferred name
middle_name                    (String) The student's middle name
work_authorization_name        (String) One of "U.S. Citizen", "Student (F-1) Visa", "J-1 Visa (Exchange Program)", "Permanent U.S. Resident", "Employment (H-1) Visa", "TN Visa", “L1 Visa”, “Work Card”,”H4 Visa”
ethnicity                      (String) The ethnicity of the user. See the reference section for options.
gender                         (String) The gender of the user. One of "Male", "Female", "Other", or blank (Not specified)
bio                            (String) A student bio
skill_names                    (String Array) An array of skills to list on the students profile
external_link_urls             (String Array) An array of external links to list on the students profile
time_zone                      (String) The time zone that this user is in. See time zones section for more details.
disabled                       (Boolean) Pass true if this student should not be able to login
override_disabled_field        (Boolean) This field tells Handshake to ignore this user in future syncs and is used to transition a student to an alumni.
work_study_eligible            (Boolean) Pass true if this student is eligible for work study jobs
mentor_information_attributes  (Hash) A nested hash containing mentor-specific attributes. See below table for possible values.
campus_name                    The name of the campus the student is at. Must be one of the campuses set up in your settings.
mobile_number                  The user's mobile phone number
system_label_names             (String Array) An array of label names to apply to the user
profile_review_status          This can be used to manage a students review status. Set this to "approved" if this student will not need a profile review. (Not relevant if profile review is not turned on for your school). All options: ['unsubmitted', 'pending', 'approved'].
document_review_status         This can be used to manage a students document review status. Set this to "automatically_approved" if this student will not need documents approved. (Not relevant if document review is not turned on for your school). All options: ['no_pending_documents' 'pending_documents' 'automatically_approved']
primary_education_attributes   (Hash) A nested hash containing the primary education attributes. See below table for possible values.
============================== ==================================================================

**Training configuration fields**
These are used only for trainings and demo setups.

============================== ==================================================================
role_names                     A semi colon separated list of roles to give to this user.
password                       Only used in demo environment for setting up trainings. Must match confirmation.
password_confirmation          Only used in demo environment for setting up trainings. Must match confirmation.
============================== ==================================================================

**Primary education params**
These are nested inside of 'primary_education_attributes' above. These values will be assigned to the student's primary education, which is the education determined as the record to respect when determining job and interview schedule qualifications.

=================================== ==================================================================
Key                                 Value
=================================== ==================================================================
education_level_name                (String) Undergraduate, Graduate, Postgraduate. This shows up on their main education on their profile
cumulative_gpa                      (Decimal) The student's cumulative GPA
department_gpa                      (Decimal) Decimal of student's departmental GPA
major_names                         (String Array) An array of major names for this student. These must be majors configured in the school's majors list.
minor_names                         (String Array) An array of minor names for this student. These must be minors configured in the school's minors list.
college_name                        (String) The college the student belongs to. Must be one of the colleges configured in the school's college list.
start_date                          (Date) The date the student started at the school in any standard date format. See references for date formats.
end_date                            (Date) The date the student finished at the school (can be blank if currently_attending is set). See references for date formats.
currently_attending                 (Boolean) Should be set to true if education_end_date is blank. This signifies they are currently attending this school.
=================================== ==================================================================

**Mentor information params**
These are nested inside of 'mentor_information_attributes' above

=================================== ==================================================================
Key                                 Value
=================================== ==================================================================
student_contact_preference          (String) Whether or not this mentor can be contacted by students. Either 'allowed' or 'not_allowed'
advice                              (String) Generic advice that this mentor has to offer
hobbies                             (String) Relevant hobbies that this mentor listed
expertise_names                     (String Array) An array of expertise that this mentor has. Will create if not already listed on school administrator page.
maximum_mentees                     (Integer) The maximum number of ongoing mentorships that this mentor is willing to do. Defaults to 50.
maximum_student_contacts_per_month  (Integer) The maximum number of messages that this mentor is willing to receive.
industry_name                       (String) The industry that this mentor is in. See references for possible values
=================================== ==================================================================

\* required

**Sample Response**
::

    {
      success: true,
      user: {
          email_address: “sgringwe@mtu.edu”,
          username: “sgringwe”,
          first_name: “Scott”,
          …
      }
    }

.. _put-users-update:

[PUT] /users/update
*******************
Allows administrators to update a student's details.

Updating sensitive fields (username, email_address, and auth_identifier) require setting top-level param 'change_sensitive_fields' to true. The request would fail otherwise.

**Top Level Params**

============================== ==================================================================
Key                            Value
============================== ==================================================================
change_sensitive_fields        (Boolean) Pass true to force update sensitive user fields.
============================== ==================================================================

See :ref:`post-users` for user params.

**Sample Response**
::

    {
      success: true,
      user: {
          email_address: “sgringwe@mtu.edu”,
          username: “sgringwe”,
          first_name: “Scott”,
          …
      }
    }

[DELETE] /users/destroy
***********************
Allows administrators to remove a student from handshake.

**Params**

=========================  ==================================================================
Key                        Value
=========================  ==================================================================
\*email_address            Student's email address
\*username                 Student's username
=========================  ==================================================================

\*One of email_address or username must be passed in order to find the user to remove

**Sample Response**
::

    {
      success: true,
      user: {
          email_address: “sgringwe@mtu.edu”,
          username: “sgringwe”,
          first_name: “Scott”,
          …
      }
    }

Student Sync
------------

[POST] /users/start_sync
************************
Tells the Handshake API that you are beginning a student data sync and moves the school in to "sync status".

**Sample Response**
::

    {
      success: true
    }

[POST] /users/create_or_update
******************************
Takes in normal user params (see :ref:`post-users`). If user does not yet exists, creates them. If user already exists, updates with given fields.

Updating sensitive fields require setting top-level param 'change_sensitive_fields' to true. See :ref:`put-users-update`.

**Sample Response**

See :ref:`post-users`.

[POST] /users/sync_details
**************************
Gives details about the current status of the sync including how many have been updated, how many have been created and how many users are not yet accounted for.

**Sample Response**
The following is an example of a response near the beginning of the sync process.

::

    {
      success: true,
      unaccounted_count: 11283,
      updated_count: 4239,
      created_count: 4
    }

[POST] /users/end_sync
***********************
Finishes the sync process. Disables any students who were not accounted for during the sync and moves the school out of "sync status".

**Sample Response**
::

    {
      success: true
    }

Reports
---------

[GET] /report/{id}
******************
Allows administrators to output customized data feeds. Because of the highly customizable nature of these reports, the responses are not guaranteed to be performant and are rate limited.

**Params**
None

**Sample Response**
::

    {
      success: true,
      report: [
        {
          id
          name
          locked
          username: “sgringwe”,
          first_name: “Scott”,
          …
        },
        {...}, {...}
      ]
      data: [
        [column1, column2, column3], #column list
        [
          {column1: value, column2: value}, #row 1
          {column1: value, column2: value}, #row 2
        ]
      ]
    }

Majors/Minors
-------------
The following is the same for minors. This part of the API allows career services centers to add, remove and receive a list of majors in the system for their school.

[GET] /majors
*************
Allows administrators to list majors for their school by name

**Params**

None

**Sample Response**
::

    {
      success: true,
      majors: ['Major name', 'Major 2 name']
    }

[POST] /majors
**************
Allows administrators to add a major to their school. Returns false if major is already at the school.

**Params**

==================  ==================================================================
Key                 Value
==================  ==================================================================
name                Name of major
major_group_names   Array of major group names to allocate this major into
==================  ==================================================================

**Sample Response**
::

    {
      success: true,
      major: 'Major name that was added'
    }

[DELETE] /majors/destroy
************************
Allows administrators to remove a major from their school. Returns false if major is not at the school.

**Params**

==========  ==================================================================
Key         Value
==========  ==================================================================
name        Name of major
==========  ==================================================================

**Sample Response**
::

    {
      success: true,
      major: 'Major name that was removed'
    }


Contacts
--------
Allows managing contacts at your institution.

[GET] /contacts
***************
Allows administrators to list contacts.

**Params**

================== ==================================================================
Key                Value
================== ==================================================================
\*first_name       ..
\*last_name        ..
\*email_address    ..
\*\*employer_id    The id of the employer that you want to list the contact for
\*\*employer_name  The name of the employer that the contact represents
title              The job title of this contact, for example 'University Relations'
location_name      ..
phone              ..
cell_phone         ..
fax                ..
description        ..
assigned_to_id     The id of the user in Handshake that manages this contact
================== ==================================================================

\* Required
\*\* Either employer_id or employer_name may be provided, but employer_id is more accurate



**Sample Response**
::

    {
      success: true,
      contacts: [
        {
          first_name: 'Bill',
          last_name: 'Hertz',
          email_address: 'careers@acmecorp.com',
          ...
        },
        { ... },
      ]
    }

[POST] /contacts
****************
Add a contact to an employer

**Params**

================ ==================================================================
Key              Value
================ ==================================================================
\*employer_id    The id of the employer to add the contact to.
\*email_address  The email address of the contact.
first_name       The first name of the contact.
last_name        The last name of the contact.
title            The title of the contact.
address          The address of the contact.
location_id      The id of the work location of the contact.
phone            The phone number of the contact
cell_phone       The cell phone number of the contact
fax              The fax number of the contact
================ ==================================================================

\* Required fields

**Sample Response**
::

    {
      success: true,
      contact: {
        employer_id: 1,
        email_address: 'bill@acmecorp.com',
        ...
      }
    }

[DELETE] /contacts/destroy
**************************
Allows administrators to remove a contact from an employer. Returns false if contact is not at the school.

**Params**

================ ==================================================================
Key              Value
================ ==================================================================
\*employer_id    The id of the employer to add the contact to.
\*email_address  The email address of the contact.
================ ==================================================================

**Sample Response**
::

    {
      success: true,
      employer: {
        name: 'Acme Corp.',
        email_domain: 'careers@acmecorp.com'
      }
    }

Jobs
-----------------
Allows managing jobs at your school

[GET] /jobs
*************
Allows administrators to list jobs at your school

**Params**

None

**Sample Response**
::

    {
      success: true,
      jobs: [
        {
          title: 'Engineering Intern'
        }
      ]
    }

[POST] /jobs
**************
Allows administrators to create jobs at your school

**Params**

=================================== ==================================================================
Key                                 Value
=================================== ==================================================================
\*title                             The jobs's title
\*employer_id                       System ID of the employer associated with this job
\*job_type_name                     The type of job. Must be one of the system job types
\*application_medium                The method a student should use to apply. One of ['handsake', 'external_link', 'offline', 'handshake_and_external']
\*physical_application_instructions Instructions on how a student should submit a physical application. This is required if the application medium is 'offline'
description                         Description of the job
job_function_names                  An array of job function names which must be one of the system job functions.
location_name                       The location of the job
salary_type                         The salary type. Must be one of the system salary types
contact_email                       The email of the contact to be associated with the job. Must match with an existing contact
expiration_date                     The date the posting should expire. yyyy-mm-dd
posting_status                      The status of the posting, if being posted to a school. Possible values: expired, approved, pending, declined.
=================================== ==================================================================

\* Required fields

**Sample Response**
::

    {
      success: true,
      job: {
        title: 'Engineering Intern'
      }
    }

Attendees
-----------------
Allows for creation and indexing of attendee records.

[GET] /attendees
*************
Allows pulling for attendees of an attendable event. The results can be paginated and are ordered by most recently updated first.

**Params**

===================== ==================================================================
Key                   Value
===================== ==================================================================
\*\*identifier        The import identifier of the attendable.
\*\*identifiable_id   The id of the attendable.
\*identifiable_type   The type of the event, either 'CareerFair' or 'Event'.
page                  The page of results that you want, 0-based.
===================== ==================================================================

\* Required fields
\*\* Either identifier or identifiable_id must be provided.

**Sample Response**
::

    {
      success: true,
      attendees: [
        {
          user_id: 1,
          user_name: 'John Doe',
          ...
        }
      ]
    }

Events
--------
Allows managing events at your institution.

[POST] /events
****************
Add an event

**Params**

=============================== ==================================================================
Key                             Value
=============================== ==================================================================
\*start_date                    (String) The date and time when the event starts. Ex: '2017-03-10 9:00 AM'
\*end_date                      (String) The date and time when the event ends. Ex: '2017-03-10 10:00 AM'
\*name                          (String) The name of the event.
\*event_type_name               (String) The type of event. Possible types: 'Workshop', 'Info Session', 'Group Appointment', 'Other'
status                          (String) The status of the event. Possible status: 'approved', 'pending', 'declined'. Defaults to 'pending'.
description                     (String) The description of the event.
student_registration_start      (String) The date students can start registering. Ex: '2017-03-01 7:00 AM'
student_registration_end        (String) The date students can no longer register. Ex: '2017-03-09 8:00 PM'
invite_only                     (Boolean) If the event requires an invite.
attendee_limit                  (Integer) The number of attendees allowed to register.
external_link                   (String) If provided, students will be redirected to this link when they register.
welcome_student_email           (String) This content will be emailed to students when they join this event.
=============================== ==================================================================

\* Required fields

**Sample Success Response**
::

    {
      success: true,
      event: {
      "id": 1,
      "name": "New Event"
      }
    }

Career Interests
--------
Allows getting information about career clusters your school has configured,
and which students have indicated their interest in those clusters.

[GET] /career_interests
****************
Get the list of career clusters that are configured for your school.

**Params**
None

**Sample Response**
::

    {
      success: true,
      career_clusters: [
        {
          id: 1,
          name: "Software Development"
        },
        {
          id: 2,
          name: "Business"
        }
      ]
    }

[GET] /career_interests/{id}
****************
Get a list of students who are interested in a given career cluster.
The ID of a career cluster can be determined using the above endpoint.

**Params**
None

**Sample Response**
::

    {
      success: true,
      students: [
        {
          id: 123,
          email_address: "jane@handshake.edu",
          first_name: "Jane",
          last_name: "Doe"
        },
        {
          id: 456,
          email_address: "john@handshake.edu",
          first_name: "John",
          last_name: "Doe"
        }
      ]
    }
