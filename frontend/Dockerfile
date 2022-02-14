# from base image node
FROM node:12.18.3

RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

# copying all the files from your file system to container file system
COPY ./frontend/package.json ./
COPY ./frontend/ .

# install all dependencies
RUN npm install
EXPOSE 3000
CMD [ "npm", "start"]

#docker build -f Dockerfile -t frontend .
#docker run -it -p 4001:3000 frontend