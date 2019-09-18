FROM ubuntu:18.04

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
EXPOSE 3306
EXPOSE 8888
EXPOSE 8080

ARG UID
RUN useradd docker -l -u $UID -s /bin/bash -m
USER docker

# set the working directory
WORKDIR /work

CMD ["ubuntu:18.04", "-f", ""]
