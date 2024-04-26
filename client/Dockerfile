FROM node:22-alpine3.18

WORKDIR /app


COPY package*.json /. 

RUN npm install

COPY . .

RUN npm start

EXPOSE 3000