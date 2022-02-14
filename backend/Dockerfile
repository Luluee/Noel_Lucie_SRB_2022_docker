FROM node:12.18.3

RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

COPY ./backend/package.json ./
COPY ./backend/ .

RUN npm install
EXPOSE 8080
CMD [ "npm", "start"]