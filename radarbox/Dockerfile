FROM debian:bullseye

RUN apt update \
 && apt install -y \
        gpg \
        ca-certificates \
 && mkdir -p /etc/apt/keyrings \
 && gpg --keyserver hkps://keyserver.ubuntu.com --recv-keys 1D043681 \
 && gpg --export 1D043681 > /etc/apt/keyrings/rb24.gpg \
 && echo 'deb [signed-by=/etc/apt/keyrings/rb24.gpg] https://apt.rb24.com/ bullseye main' > /etc/apt/sources.list.d/rb24.list \
 && apt update \
 && apt install -y \
        rbfeeder \
 && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["sh", "-c", "rbfeeder --set-network-mode on --set-network-host ${DUMP1090_HOST} --set-network-port ${DUMP1090_PORT} --set-network-protocol beast"]
