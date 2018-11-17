FROM docker/compose:1.19.0

RUN \
    mkdir -p meeting

COPY .env /meeting
COPY docker-compose.yml /meeting

RUN \
    cd meeting && \
    docker-compose up -d

EXPOSE 80 8443 8080

VOLUME /meeting