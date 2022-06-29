# Start from deterministic ubuntu 20.04 image
FROM ubuntu:20.04@sha256:626ffe58f6e7566e00254b638eb7e0f3b11d4da9675088f4781a50ae288f3322

ARG DEBIAN_FRONTEND=noninteractive

#install python, get linux packages, install python dependencies and then cleanup
RUN apt-get -y update \
    && apt-get install -y python3-pip python3-dev \
    && cd /usr/local/bin \
    && ln -s /usr/bin/python3 python \
    && pip3 install --upgrade pip

# install the sdk and remove it
COPY ./philips-pathologysdk-2.0-L1-ubuntu20_04_py38_research /pathologysdk
WORKDIR /pathologysdk

RUN chmod 777 InstallPathologySDK.sh && ./InstallPathologySDK.sh -y

WORKDIR /
RUN rm -r /pathologysdk

RUN apt-get install -y libtiff5-dev --no-install-recommends \    
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT [ "sh", "-c" ]