FROM alpine:3.7 AS source

RUN apk add --no-cache git

WORKDIR /app

RUN git clone https://github.com/marmota-alpina/address-service.git

FROM python:3.10-alpine3.20

LABEL Description="This image is used to build the address-service image"
LABEL Version="1.0"
LABEL Maintainer="marmota-alpina"

WORKDIR /app

COPY --from=source /app/address-service /app

RUN pip install poetry

RUN poetry config virtualenvs.create false

RUN poetry install --no-dev

EXPOSE 8000

CMD ["poetry", "shell", "run", "uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]