FROM node:12.18.3

RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

COPY ./frontend/package.json ./
COPY ./frontend/ .

RUN npm install
EXPOSE 3000
CMD [ "npm", "start"]