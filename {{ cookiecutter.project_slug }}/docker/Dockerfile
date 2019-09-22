FROM ubuntu:18.04
 
RUN apt-get update && apt-get install -y \
  git \
  python3.7 \
  python3-pip \
  python3.7-dev

RUN pip install --upgrade pip
RUN pip install --upgrade setuptools

# copy requirements.txt to container
# and install packages

COPY ./requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

COPY ./ /{{ cookiecutter.project_slug }}/

WORKDIR /{{ cookiecutter.project_slug }}

