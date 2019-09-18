# build an image
{%- if cookiecutter.use_nvidia_docker == 'yes' -%}
FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04
{%- else -%}
FROM ubuntu:18.04
{%- endif %}

# set the working directory
WORKDIR /{{ cookiecutter.project_slug }}/work

COPY . .

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
EXPOSE 4000

ARG UID
RUN useradd docker -l -u $UID -s /bin/bash -m
USER docker

ENTRYPOINT ["/bin/bash"]
