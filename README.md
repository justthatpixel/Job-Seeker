# Team *GGs* Major Group project


## Project structure
The project is called `job_hiring`.  It currently consists of a single app `jobs` where all functionality resides.
Based off the academic project `2.3.A3: App for job hiring`


## Deployed version of the application
The deployed version of the application can be found at [dmy2003.pythonanywhere.com](https://dmy2003.pythonanywhere.com/).

## Installation instructions
To install the software and use it in your local development environment, you must first set up and activate a local development environment.  From the root of the project:

```
$ virtualenv venv
$ source venv/bin/activate
```

Install all required packages:

```
$ pip3 install -r requirements.txt
```

Migrate the database:

```
$ python3 manage.py migrate
```

Seed the development database with:

```
$ python3 manage.py seed
```

Run all tests with:
```
$ python3 manage.py test
```

*The above instructions should work in your version of the application.  If there are deviations, declare those here in bold.  Otherwise, remove this line.*

## Seeder
This application contains a seeder which can generate test data for you.
The seeder will generate both random data and pre-defined data.
There is a set number of predefined data you can't change, specified below.
However, you can change the number of randomly generated entities for each model from tne project settings file.
The default password for all seeded standard users is "Password123" but this can be changed in the settings file.
The default password for all seeded admin users is "Kanger00$" but this can also be changed in the settings file.
The data seeded includes:

#### Currencies
- 157 currencies with current exchange rates are generated
- Since this process involves an API, we excluded currencies from deletion during unseeding to reduce
the request traffic in future seeds.

#### Directors
- KELLY_BROWN = (firstname="Kelly", lastname="Brown", email="kelly.brown@example.org", password="Kanger00$")

#### Administrators
- BOBBY_FLOMP = (firstname="Bobby", lastname="Flomp", email="bobby.flomp@example.org, password="Kanger00$")
- TIM_TURNER = (firstname="Tim", lastname="Turner", email="tim.turner@example.org, password="Kanger00$")
- A number of other randomly generated admin. This number is specified in the project's settings file


#### Job Seekers
- JOHN_DOE = (firstname="John", lastname="Doe", email="john.doe@example.org", bio="Looking for work!", password="Password123")
- JANE_DOE = (firstname="Jane", lastname="Doe", email="jane.doe@example.org", bio="Lead Hiring Executive of Java", password="Password123")
- A number of other randomly generated job seekers. This number is specified in the project's settings file

#### Employers
- JAMES_JAMISON = (firstname="James", lastname="Jamison", email="james.jamison@example.org", company="Java Inc", password="Password123")
- JOSH_JONES = (firstname="Josh", lastname="Jones", email="josh.jones@example.org", company="Blue J Corporation", password="Password123")
- A number of other randomly generated employers. This number is specified in the project's settings file

#### Job Advertisements
- JAVA_DEVELOPER = (employer=JAMES_JAMISON, job_title="Java Developer", job_description=Develop complex software for our company using java", start_date=A_WEEK_FROM_DATE_DATA_SEEDED, salary=100, country = "United Kingdom",state ="England",city = "London",street = "112 Barkshlow street",postcode = "IG11 9UT", job_type="Full-time", hours=40, remote_work=False, website="https://docs.oracle.com/en/java/")
- C++_DEVELOPER = (employer=JAMES_JAMISON, job_title="C++ Developer", job_description="Work in a team to develop/improve software requested by our clients", start_date=A_WEEK_FROM_DATE_DATA_SEEDED, salary=200, country = "United Kingdom",state ="England",city = "London",street = "10 Lynford gardens",postcode = "IG3 9LY", job_type="Full-time", hours=45, remote_work=False, website="https://devdocs.io/cpp/")
- SCALA_DEVELOPER = (employer=JOSH_JONES, job_title="Scala Developer", job_description="Looking for an experienced scala developer to create software", start_date=A_WEEK_FROM_DATE_DATA_SEEDED, salary=70,  country = "United Kingdom",state ="England",city = "London",street = "25 marmion avenue",postcode = "E4 8EP", job_type="Part-time", hours=35, remote_work=False, website="https://docs.scala-lang.org/")
- SCRATCH_DEVELOPER = (employer=JOSH_JONES, job_title="Scratch Developer", job_description="Looking for a an experienced software developer with at least 10 years of experience working with scratch", start_date=A_WEEK_FROM_DATE_DATA_SEEDED, salary=150, country = "United Kingdom",state ="England",city = "London",street = "22a Chingford Avenue",postcode = "E17 EPG", job_type="Full-time", hours=40, remote_work=True, website="https://scratch.mit.edu/developers")
- A number of other randomly generated job advertisements. This number is specified in the project's settings file

#### Job Applications
- (advertisement=JAVA_DEVELOPER, job_seeker=JOHN_DOE, application_date=DATE_WHEN_DATA_WAS_SEEDED, status='Accepted')
- (advertisement=C++_DEVELOPER, job_seeker=JOHN_DOE, application_date=DATE_WHEN_DATA_WAS_SEEDED, status='Pending')
- (advertisement=SCALA_DEVELOPER, job_seeker=JOHN_DOE, application_date=DATE_WHEN_DATA_WAS_SEEDED, status='Rejected')
- (advertisement=SCRATCH_DEVELOPER, job_seeker=JOHN_DOE, application_date=DATE_WHEN_DATA_WAS_SEEDED, status='Pending')
- (advertisement=JAVA_DEVELOPER, job_seeker=JANE_DOE, application_date=DATE_WHEN_DATA_WAS_SEEDED, status='Pending')
- (advertisement=SCALA_DEVELOPER, job_seeker=JANE_DOE, application_date=DATE_WHEN_DATA_WAS_SEEDED, status='Pending')
- A number of other randomly generated job applications. This number is specified in the project's settings file

#### Job Advertisement Reports
- (reporter=JOHN_DOE, report_date=DATE_WHEN_WAS_DATA_SEEDED, report_group=JAVA_SPECIALIST_REPORT_GROUP, report_text="It didn't seem genuine to me")
- (reporter=JOHN_DOE, report_date=DATE_WHEN_WAS_DATA_SEEDED, report_group=JAVA_SPECIALIST_REPORT_GROUP, report_text="Looks suspicious")
- (reporter=JANE_DOE, report_date=DATE_WHEN_WAS_DATA_SEEDED, report_group=C++_ENTHUSIAST_REPORT_GROUP, report_text="Looks too good to be true")
- (reporter=JANE_DOE, report_date=DATE_WHEN_WAS_DATA_SEEDED, report_group=SCALA_ENJOYER_REPORT_GROUP, report_text=EMPTY_STRING)
- A number of other randomly generated job reports. This number is specified in the project's settings file
- Also note that a report group is a grouping of reports all reporting the same job advertisement. The user will never know about these and is purely there for the admin to see.
    Hence, there is no need to give seeder details of these, and you can assume a report group exists for an advertisement if it has been reported at least once.

#### Message channels
A message channel contains a number of users in the channel. Users can then send messages to this channel and see any messages in the channel.
 Note that we are seeding these channels with the last updated field set to twenty days before seeding. This is with the intention that when seeded messages are added to the channel they
 will overwrite this with the date of the most recent message sent to the channel
- (users={JOHN_DOE,JAMES_JAMISON}, last_updated=TWENTY_DAYS_BEFORE_DATE_WHEN_WAS_DATA_SEEDED)
- (users={JANE_DOE,JAMES_JAMISON}, last_updated=TWENTY_DAYS_BEFORE_DATE_WHEN_WAS_DATA_SEEDED)
- Other message channels will be generated with randomly generated messages between users

#### Messages between users
These messages will be part of the seeded channels above
- (message_text="Greetings John! I saw your application for our job posting and was looking to offer you an interview. Would you be free to come to the office tomorrow?", date=DAYS_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JAMES_JAMISON, message_channel=JAMES_JAMISON_JOHN_DOE_CHANNEL)
- (message_text="Hi James, that's great news! Yes I would love to come by tomorrow. Would I need to bring anything?", date=2_HOURS_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JOHN_DOE, message_channel=JAMES_JAMISON_JOHN_DOE_CHANNEL)
- (message_text="Just yourself and your CV", date=30_MINUTES_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JAMES_JAMISON, message_channel=JAMES_JAMISON_JOHN_DOE_CHANNEL)

- (message_text="Hi John, Unfortunately we\'re not hiring for the position you\'ve applied for anymore. However, we do have multiple other positions we could offer you if you\'re interested?", date=5_DAYS_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JOSH_JONES, message_channel=JOHN_DOE_JOSH_JONES_CHANNEL)
- (message_text="Hello Josh, unfortunately I\'ve accepted another position now. I appreciate the offer though", date=4_DAYS_AND_3_HOURS_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JOHN_DOE, message_channel=JOHN_DOE_JOSH_JONES_CHANNEL)
- (message_text="No worries John and all the best", date=2_DAYS_AND_20_MINUTES_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JOSH_JONES, message_channel=JOHN_DOE_JOSH_JONES_CHANNEL)


- (message_text="I'm interested in your recent posting for a worker", date=3_DAYS_AND_55_MINUTES_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JANE_DOE, message_channel=JAMES_JAMISON_JANE_DOE_CHANNEL)
- (message_text="What qualifications do you have?", date=1_DAY_AND_8_HOURS_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JAMES_JAMISON, message_channel=JAMES_JAMISON_JANE_DOE_CHANNEL)
- (message_text="2 years experience in Scala, 1 in Java and 5 in Scratch", date=20_MINUTES_BEFORE_DATE_OF_WHEN_DATA_WAS_SEEDED, sender=JANE_DOE, message_channel=JAMES_JAMISON_JANE_DOE_CHANNEL)

- A number of other randomly generated messages. This number is specified in the project's settings file

#### Notifications
- A message notification is generated for the receiver of the last message sent to each channel
- A message channel notification is generated for the receiver of the last message sent to each channel
- A job application status notification is generated for each applicant where the seeded job application status is not 'pending'




You can remove all seeded data (except the currencies) with the 'unseed' command.


## API

#### GEOAPIFY
- Used to normalise location data inputted in the job seeker criteria and advertisement creation forms.
- https://www.geoapify.com/

#### exchangerate.host
- Used to provide current exchange rates for currency conversions in the job matching process.
- https://exchangerate.host/

#### Google Maps API
- Used to display the location of a job in the advertisement preview.
- https://www.google.com/maps/


## Sources
The packages used by this application are specified in `requirements.txt`

- [Django custom authentication docs](https://docs.djangoproject.com/en/4.1/topics/auth/customizing/#authentication-backends)
- [Homepage](https://codepen.io/essentialenglish/pen/OJOzjVv)
- [JQuery](https://api.jquery.com/)
- [Ajax](https://api.jquery.com/Jquery.ajax/)
- [Animated icons (lordicon)](https://lordicon.com/)
- Logo for the website https://blog.hubspot.com/website/css-animation-examples
- Popup https://codepen.io/tt0113243/pen/mMJqma  
- Adblock detection  Author: AdGlare Ad Server (https://www.adglare.com)
