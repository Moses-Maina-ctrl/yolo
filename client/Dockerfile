################################
###    BUILD STAGE           ###
################################


FROM  node:13.12-alpine as build

WORKDIR /app


COPY package.json . 

RUN npm install

COPY . ./

################################
###    FINAL STAGE           ###
################################

FROM node:13.12-alpine 

COPY --from=build  /app  .

EXPOSE 3000

CMD [ "npm", "start" ]  