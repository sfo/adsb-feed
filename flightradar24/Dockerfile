FROM debian:bullseye

RUN apt update \
 && apt install -y \
        wget \
 && rm -rf /var/lib/apt/lists/*

RUN wget -O - http://repo.feed.flightradar24.com/rpi_binaries/fr24feed_1.0.34-0_armhf.tgz | tar xzf - -C /bin --strip 1

COPY fr24feed.ini /etc/fr24feed.ini

ENTRYPOINT ["fr24feed"]
