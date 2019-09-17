# build an image
{%- if cookiecutter.use_nvidia_docker == 'yes' -%}
FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04
{%- else -%}
FROM ubuntu:18.04
{%- endif %}

RUN apt-get update && apt-get install -y \
  git \
  python3.7 \
  python3-pip \
  python3.7-dev

RUN pip3 install --upgrade pip

# copy requirements.txt to container
# and install packages

COPY ./requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

ARG UID
RUN useradd docker -l -u $UID -s /bin/bash -m
USER docker

# set the working directory
WORKDIR /work

ENTRYPOINT ["/bin/bash"]
