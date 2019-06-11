# pull official base image
FROM python:3.7-alpine

# set work directory
WORKDIR /Users/manel/Dev/docker_django/app/

# set environment varibles
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2
RUN apk update \
    && apk add --virtual build-deps gcc python3-dev musl-dev \
    && apk add postgresql-dev \
    && pip install psycopg2 \
    && apk del build-deps

# install dependencies
RUN pip install --upgrade pip
RUN pip install pipenv
COPY ./Pipfile /Users/manel/Dev/docker_django/app/Pipfile
RUN pipenv install --skip-lock --system --dev

# copy entrypoint.sh
COPY ./entrypoint.sh /Users/manel/Dev/docker_django/app/entrypoint.sh

# copy project
COPY . /Users/manel/Dev/docker_django/app/

# run entrypoint.sh
ENTRYPOINT ["/Users/manel/Dev/docker_django/app/entrypoint.sh"]
