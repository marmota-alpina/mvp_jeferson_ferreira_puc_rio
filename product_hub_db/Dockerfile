FROM alpine:3.7 AS source

RUN apk add --no-cache git

WORKDIR /app

RUN git clone https://github.com/marmota-alpina/product-hub.git


RUN cp /app/product-hub/docker/db/init_db.sql /app/001_init_db.sql

FROM postgres:latest

COPY --from=source /app/001_init_db.sql /docker-entrypoint-initdb.d/
