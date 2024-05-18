################################
###    BUILD STAGE           ###
################################


FROM  node:16-alpine as build

WORKDIR /app


COPY package.json . 

RUN npm install

COPY . ./

RUN npm run build
################################
###    FINAL STAGE           ###
################################

FROM node:16-alpine 

WORKDIR /app

RUN npm install -g serve

COPY --from=build  /app  .

EXPOSE 3000

CMD [ "serve", "-s", "build"]  