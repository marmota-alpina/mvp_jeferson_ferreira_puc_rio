FROM alpine:3.7 AS source

RUN apk add --no-cache git

WORKDIR /app

RUN git clone https://github.com/marmota-alpina/product-hub-ui.git

FROM node:20.12.2-alpine AS build

WORKDIR /app

COPY --from=source /app/product-hub-ui /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build --prod

FROM nginx:alpine

COPY --from=build /app/dist/product-hub/* /usr/share/nginx/html

COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

# Comando para iniciar o NGINX
CMD ["nginx", "-g", "daemon off;"]
