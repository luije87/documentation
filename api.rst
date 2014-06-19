.. _api:

API Documentation
=================

Introduction
-----------------------

The Handshake API allows users to make RESTful calls using JSON for sending and receiving data.

The API root URL is : `https://app.joinhandshake.com/api/v1/ <https://app.joinhandshake.com/api/v1/>`__

Tokens
----------

API Calls must use an API token to authenticate with the service. API Tokens can be managed in the school administration page. To create an API token, simply specify the purpose (description) of the token and click create. API tokens can be removed at any time. If you believe that an API token has been compromised, simply delete it from the administration page and it will no longer be active.

When making API calls, the API token needs to be passed via an HTTP header. Set the authorization header to have your API token. An example curl request would be::

    curl https://app.joinhandshake.com/api/v1/users/create -H 'Authorization: Token token="token_goes_here"’

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
The Handshake API has a consistent response format. API responses are always returned as JSON hash. Each response has a ‘success’ attribute on that hash which will be set to either true or false. This is an easy way to know if the call succeeded.

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

The individual objects within the ‘objects’ list will typically contain the same data as a single object response would::

    {
      success: true,
      users: [
        { ... }, { ... }
      ]
    }

**Error**

The ‘errors’ attribute is a hash with attributes as keys and values as arrays of errors on that attribute::

    {
      success: false,
      errors: {
        “attribute”: [“error 1 on attribute”, “error 2 on attribute”],
        “attribute2”: [“error 1 on attribute2”]
      }
    }

Batch Requests
-----------
[POST] /batch
*************
All API calls listed in this document can be done in batch calls via the batch API call. A batch call takes a list of http request details (method type, url, params) and runs each request. The response is the result set of all requests.

**Params**

=========  ===================================================================
Key        Value
=========  ===================================================================
ops        "An array of objects containing details on the request to be made."
=========  ===================================================================

**Sample Params**
::

    {
      ops: [
        {
          method: ‘post’,
          url: ‘app.joinhandshake.com/api/v1/users’,
          params: {
            user: {
              email_address: ‘sgringwe@mtu.edu’,
              username: ‘sgringwe’,
              first_name: ‘Scott’,
              …
            }
          }
        },
        {
          method: ‘post’,
          url: ‘app.joinhandshake.com/api/v1/users’,
          params: {
            user: {
              email_address: ‘bmchrist@mtu.edu’,
              username: ‘bmchrist’,
              first_name: ‘Ben’,
              …
            }
          }
        }
      ]
    }

**Sample Response**
::

    {
      results: [
        {
          body: {
            success: true,
            user: {
              ...
            }
          },
          headers: {
            "Content-Type"=>"application/json; charset=utf-8",
            ...
          },
          status: “200”
        },
        {
          body: {
            success: true,
            user: {
              ...
            }
          },
          headers: {
            "Content-Type"=>"application/json; charset=utf-8",
            ...
          },
          status: “200”
        }

      ]
    }

User Management
---------------
Handshake allows users to manage users at their school via the API. This can be useful when integrating with other systems at the university which hold student data in order to keep Handshake up to date.

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

[POST] /users
*************
Allows administrators to add a student.

**Params**

=========================  ==================================================================
Key                        Value
=========================  ==================================================================
*email_address:            Student’s email address
*username:                 Student’s username
user_type:                 Defaults to "Students", one of "Students", "Career Services", "Mentors"
first_name:                Student’s first name
last_name:                 Student’s last name
school_year_name:          The name of student’s school year
work_authorization_name:   One of "U.S. Citizen", "Student (F-1) Visa", "J-1 Visa (Exchange Program)", "Permanent U.S. Resident", "Employment (H-1) Visa"
department_gpa:            Decimal of student’s departmental GPA
cumulative_gpa:            Decimal of student’s cumulative GPA
bio:                       A student bio
major_names:               An array of major names for this student
minor_names:               An array of minor names for this student
time_zone:                 The time zone that this user is in. See time zones section for more details.
disabled:                  Pass true if this student should not be able to login
work_study_eligible:       Pass true if this student is eligible for work study jobs
is_public:                 Pass false if this student's profile should not be viewable by approved employers
=========================  ==================================================================
* required

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

[PUT] /users/update
*******************
Allows administrators to update a student’s details

**Params**

See POST params

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
*email_address:            Student’s email address
*username:                 Student’s username
=========================  ==================================================================
*One of email_address or username must be passed in order to find the user to remove

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

Reports
---------

[GET] /report/{id}
******************
Allows administrators to output custom data

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
-----------------
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
      majors: [‘Major name’, ‘Major 2 name’]
    }

[POST] /majors
**************
Allows administrators to add a major to their school. Returns false if major is already at the school.

**Params**

==========  ==================================================================
Key         Value
==========  ==================================================================
name:       Name of major
==========  ==================================================================

**Sample Response**
::

    {
      success: true,
      major: ‘Major name that was added’
    }

[DELETE] /majors/destroy
************************
Allows administrators to remove a major from their school. Returns false if major is not at the school.

**Params**

==========  ==================================================================
Key         Value
==========  ==================================================================
name:       Name of major
==========  ==================================================================

**Sample Response**
::

    {
      success: true,
      major: ‘Major name that was removed’
    }

Employers
-----------------
Allows managing employers in your school's list of approved employers.

[GET] /employers
*************
Allows administrators to list employers that are approved at your school.

**Params**

None

**Sample Response**
::

    {
      success: true,
      employers: [
        {
          name: 'Acme Corp.',
          email_domain: 'careers@acmecorp.com'
        }
      ]
    }

[POST] /employers
**************
Allows administrators to approve an employer at their school. Returns false if major is already at the school.

**Params**

============== ==================================================================
Key            Value
============== ==================================================================
*name:          Name of major
*email_domain:  Email domain of the company. For example, 'acmecorp.com'.
============== ==================================================================

* Required fields

**Sample Response**
::

    {
      success: true,
      employer: {
        name: 'Acme Corp.',
        email_domain: 'careers@acmecorp.com'
      }
    }

[DELETE] /employers/destroy
************************
Allows administrators to remove an employer from their school. Returns false if employer is not at the school.

**Params**

============== ==================================================================
Key            Value
============== ==================================================================
*name:          Name of major
*email_domain:  Email domain of the company. For example, 'acmecorp.com'.
============== ==================================================================

**Sample Response**
::

    {
      success: true,
      employer: {
        name: 'Acme Corp.',
        email_domain: 'careers@acmecorp.com'
      }
    }