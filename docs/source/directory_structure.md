## Directory Structure

### Django Apps

EvalAI is a Django-based application. Hence, it leverages the concept of Django apps to properly namespace the functionalities. All the apps can be found in the `apps` directory situated in the root folder.

Some important apps along with their main uses are:

* **Challenges**

This app handles all the workflow related to creating, modifying, and deleting the challenges.

* **Hosts**

This app is responsible for providing the functionalities to the challenge hosts/organizers.

* **Participants**

This app serves for users who would like to take part in any of the challenges. It contains code for creating a Participant Team, through which they can participate in any challenge.

* **Jobs**

This is one of the most important apps.it is responsible for processing and evaluating the submissions made by the participants. It contains code for creating a submission, changing the visibility of the submission and populating the leaderboard for any challenge.

* **Web**

This app serves some of the basic functionalities like providing support for contact us or adding a new contributor to the team, etc.

* **Accounts**

As the name indicates, this app deals with storing and managing the data related to user's accounts.

* **Base**

It is a placeholder app which contains the code that is used across various other apps.


### Settings

Settings are used across the backend codebase by Django to provide config values on a per-environment basis. Currently, the following settings are available:

* **dev**

Used in developmentof the environment

* **testing**

Used whenever test cases are runned

* **staging**

Used on a staging server

* **production**

Used on a production server

### URLs

The base URLs for the project are present in `evalai/urls.py`. This file includes URLs of various applications, which can also be namespaced by the app name. So URLs for the `challenges` app will have its app namespace in the URL as `challenges`. This actually helps us separate our API based on the app.


### Frontend

The whole codebase for the frontend resides in a folder named `frontend` in the root directory.


### Scripts

Scripts contains various helper scripts, utilities and python workers. It also contains the following folders:

* **migration**

 This contains some of the scripts which are used for one-time migration or formatting of data.

* **tools**

A folder for storing helper scripts, e.g. a script to fetch pull request

* **workers**

One of the main directories,  contains the code for submission worker. Submission worker is a normal python worker which is responsible for processing and evaluating the submission of a user. The command used to start a worker is:

```
python scripts/workers/submission_worker.py
```

### Test Suite

All of the codebases are related to testing resides in `tests` folder in the root directory. In this directory, tests are namespaced according to their app, e.g. tests for `challenges` app lives in a folder named `challenges`.

### Management Commands

To perform certain actions like seeding the database, we use Django management commands. Since the management commands are common throughout the project, they are present in `base` application directory. At a moment, the only management command is `seed`, which is used to populate the database with some random values. The command can be invoked by calling.

```
python manage.py seed --settings=settings.dev
```
