FROM python:3.9-slim

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1
ENV PIP_NO_CACHE_DIR off

RUN apt-get update && apt-get install -y --no-install-recommends --no-install-suggests build-essential libpq-dev python3-dev  netcat-openbsd  netcat-traditional gettext && pip install --no-cache-dir --upgrade pip

WORKDIR /code
RUN mkdir /requirements
COPY ./requirements/Base.txt /code/requirements/Base.txt

RUN pip install --no-cache-dir -r /code/requirements/Base.txt

COPY . /code

RUN touch /code/logs/celery.log
RUN chmod +x /code/logs/celery.log    

RUN chmod +x /code/entrypoint.sh
ENTRYPOINT ["/code/entrypoint.sh"]