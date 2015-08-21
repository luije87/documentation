.. _application_mass_emails:

Mass Emails
===========

Mass Emailing allows staff to send targeted emails to large numbers of recipients. They give full control over who receives the mass email, the content in the email, and has additional functionality such as attaching cards.

Setting the Recipients
----------------------

There are generally two ways to initiate a mass email to a set of recipients.

Searching for Students
######################

The simpleset way to start a mass email is by directly visiting the 'New Mass Email' page. Using this method will present you with a search page to narrow down and find the students you wish to email. This will also provide with a graph breakdown of the recipient demographic.

Preset Recipients
#################

Mass Emails may also be created using a preset set of recipients. Examples of these situations include mass emailing everyone who has not yet responded to a survey, the attendees of an event, or a set of applicants. With this option no graph breakdown will be shown.

In some scenarios, there will be a mix of contacts and users when using preset recipients. In this situation only users will be able to login to links and cards attached to the mass email. For more information on why, see the :ref:`users vs. contacts page <application_users_contacts>`

Writing the Email
-----------------

Writing the email is done using a simple, What You See is What You Get interface. It allows for rich text such as colors, bolding, different sizes, links, images, and more. For the more advanced users, an HTML editor is also allowed. Although the mass email editor is highly configurable, some styling options are not available for security reasons.

Attaching Cards
###############

A common pattern in mass emails is to email about something in Handshake such as jobs, events, career fairs or surveys. To make this use case easier, consider using cards. Mass Email Cards are pre-styled information included at the base of the mass email about the item desired.

In addition to being a convenient way to add information about something in Handshake to your mass email, certain cards will also automatically invite the recipient to the card. Mass emails that include cards for career fairs, events or surveys have this behavior.

Finishing the Email
-------------------

To ensure no simple mistakes are made, a review and confirmation process is included.

Review Page
###########

Once your mass email is ready to go, a review page is shown before moving on. On the review page you can see a high level overview of the mass email and confirm that all of the details are correct. Once reviewed, finalize the mass email to move forward.

Sending Test Emails
###################

Once a mass email is finalized, it cannot be edited by you or other staff. From this page can review the content of the mass email and send yourself a test email for review. As long as the email is correct, the mass email can then be sent.

Variables in Mass Email
-----------------------

In order to personalize mass emails, you can use variables in your email body. The variables available should be wrapped with '%' tags when being used, for example '%recipient.first_name%', without the quotes.

The variables available are 'recipient.username' 'recipient.name' 'recipient.first_name' 'recipient.calculated_first_name' 'recipient.last_name' 'recipient.email_address' 'recipient.institution_name'

NOTE: 'caluclated_first_name' uses the preferred first name if available, and otherwise uses their first name. Variables only work for users, not contacts, at this time.
