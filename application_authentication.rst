.. _application_authentication:

Authentication
==============

Handshake provides multiple convenient ways to authenticate and login to the application. Employers, students, alumni, mentors and administrators all may have different options available depending on the School's Single Sign On systems.

Login Page
----------

Handshake allows all users to login from any subdomain. This means that whether the student finds handshake at "app.joinhandshake.com" or "myschool.joinhandshake.com", they'll be able to login.

If "myschool.joinhandshake.com" is accessed, the student will intelligently be provided with relevant options based on their school's SSO systems. Handshake supports SAML, CAS and LDAP integrations.

Configuring Your Login Options
##############################

Each school is allowed to present two login options to their users. The first slot is for Single Sign On users and the second slot is for Handshake authentication. To set up your login options, contact the Handshake team.

SSO vs. Handshake Authentication
################################

While Handshake integrates with common Single Sign On technologies, it also provides its own authenticatio method which is available to any user.

**Handshake Authentication** is most often used by employers, mentors and alumni without SSO access. **SSO Authentication** is most often used by active students and administrators.

Automatically Fixing Misconfigured SSO Users
--------------------------------------------

In some cases, students may have a misconfigured SSO setup. This most often happens in cases where students register for Handshake before their school joins. Handshake has an automated and seamless process for helping students connect their Handshake account with their SSO credentials with the following process:

1. User logs into SSO portal successfully and is redirected back to Handshake.
2. User is given a link to start the process.
3. Upon clicking the link, they are sent an email with a special link to click and a passcode.
4. User clicks on the link in their inbox and enters the passcode when prompted.

With those four steps, any student can connect their Handshake account to their school's SSO.

Password Resets
---------------

Any user can reset their Handshake password at any time using the link on the login page.

Multiple User Types
-------------------

Handshake allows users to have multiple account types, each connected with the same email address. For these users, you can easily switch between the different types using the top right dropdown switcher.

Logging Out
-----------

Users can logout using the top right dropdown. If you are signed in using SSO, we will also sign you out of your SSO portal.
