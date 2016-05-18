.. _references:

References
==========


Encodings
---------

Handshake requires your file uploads to be UTF-8  (http://www.utf8-chartable.de/)

Example command to check your file's encoding `file ./input_file.csv`

Example command to convert your file to UTF-8 `iconv -f MACROMAN -t UTF-8 ./input_file.csv > ./output_file.csv`

Booleans
--------

If specifying a boolean value (true or false) please use all lower case or all upper case letters
Good: TRUE true FALSE false
Bad: True False

Dates
-----
| When using dates or datetimes in the CSV or API, please provide them in one of the following formats:
| yyyy-mm-dd
| yyyy-mm-dd hh:mm:ss (assumes UTC time)  
| yyyy-mm-dd hh:mm:ss offset (where timezone offset is either + or -, and hhmm)  

School Years
------------

The following standardized list of school years are supported in Handshake::
   
   Freshman
   Sophomore
   Junior
   Senior
   Masters
   Doctorate
   Postdoctoral Studies
   Alumni
   
The fields below are deprecated. They are still supported on the api, but will map to the value in parentheses::

   Graduate (Masters)
   Post Graduate (Doctorate)

Gender
------

The following standardized list of genders supported in Handshake::

    Male
    Female
    Other


Work Authorizations
-------------------

The following standardized list of work authorizations supported in Handshake::

    U.S. Citizen
    Student (F-1) Visa
    J-1 Visa (Exchange Program)
    Permanent U.S. Resident
    Employment (H-1) Visa
    TN Visa
    L1 Visa
    Work Card
    H4 Visa


Education Levels
----------------

The following standardized list of education levels are supported in Handshake::

   High School
   Associates
   Certificate
   Advanced Certificate
   Bachelors
   Masters
   Doctorate
   Postdoctoral Studies

The fields below are deprecated. They are still supported on the api, but will map to the value in parentheses::

   Graduate (Masters)
   Postgraduate (Doctorate)

Administrative Roles
----------
The following roles are supported in Handshake::

   Experiences
   Articles
   Manage Own Appointments
   Manage All Appointments
   External Feeds
   Jobs
   Employer Approvals
   Manage Students
   View as Student
   Events
   Surveys
   Interview Schedules
   Reports
   Manage Staff
   Upload Attachments
   Career Plans
   Rooms
   Mass Emails
   Mentorships
   Outcomes
   Posts
   Student Reviews
   Applications
   Career Fairs
   Pins
   View Shared Notes
   Manage Labels
   Launch Check-in Kiosk

Salary Type Names
-----------------

The following standardized list of salary types is supported in Handshake::

   Paid
   Unpaid
   Commission Only
   Commission Plus Salary

Job Type Names
--------------

The following standardized list of job types is supported in Handshake::

   Job
   Internship
   Cooperative Education
   Experiential Learning
   On Campus Student Employment
   Fellowship
   Graduate School

Employment Type Names
---------------------

The following standardized list of employment types is supported in Handshake::

   Full Time
   Part Time
   Seasonal

Ethnicity
---------------------

The following standardized list of ethnicities is supported in Handshake::

   Native American/Alaskan Native
   Black or African American
   Asian/Asian American
   Native Hawaiian/Pacific Islander
   Latino(a)
   White/Caucasian
   Middle Eastern


Industries
----------

The following standardized list of industries are supported in Handshake::

    Accounting
    Advertising, PR & Marketing
    Aerospace
    Agriculture, Farming, & Ranching
    Architecture and Civil Engineering
    Automotive
    Biotech & Life Sciences
    Commercial Banking & Credit
    Computer Systems
    Construction
    Defense
    Design
    Electronic & Computer Hardware
    Fashion
    Food / Beverage & Consumer Goods
    Forestry
    Government - Local, State & Federal
    Healthcare
    Higher Education
    Hotels & Accommodation
    Insurance
    International Affairs
    Internet & Software
    Investment Banking
    Investment / Portfolio Management
    Journalism, Digital Media & Publishing
    K-12 Education
    Legal & Law Enforcement
    Management Consulting
    Manufacturing - Other
    Medical Devices
    Movies, TV, Radio
    Non-Profit - Other
    Oil, Gas, & Natural Resources
    Other Education
    Other Industries
    Performing and Fine Arts
    Pharmaceuticals
    Politics
    Real Estate
    Religious work
    Restaurants & Food Service
    Retail Stores
    Scientific and Technical Consulting
    Social Assistance
    Sports & Leisure
    Telecommunications
    Tourism
    Transportation & Logistics
    Utilities and Renewable Energy
    Veterinary
    Wholesale Trade  

Job Functions
-------------

The following standardized list of job functions are supported in Handshake::

    Account Management/Planning
    Accounting/Auditing
    Administration
    Administrative/Support Services
    Advertising
    Advocacy
    Analyst
    Animal Care
    Bookkeeping
    Brand Management
    Broadcasting
    Business Development
    Buying/Purchasing
    Childcare
    Childcare
    Coaching
    Community Service
    Computer Drafting and Design
    Conflict Resolution
    Construction/Contracting
    Consulting
    Counseling
    Creative/Design/Multimedia
    Curriculum Development
    Customer Service
    Cyber Security
    Data Entry
    Data Management
    Database Management
    Distribution
    Domestic Care/Services
    Economic/Community Development
    Engineering
    Entrepreneur
    Event Planning
    Finance
    Financial Planning
    Fundraising/Development
    Game Design
    Graphic Design
    Health Services/Healthcare
    Horticulture
    Hotel/Restaurant/Hospitality
    Human Resources
    Information Management/MIS
    Interactive Media
    IT/Systems
    Law
    Library Science
    Management
    Marketing
    Not Specified
    Operations
    Other
    Political Organization/Lobbying
    Product Management
    Production
    Programming/Software Development
    Project Management
    Psychology
    Public Relations
    Quality Control/Assurance
    Reporting
    Research
    Risk Management/Assessment
    Sales
    Skilled Labor
    Social Work
    Supply Chain Management/Logistics
    Sustainability
    Tax
    Teaching/Education
    Technical Support
    Technician
    Therapy
    Training
    Urban and Regional Planning
    Volunteer
    Warehousing/Materials Management
    Web Design
    Web Development


Time Zone Options
-----------------

The supported options for time zones in Handshake are::

    "American Samoa"
    "International Date Line West"
    "Midway Island"
    "Hawaii"
    "Alaska"
    "Pacific Time (US & Canada)"
    "Tijuana"
    "Arizona"
    "Chihuahua"
    "Mazatlan"
    "Mountain Time (US & Canada)"
    "Central America"
    "Central Time (US & Canada)"
    "Guadalajara"
    "Mexico City"
    "Monterrey"
    "Saskatchewan"
    "Bogota"
    "Eastern Time (US & Canada)"
    "Indiana (East)"
    "Lima"
    "Quito"
    "Caracas"
    "Atlantic Time (Canada)"
    "Georgetown"
    "La Paz"
    "Santiago"
    "Newfoundland"
    "Brasilia"
    "Buenos Aires"
    "Greenland"
    "Montevideo"
    "Mid-Atlantic"
    "Azores"
    "Cape Verde Is."
    "Casablanca"
    "Dublin"
    "Edinburgh"
    "Lisbon"
    "London"
    "Monrovia"
    "UTC"
    "Amsterdam"
    "Belgrade"
    "Berlin"
    "Bern"
    "Bratislava"
    "Brussels"
    "Budapest"
    "Copenhagen"
    "Ljubljana"
    "Madrid"
    "Paris"
    "Prague"
    "Rome"
    "Sarajevo"
    "Skopje"
    "Stockholm"
    "Vienna"
    "Warsaw"
    "West Central Africa"
    "Zagreb"
    "Athens"
    "Bucharest"
    "Cairo"
    "Harare"
    "Helsinki"
    "Istanbul"
    "Jerusalem"
    "Kyiv"
    "Pretoria"
    "Riga"
    "Sofia"
    "Tallinn"
    "Vilnius"
    "Baghdad"
    "Kuwait"
    "Minsk"
    "Nairobi"
    "Riyadh"
    "Tehran"
    "Abu Dhabi"
    "Baku"
    "Moscow"
    "Muscat"
    "St. Petersburg"
    "Tbilisi"
    "Volgograd"
    "Yerevan"
    "Kabul"
    "Islamabad"
    "Karachi"
    "Tashkent"
    "Chennai"
    "Kolkata"
    "Mumbai"
    "New Delhi"
    "Sri Jayawardenepura"
    "Kathmandu"
    "Almaty"
    "Astana"
    "Dhaka"
    "Ekaterinburg"
    "Rangoon"
    "Bangkok"
    "Hanoi"
    "Jakarta"
    "Novosibirsk"
    "Beijing"
    "Chongqing"
    "Hong Kong"
    "Krasnoyarsk"
    "Kuala Lumpur"
    "Perth"
    "Singapore"
    "Taipei"
    "Ulaanbaatar"
    "Urumqi"
    "Irkutsk"
    "Osaka"
    "Sapporo"
    "Seoul"
    "Tokyo"
    "Adelaide"
    "Darwin"
    "Brisbane"
    "Canberra"
    "Guam"
    "Hobart"
    "Melbourne"
    "Port Moresby"
    "Sydney"
    "Yakutsk"
    "New Caledonia"
    "Solomon Is."
    "Vladivostok"
    "Auckland"
    "Fiji"
    "Kamchatka"
    "Magadan"
    "Marshall Is."
    "Wellington"
    "Chatham Is."
    "Nuku'alofa"
    "Samoa"
    "Tokelau Is."
    
Major Groups
------------

The following list of major groups is supported in Handshake. The categories are listed at the top level, with the major groups themselves underneath.

Arts and Design::

    Architecture
    Art History
    Design and Applied Arts
    Drama and Theatre Arts
    Fine and Studio Arts
    Graphic Design
    Industrial Design
    Interior Design
    Museum Studies
    Music and Music Education
    Photography
    Product Design/Packaging
    Textiles and Clothing

Business and Entrepreneurship::

    Accounting
    Actuarial/Risk Analysis
    Business Administration and Management
    Business Analytics
    Consulting
    Economics
    Entrepreneurship
    Finance and Financial Management
    Food Industry Management
    Human Resources
    Marketing
    Operations Management
    Parks, Recreation, and Leisure Studies
    Real Estate
    Retail and Hospitality Administration
    Sales
    Sport Business and Marketing
    Supply Chain Management

Communications::

    Advertising
    Communication and Media Studies
    Digital Communication
    Documentary/Film
    Journalism
    Public Relations
    Radio, Television, Media

Computer Science, Information Systems, and Technology::

    Computer Programming
    Computer Science
    Cyber Security
    Data Mining
    Information Systems Management
    Library Sciences
    Software Design
    User Experience/Social Computing

Education::

    Early Childhood Education
    Education Administration
    Elementary Education
    Health and Physical Education
    Language Arts Education
    Mathematics Education
    Secondary Education
    Special Education

Engineering::

    Aerospace Engineering
    Agriculture and Biological Engineering
    Biomedical Engineering
    Chemical Engineering
    Civil/Environmental Engineering
    Computer Engineering
    Construction Engineering & Management
    Electrical Engineering
    General Engineering
    Industrial Engineering
    Materials Science & Engineering
    Mechanical Engineering
    Nautical/Naval Engineering
    Network Engineering
    Nuclear Engineering

Health Professions::

    Athletic Training
    Communication Disorders Sciences and Services
    Dentistry
    Health/Exercise Science
    Health/Hospital Administration
    Kinesiology
    Medicine
    Movement Science
    Nursing
    Nutrition
    Pharmacy
    Physical/Occupational Therapy
    Public Health
    Speech Pathology

Social Sciences::

    Anthropology
    Cognition & Neuroscience/Biopsychology
    Counseling
    Family and Consumer Science
    Human and Child Development
    Psychology
    Social Work/Human Services
    Sociology

Civics and Government::

    Criminal Justice/Criminology
    Emergency Management/Homeland Security
    Forensics
    International Studies/Comparative Politics
    Law
    Political Science and Government
    Public Administration
    Public Policy
    Urban Planning

Humanities and Languages::

    Classical Studies
    Comparative Literature
    Creative Writing
    Cultural and Ethnic Studies
    English
    Foreign Languages and Literature
    Gender Studies
    History
    Linguistics
    Philosophy/Ethics
    Religious Studies/Divinity/Theology

Life Science::

    Animal Science
    Anthropology/Zoology
    Biology
    Ecology
    Epidemiology
    Genetics
    Immunology
    Marine Biology
    Microbiology
    Physiological Science

Math and Physical Sciences::

    Chemistry
    Physics
    Mathematics
    Statistics

Natural Resources, Sustainability and Environmental Science::

    Agriculture
    Cartography
    Conservation
    Earth Sciences
    Fisheries and Wildlife
    Forestry
    Geology/Mining
    Natural Resource Management
    Oceanography
    Plant Sciences/Horticulture
