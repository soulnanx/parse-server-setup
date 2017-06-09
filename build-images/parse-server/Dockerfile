FROM node:6.3.1
USER root
RUN mkdir /opt/parse

COPY . /opt/parse
WORKDIR /opt/parse
RUN npm install -g parse-server

EXPOSE 1337  

CMD ["ls"]
