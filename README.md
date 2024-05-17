Setup instructions

Deployed version of the application:
The web application can be accessed from here: https://dmy2003.pythonanywhere.com/

Set up instructions:
To run the application locally, please refer to the following below:


1. Clone the repository from the GitHub.
2. Navigate into the folder and setup a local development environment using the following commands:
•	$ virtualenv venv
•	$ source venv/bin/activate
3. To install all required packages, run the following command:
   •	$ pip3 install -r requirements.txt If pip3 is not configured on your machine, then it needs to be installed with the following:
   •	$ sudo apt install python3-pip
4. In order to setup the database, run the following commands:
   •	$ python3 manage.py makemigrations
   •	$ python3 manage.py migrate And the database can be seeded with test data with:
   •	$ python3 manage.py seed Or if the database needs to be unseeded
   •	$ python3 manage.py unseed
5. To run your test suite to ensure that the application is working as intended, run:
   •	$ python3 manage.py test And the following commands can also be run to indicate how much of the application is being tested, i.e: how much of the code is executed during the tests.
   •	$ coverage run python3 manage.py •	$ coverage report

