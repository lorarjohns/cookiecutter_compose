FROM ubuntu:18.04
 
RUN apt-get update && apt-get install -y \
  git \
  python3.7 \
  python3-pip \
  python3.7-dev

RUN pip3 install --upgrade pip
RUN pip3 install --upgrade setuptools

# copy requirements.txt to container
# and install packages

COPY ./requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

# ARG UID
# RUN useradd docker -l -u $UID -s /bin/bash -m
# USER docker

COPY ./ /{{ cookiecutter.project_slug }}/

WORKDIR /{{ cookiecutter.project_slug }}

# CMD ["ubuntu:18.04", "-f", ""]
