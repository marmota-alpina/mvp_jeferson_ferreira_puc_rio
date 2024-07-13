FROM alpine:3.7 AS source

RUN apk add --no-cache git

WORKDIR /app

RUN git clone https://github.com/marmota-alpina/product-hub.git

FROM python:3.10-alpine3.20

LABEL Description="This image is used to build the product-hub service image"
LABEL Version="1.0"
LABEL Maintainer="marmota-alpina"

WORKDIR /app

COPY --from=source /app/product-hub /app

RUN pip install poetry

RUN poetry config virtualenvs.create false

RUN poetry install --no-dev

EXPOSE 8000

CMD ["python", "-m", "flask", "run", "--host", "0.0.0.0", "--port", "8000"]