FROM alpine:3.7 AS source

RUN apk add --no-cache git

WORKDIR /app

RUN git clone https://github.com/marmota-alpina/jedex_api.git

FROM python:3.10-slim

LABEL Description="This image is used to build the jedex_api image"
LABEL Version="1.0"
LABEL Maintainer="marmota-alpina"

WORKDIR /app

COPY --from=source /app/jedex_api /app

RUN pip install poetry

RUN poetry config virtualenvs.create false && poetry install --no-root

EXPOSE 8000

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
