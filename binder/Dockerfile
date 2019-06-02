FROM ubuntu:18.04

RUN apt-get update && \
	  apt-get install curl git htop vim wget openjdk-8-jdk python3-pip -y && \
	  apt-get autoclean  -y && \
	  apt-get autoremove -y 

# nodejs 10
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - && \
apt-get install -y nodejs

# install the notebook package
RUN pip install --no-cache --upgrade pip && \
    pip install --no-cache notebook

# create user with a home directory
ARG NB_USER
ARG NB_UID
ENV USER ${NB_USER}
ENV HOME /home/${NB_USER}

RUN adduser --disabled-password \
    --gecos "Default user" \
    --uid ${NB_UID} \
    ${NB_USER}
WORKDIR ${HOME}
USER ${USER}
