# Pull python base image.
FROM python:3.8.0-alpine

# Create a directory to store our application files.
RUN mkdir -p /usr/src/django
WORKDIR /usr/src/django

# Install dependencies.
RUN apk update \
    && apk add postgresql-dev gcc python3-dev musl-dev

# Use pipenv to install python dependencies.
# The --system flag is used because an extra virtual environment is not required.
COPY Pipfile Pipfile.lock  /usr/src/django/
RUN pip install --upgrade pip
RUN pip install pipenv && pipenv install --system

# Copy project code.
COPY . /usr/src/django/

# CMD ["gunicorn", "--chdir", "application", "--bind", ":80", "application.wsgi:application"]