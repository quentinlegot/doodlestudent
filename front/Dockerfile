FROM ubuntu:22.04 as builder

RUN apt update -y && apt install curl -y

RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - && apt update -y && apt install -y nodejs

WORKDIR /opt/app

COPY . .


RUN npm ci
RUN npm run build --prod

FROM nginx:latest as runner

EXPOSE 80

COPY nginx.conf /etc/nginx/nginx.conf

COPY --from=builder /opt/app/dist/tlcfront /usr/share/nginx/html

