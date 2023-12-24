# DJANGO_SCHEDULE_JOBS_

Hi there.
this is Django app with celery and flower to monitor and redis as massege brocker and postres as  a database on docker on localhost will you get up and running quickly

### Local Development Setup

1. Clone this repo `https://github.com/bobby-didcoding/did_django_schedule_jobs_v2.git`
2. Create your .env file from the template file `cp .env.template backend/.env`

### Install Redis for Celery 

1. create a username (must be an email) & password
2. Now create redis repository `sudo apt-add-repository ppa:redislabs/redis`
3. Now update and upgrade packages `sudo apt-get update` then `sudo apt-get upgrade`
4. Now install Redis `sudo apt-get install redis-server`
   
### Config

1. Create a `.env` file from the `.env.template` and fill-in the environment variables specific to your setup (eg. DB
   name, user and password) - Save this into `/backend`
2. Set up a virtual environment `cd backend && python -m venv env`
3. Activate virtual environment `source /env/bin/activate`
4.  Install dependencies for your local environment by running `pip install -r requirements/Base.txt`
5.  Run `python manage.py migrate`

### Fire up servers
1. Open Ubuntu terminal and fire up a Redis server `redis-server`
2. Open another Ubuntu and set up a Redis CLI `redis-cli`
3. Open new cmd in root and use this command `celery -A did_django_schedule_jobs_v2.celery beat -l INFO`to fire up celery beat
4. Open new cmd in root and use this command `celery -A did_django_schedule_jobs_v2.celery worker --pool=solo -l info` to fire up a celery worker
5. Run `python manage.py runserver`

### Local Development Setup with Docker
1. Create an env file `cp .env.template .env`
2. Install Docker & Docker compose
3. Compose a docker image `docker-compose -f docker-compose.yml up -d --build`


