FROM debian:bullseye

ENV DEBIAN_FRONTEND noninteractive

RUN apt update \
 && apt install -y \
        wget \
        gpg \
        ca-certificates \
 && mkdir -p /etc/apt/keyrings \
 && wget -O- https://opensky-network.org/files/firmware/opensky.gpg.pub | gpg --dearmor > /etc/apt/keyrings/opensky.gpg \
 && echo 'deb [signed-by=/etc/apt/keyrings/opensky.gpg] https://opensky-network.org/repos/debian opensky custom' > /etc/apt/sources.list.d/opensky.list

ARG DEBIAN_FRONTEND=noninteractive
ARG DEBCONF_NONINTERACTIVE_SEEN=true
COPY opensky_config /tmp/opensky_config
RUN debconf-set-selections /tmp/opensky_config

RUN apt update \
 && apt install -y \
        opensky-feeder \
 && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["openskyd-dump1090"]
