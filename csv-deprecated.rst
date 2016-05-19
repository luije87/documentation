.. _csv:

Deprecated CSV Upload
=====================

Students
-------

Deprecated Fields
******************************************************************************************************

These fields are currently deprecated and support for them will be removed soon.

============================== ==================================================================
education_level_name           (String) Undergraduate, Graduate, Postgraduate. This shows up on their main education on their profile
cumulative_gpa:                (Decimal) The student's cumulative GPA
department_gpa:                (Decimal) Decimal of student's departmental GPA
major_names:                   (String Array) An array of major names for this student. These must be majors configured in the school's majors list.
minor_names:                   (String Array) An array of minor names for this student. These must be minors configured in the school's minors list.
primary_college_name           (String) The college the student belongs to. Must be one of the colleges configured in the school's college list.
education_start_date           (Date) The date the student started at the school in any standard date format. See references for date formats.
education_end_date             (Date) The date the student graduated or plans to graduate school (can be blank if currently_attending is set). See references for date formats.
education_currently_attending  (Boolean) Should be set to true if education_end_date is blank. This signifies they are currently attending this school.
override_disabled_field                   (Boolean) This field tells Handshake to ignore this user in future disabling syncs and is used to transition a student to an alumni.
============================== ==================================================================

Disabling Syncs
******************************************************************************************************

As mentioned above, the user sync process can be used to automatically disable users who should no longer have access to Handshake. This process is called a "Disabling Sync" and can be done upon request with any new user file. By default, user syncs are *not* "Disabling Sync"'s and will leave user accounts enabled, even if not found in the file. This is to ensure that active and current students are not unexpectedly disabled because of a glitch or accidental removal from the CSV file.

When a "Disabling Sync" is run, all students in Handshake that are not included in the sync and do not have "override_disabled_field" set to true will be disabled. Those students will be able to request reactivation and the Career Services staff will be able to re-enable them upon request or proactively.

For a normal, "Non-disabling Sync", users listed in the CSV will be created or updated, but no users will be disabled.

Handling Students who Graduate
******************************************************************************************************

**Recommended option**

+ Run a final sync before graduation that updates their school year status to Alumni

+ The file should Also include ‘override_disabled_field’ set to true so that the alumni are not disabling during future Disabling Syncs.


