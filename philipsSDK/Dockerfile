# Start from deterministic ubuntu 18.04 image
FROM ubuntu:18.04@sha256:478caf1bec1afd54a58435ec681c8755883b7eb843a8630091890130b15a79af

ARG DEBIAN_FRONTEND=noninteractive

#install python, get linux packages, install python dependencies and then cleanup
RUN apt-get -y update \
    && apt-get install -y python3-pip python3-dev \
    && cd /usr/local/bin \
    && ln -s /usr/bin/python3 python \
    && pip3 install --upgrade pip \
    && apt-get -y install --no-install-recommends \
    libopenjp2-7-dev libopenjp2-tools \
    libtiff5-dev \
    openslide-tools \
    libgl1 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# install the sdk and remove it
COPY ./philips-pathologysdk-2.0-ubuntu18_04_py36_research /pathologysdk
WORKDIR /pathologysdk

RUN chmod 777 InstallPathologySDK.sh

RUN ./InstallPathologySDK.sh

WORKDIR /
RUN rm -r /pathologysdk

ENTRYPOINT [ "sh", "-c" ]