# pyconsg-workshop-cookiecutter-django

:cookie: Welcome to the cookicutter-django workshop!

> What is the best practice for XXX in Django?
> How can I enable HTTPS for Django
> What is the recommendation project structure for Django?
> How to integration Docker with Django?

If you ever ask yourself asking these questions, cookiecutter-django is the right answer for you.

![cookiecutter](https://camo.githubusercontent.com/c2095c350e36abaafd738dcdc6cdc9e7d585d69e/68747470733a2f2f7261772e6769746875622e636f6d2f617564726579722f636f6f6b69656375747465722f336163303738333536616466356131613732303432646665373265626661346139636435656633382f6c6f676f2f636f6f6b69656375747465725f6d656469756d2e706e67)

cookiecutter: https://github.com/audreyr/cookiecutter

## Pre-requisites

* Git
* Docker
* Github account
* Text editor or IDE (e.g. VSCode or PyCharm)

## Workshop

Docker is an extremely useful tool to speed up the development and deployment cycle. We will use Docker throughout this workshop. It is available for all the major platforms. When if doubt, please reach out to the workshop conductor.

* Install Docker
for [Mac](https://docs.docker.com/docker-for-mac/install/) or [Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows)

* Install cookiecutter CLI 

cookicutter is a great tool developed by Audrey to quickly create a project based on some templates. In this workshop, we will use the [cookiecutter-django](https://github.com/pydanny/cookiecutter)) template which is specically baked with Django best practices.

```bash

# for Mac
$ brew install cookiecutter

# or generally
$ pip install cookiecutter
```

* Createa a new Django project using cookiecutter

Later you will be asked a series of questions. Based on your answer, a customerized project will be generated. For the purpose of this workshop, you may use the follow answer as a guide.

```bash
# Here cookiecutter CLI is taking the first parameter as the template source
# In this example, it's a Github repo and cookiecutter will use the latest master at this 
# point of time. The following questions may vary depending on when you run the command 

$ cookiecutter https://github.com/pydanny/cookiecutter-django

project_name [My Awesome Project]: my-favorite-cookie (or whatever cool name you like)
project_slug [my_favorite_cookie]: my_favorite_cookie (or whatever cool name you like)
description [Behold My Awesome Project!]: this is my favorite cookie 
author_name [Daniel Roy Greenfeld]: Your name
domain_name [example.com]: enter
email [wan-liuyang@example.com]: your email
version [0.1.0]: enter
Select open_source_license:
1 - MIT
2 - BSD
3 - GPLv3
4 - Apache Software License 2.0
5 - Not open source
Choose from 1, 2, 3, 4, 5 [1]: 1
timezone [UTC]: enter
windows [n]: Choose accordingly
use_pycharm [n]: n
use_docker [n]: y (Important!)
Select postgresql_version:
1 - 10.3
2 - 10.2
3 - 10.1
4 - 9.6
5 - 9.5
6 - 9.4
7 - 9.3
Choose from 1, 2, 3, 4, 5, 6, 7 [1]: 4 (Important!)
Select js_task_runner:
1 - None
2 - Gulp
Choose from 1, 2 [1]: 1
custom_bootstrap_compilation [n]: n
use_compressor [n]: n
use_celery [n]: n
use_mailhog [n]: y
use_sentry [n]: n
use_whitenoise [n]: n
use_heroku [n]: y
use_travisci [n]: y
keep_local_envs_in_vcs [y]: y
debug [n]: n
 [SUCCESS]: Project initialized, keep up the good work!
```

That's it. You now have a production-ready Django project.

## Run the project using Docker

```
# Make sure docker and docker-compose are installed correctly
$ docker version
$ docker-compose version

# Navigate to the project
$ cd my_favorite_cookie # change to your project name

# Build docker image using docker-compose
# This step will probably take a while, depending on your network. Grab a coffee if you like.
# This will install all the dependencies required to run the project
# like your database, your OS dependenceis, your requirements.txt and etc.
$ docker-compose -f local.yml build

# Run the docker image we just built 
# This will run your migrations and trigger the python manage.py runserver
$ docker-compose -f local.yml up
```

* Github OAuth login
* Deploy to heroku
* (Optional) Make it HTTPS
