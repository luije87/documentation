.. _application_interview_schedules:

Interview Schedules
===================

Interview Scheduling is a core feature in Handshake and a special type of Event. Interview scheduling in Handshake supports Room Conflict Management, setting qualifications, slot management, timelines, automated slot swapping, and applicant management. Interview Schedules can be restricted to a subset of students using :ref:`student permissions <application_student_permissions>`.

.. note:: Registrations have a one-click report download option. Filter down to the relevant items and click the download button to quickly generate a report.

Interview Schedule Preferences
------------------------------

There are many configuration and templating options available for interview scheduling. Configurations allow you to customize interview scheduling for your school and templating makes the interview schedule administration easier and automated.

Interview Seasons
#################

Use interview seasons for establishing when interview schedules can be requested and for what dates interviews can take place. These seasons are enforced for employers requesting interviews at your school, but can be overridden by career services staff.

Interview Schedule Templates
############################

Interview Schedule templates allow slots to be built in one click using pre-determined slots. Templates can be hidden from employers to limit the options available to them. As long as templates are available to the interview schedule requester, a template must be chosen.

Interview Schedule Timelines
############################

While templates are used to easily build out slots for an interview schedule request, timelines are used for establishing the dates of the interview schedule. The dates included in the timeline are application periods, signup periods, and reminder dates.

Because the relevant dates for an interview schedule depend on the type of schedule, timelines also have an Interview Schedule Type associated with them. Specifically, the signup period is only relevant to Preselect interview schedules.

As long as a timeline is available to the interview schedule requester, a timeline must be chosen. In addition, employers will not be allowed to manually choose their Interview Schedule Type or dates if timelines are available to be chosen.

Room Conflict Management
########################

Room Conflict Managmenet can be set up to enforce limitations on the number of interviews that can take place per day. To use room confict management, you must first choose which rooms are available for interviews. Once you have established which rooms are available, the Handshake System will automatically ensure that there are never more interviews than available rooms for a given day. Career Services Staff can override room conflict management limits.

Additional Configuration
########################

In addition to the above, there are options for the following

**Room Costs** Specify a room cost to charge employers for their rooms. This cost is based on the price for a room for one day.
**Maximum Rooms per Request** To limit the number of rooms an employer can request per schedule, use this option.

Building an Interview Schedule
------------------------------

Building an interview schedule requires entering basic details such as the employer and description, timeline details such as interview dates and timelines, and an application method such as qualifications or associated jobs.

Application Methods
###################

Interviews can be configured to receive applicants through two methods. The default and recommended option is to apply through jobs. When applicants apply through jobs, they will be asked which associated job they want to apply to. The other option is to apply directly without having to associate any jobs. For this option, you will specify the qualifications for the interview schedule.

For more information about managing applicants, see the :ref:`Applications Page <application_applications>`.

Associating Jobs
################

By associating jobs to an interview schedule, you are allowing students to apply to the interview schedule through those jobs. The applicants will be shown on the interview schedule's applicants page like normal.

When a job is associated with an interview, all applicants for the associated job will also be applied to the interview as long as the interview schedule is 1) approved and 2) not yet finished with the application period. If those two conditions are not met, the applicants will be drawn in as soon as they are met.

Qualifications
##############

If you choose to have students apply directly, you will be prompted to specify the qualifications for the interview schedule. For more information on setting qualifications see the :ref:`Qualifications <application_qualifications>` page.

Approval Process
################

Once an interview schedule is requested, it will take one of two routes.

1) If the interview schedule is being requested by/for an employer that has automatic interview schedule approval turned on, it will automatically be approved.
2) If the interview schedule is being requested by/for an employer that does not have automatic approval, it will be listed as pending for your approval.

Interview Dates
###############

Each interview schedule must have at least one interview schedule date specified. Interview schedule dates specify the dates on which interviews will take place. If room conflict management is enabled, the remaining room counts will be shown and automatically updated as the counts change.

Managing Interview Slots
------------------------

Interview slots represent the time, student, room, and interviewer of an interview. Interview schedules have multiple interview schedule dates, each of which has multiple interview slots. Interview slots can be edited individually or in bulk.

Associating a Job
#################

Interview Slots with an associated Job are reserved for applicants who applied to the interview through that job. Other applicants will not be able to take that slot. If there is no associated slot, it is open to all applicants.

Adding Breaks
#############

To add a break to an interview slot, mark the slot as "Unavailable".

.. note::  You may also enter the reason for the break in place of the 'Interviewer Name' field.

Building Slots Automatically
############################

Slots can be built automatically using the template specified for the interview schedule. When automatically building slots, you can also specify a room to use for each room requested.

.. note::  As an administrator you can override the template used at any time.

Interview Swap Requests
-----------------------

Interview slot swap requests are an automated, controlled system for letting students request slot swaps with other students. The swaps only take place if both students agree to the swap, and happen as one single transaction to ensure no student will lose their slot during the swap. Interview slot swaps may only occur during the sign up period; once signup end is reached, slot swaps are cancelled and unavailable.

As an administrator, you may view existing slot swap requests and their status.

Timeline Status
---------------

Interview schedules have a series of dates, as specified by the interview schedule timeline. These dates are automatic triggers for system events as the interview schedule moves through each 'Timeline Status'. When a schedule moves into the next timeline status, relevant email notifications and reminders are sent to the appropriate parties.

Interview Schedule Types
------------------------

There are four types of interviews in Handshake.

**Room Only**: Interview slots in a room will be reserved. Handshake will not be used for signing up students.

**Open**: Specify an application period in which students that pass the specified qualifications are allowed to take slots.

**Preselect Continuous**: Specify an application period in which students that pass both the specified qualifications as well as are manually approved are allowed to take slots.

**Preselect**: Specify both an application period and a signup period. Primary and alternate student choices are selected after the application period. Primaries are allowed to sign up before alternates.

.. note::  Preselect interview schedules are the only schedules that have a signup period. The other types of interview schedules have students apply and sign up in the same time period.

Sharing with Schools
---------------------

Interview schedules can be shared with specific schools. When sharing your interview schedule with other schools, the students at those schools will be able to find, view and register for the schedule. Administrators at those schools will also be able to view, but will not have access to configure or edit the interview schedule.

.. note:: In addition to sharing with schools, you may also share with any consortia you are a part of.
