# pull official base image
FROM python:3.8.5-alpine

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

COPY ./requirements.txt .

# install dependencies
RUN apk update && \ 
  apk add --no-cache --virtual .build-deps \
  gcc \
  musl-dev \
  python3-dev \
  postgresql-dev \
  libxml2 \
  libxml2-dev && \
  pip3 install --upgrade pip && \
  pip3 install --no-cache-dir -r requirements.txt && \
  apk del .build-deps

# copy project
COPY . .

RUN apk --no-cache add libpq
