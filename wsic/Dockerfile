FROM python:3.9-slim-bullseye@sha256:980b778550c0d938574f1b556362b27601ea5c620130a572feb63ac1df03eda5
ENV input=''
ENV output=''

WORKDIR /data
COPY ./requirements.txt .

#get linux packages
RUN apt-get -y update && apt-get -y install --no-install-recommends \
    libopenjp2-7-dev libopenjp2-tools \
    openslide-tools \
    libgl1 \
    build-essential \
    && pip3 install --no-cache-dir -r requirements.txt \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT [ "sh", "-c" ]
CMD ["wsic convert -i ${input} -o ${output} -rt 4096 4096 -w 4 --no-ome --overwrite -to 60"]