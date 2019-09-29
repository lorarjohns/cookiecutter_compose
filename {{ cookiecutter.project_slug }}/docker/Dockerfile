FROM ubuntu:18.04

USER root
 
RUN apt-get update && apt-get install -y \
  git \
  python3.7 \
  python3-pip \
  python3.7-dev

# make virtual directory
SHELL ["/bin/sh", "-lc"]
RUN mkdir -p /{{ cookiecutter.project_slug }}

RUN pip3 install --upgrade pip
RUN pip3 install --upgrade setuptools

# copy requirements.txt to container
# and install packages

COPY ./requirements.txt /{{ cookiecutter.project_slug }}/requirements.txt
RUN yes | pip install -r /{{ cookiecutter.project_slug }}/requirements.txt

RUN pip install https://github.com/explosion/spacy-models/releases/download/en_core_web_sm-2.1.0/en_core_web_sm-2.1.0.tar.gz#egg=en_core_web_sm
RUN pip install https://github.com/explosion/spacy-models/releases/download/en_core_web_md-2.1.0/en_core_web_md-2.1.0.tar.gz#egg=en_core_web_md
RUN pip install https://github.com/explosion/spacy-models/releases/download/en_core_web_lg-2.1.0/en_core_web_lg-2.1.0.tar.gz#egg=en_core_web_lg

COPY ./ ./ 

WORKDIR ./



