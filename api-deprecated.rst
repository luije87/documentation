.. _api-depracated:

Deprecated API Documentation
============================

User Management
---------------

[POST] /users
*************

**Deprecated Fields**
These fields are currently deprecated and support for them will be removed soon.

============================== ==================================================================
education_level_name           (String) Undergraduate, Graduate, Postgraduate. This shows up on their main education on their profile
cumulative_gpa                 (Decimal) The student's cumulative GPA
department_gpa                 (Decimal) Decimal of student's departmental GPA
major_names                    (String Array) An array of major names for this student. These must be majors configured in the school's majors list.
minor_names                    (String Array) An array of minor names for this student. These must be minors configured in the school's minors list.
primary_college_name           (String) The college the student belongs to. Must be one of the colleges configured in the school's college list.
education_start_date           (Date) The date the student started at the school in any standard date format. See references for date formats.
education_end_date             (Date) The date the student graduated or plans to graduate school (can be blank if currently_attending is set). See references for date formats.
education_currently_attending  (Boolean) Should be set to true if education_end_date is blank. This signifies they are currently attending this school.
============================== ==================================================================

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
