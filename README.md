# LAB - Class 34

## Project: Django REST Framework Authentication & Production Server

### Author: Katrina Hill

- attribution to instructor JB Tellez for class demo code modified for this application

### api-quick-start

Template Project for starting up CRUD API with Django Rest Framework

### Customization Steps

- DO NOT migrate yet
- add additional dependencies as needed
  - Re-export requirements.txt as needed
- change `things` folder to the app name of your choice
- Search through entire code base for `Thing`,`Things` and `things` to modify code to use your resource
  - `project/settings.py`
  - `project/urls.py`
  - App's files
    - `views.py`
    - `urls.py`
    - `admin.py`
    - `serializers.py`
    - `permissions.py`
- Update ThingModel with fields you need
  - Make sure to update other modules that would be affected by Model customizations. E.g. serializers, tests, etc.
- Rename `project/.env.sample` to `.env` and update as needed
- Run makemigrations and migrate commands
- Optional: Update `api_tester.py`

### How to initialize/run the application

- create repo from template
- clone repo to local machine
- docker compose up
- rename .env.sample to .env
- docker-compose run web bash
- copy from python command to generate a secrety key from the assignment instructions to the terminal
- paste the generated secret key from the terminal into .env for SECRET_KEY
- exit the container
- change the name of the `things` app folder to `cookie_stands`
- Look in each file, where applicable, change `Thing` to `CookeStand`, `things` `cookie_stands`
- docker-compose run web bash
- python manage.py showmigrations
- python manage.py make migrations cookie_stands
- python manage.py showmigrations
- python manage.py migrate
- python manage.py createsuperuser (create a username, password, and email address)
- exit
- docker compose up or docker compose up --build
- open localhost/development server to ensure site set up properly
- brew install httpie OR pip install httpie (if not already installed)
- go to ElephantSQL website and create a new instance
- add instance environmental variables to settings.py
- uncomment environmental variables in settings.py
- docker compose down
- docker compose up --build
- in another terminal, docker compose run web bash
- pip install psycopg2-binary
- pip freeze > requirements.txt
- exit
- docker compose up build
- docker compose run web bash
- python manage.py showmigrations
- python manage.py migrate
- go to Elephant and click on Browser
- select cookie_stands_cookiestand (public) (0 KiB, ~0 rows)
- execute
- in docker container, python manage.py createsuperuser
- exit
- docker compose up
- go to open local host site and refresh
- click Log in
- make an entry
- post
- go to ElephantSQL to see if the added snack shows up
- execute
- docker compose down
- heroku apps:create snacks-api-401d18
- type cookie-stand-api-katrina-hill
- heroku stack:set container
- add, commit, push to branch then merge to main in GitHub
- git push heroku main
- log in to Heroku
- click on the project
- go to settings, Reveal Config Vars
- copy the environmental variables from settings.py into Reveal Config Vars
- refresh heroku website (if this doesn't work, type heroku restart in the terminal)
- if CSRF error, add to bottom of settings.py file, (CSRF_TRUSTED_ORIGINS = ["https://cookie-stand-api-katrina-hill.herokuapp.com"]
- add, commit, push to branch then merge to main in GitHub
- git push heroku main

### Thunder Client process

- click New Request
- in dropdown, select GET
- type <http://0.0.0.0:8000/api/v1/cookie_stands>
- click on Body, then JSON
- type in the Json Content window: ```{
    "id": 1,
    "location": "Houston",
    "description": "Great town.",
    "hourly_sales": [
        "$10",
        "$15",
        "$20"
    ],
    "minimum_customers_per_hour": 5,
    "maximum_customers_per_hour": 10,
    "average_cookies_per_sale": 6.0,
    "owner": 1
}

```
- click Send
- In the Response window, you should see two food entries that were created in the the production server

### How to run the tests

- import class Food
- import APITestCase
- type python manage.py test

- tests were provided from instructor JB Tellez in class demo code

### How to view deployed sites

Vercel deployed site: https://cookie-stand-admin-katrina-hill.vercel.app/

Heroku deployed site: https://cookie-stand-api-katrina-hill.herokuapp.com/
- type api/v1/cookie_stands/ after the base url to see the Cookie Stand List
