FROM node

RUN mkdir /opt/parse

COPY . /opt/parse
WORKDIR /opt/parse
RUN npm install -g parse-server

EXPOSE 4040  

CMD ["ls"]
