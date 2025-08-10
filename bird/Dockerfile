FROM debian:12.11-slim@sha256:2424c1850714a4d94666ec928e24d86de958646737b1d113f5b2207be44d37d8
ARG APP_VERSION

LABEL org.opencontainers.image.version=${APP_VERSION} \
      org.opencontainers.image.title="bird" \
      org.opencontainers.image.description="BIRD is an (not only) IP routing daemon." \
      org.opencontainers.image.licenses="GPL-2.0-or-later" \
      org.opencontainers.image.authors="Frédéric Arroyo" \
      org.opencontainers.image.vendor="Frédéric Arroyo"

RUN useradd -u 1001 app \
  && apt update \
  && apt -y install apt-transport-https ca-certificates wget \
  && wget -O /usr/share/keyrings/cznic-labs-pkg.gpg https://pkg.labs.nic.cz/gpg \
  && echo "deb [signed-by=/usr/share/keyrings/cznic-labs-pkg.gpg] https://pkg.labs.nic.cz/bird3 bookworm main" > /etc/apt/sources.list.d/cznic-labs-bird3.list \
  && apt -y update \
  && apt -y install bird3=${APP_VERSION} \
  && apt -y upgrade \
  && apt -y clean \
  && apt -y autoremove \
  && mkdir /app /app/run /app/config /app/log \
  && chown -R app:app /app

WORKDIR /app
USER app
ENTRYPOINT [ "bird",  "-P", "/app/run/bird.pid", "-s", "/app/run/bird.ctl", "-c", "/app/config/bird.conf", "-f" ]
