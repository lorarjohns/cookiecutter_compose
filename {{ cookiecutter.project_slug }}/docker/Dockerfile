FROM ubuntu:18.04

USER root

RUN mkdir -p /work/

RUN apt-get update && apt-get install -y \
  git \
  python3-pip \
  python3-dev

RUN pip3 install --upgrade pip
RUN pip3 install --upgrade setuptools

# copy requirements.txt to container
# and install packages

COPY requirements.txt /work/requirements.txt
RUN pip3 install -r /work/requirements.txt

RUN pip3 install https://github.com/explosion/spacy-models/releases/download/en_core_web_sm-2.1.0/en_core_web_sm-2.1.0.tar.gz#egg=en_core_web_sm
RUN pip3 install https://github.com/explosion/spacy-models/releases/download/en_core_web_md-2.1.0/en_core_web_md-2.1.0.tar.gz#egg=en_core_web_md
RUN pip3 install https://github.com/explosion/spacy-models/releases/download/en_core_web_lg-2.1.0/en_core_web_lg-2.1.0.tar.gz#egg=en_core_web_lg

COPY ./ /work/

WORKDIR /work/



