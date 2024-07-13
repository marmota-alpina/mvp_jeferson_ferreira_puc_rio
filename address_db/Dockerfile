FROM alpine:3.7 AS source

RUN apk add --no-cache git

WORKDIR /app

RUN git clone https://github.com/marmota-alpina/address_service.git

RUN ls -la /app/address_service/db/backups

RUN cd /app/address_service/db/backups && cat part_* > /app/002_backup.sql

FROM postgres:latest

COPY --from=source /app/002_backup.sql /docker-entrypoint-initdb.d/002_backup.sql
