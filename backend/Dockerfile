# from base image node
FROM node:12.18.3

RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

# copying all the files from your file system to container file system
COPY ./backend/package.json ./
COPY ./backend/ .

# install all dependencies
RUN npm install
EXPOSE 8080
CMD [ "npm", "start"]

#docker build -f Dockerfile -t backend .
#docker run -it backend