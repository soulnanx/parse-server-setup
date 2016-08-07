FROM node

RUN mkdir /opt/parse

COPY . /opt/parse
WORKDIR /opt/parse
RUN npm install -g parse-dashboard

EXPOSE 4040  

CMD ["ls"]
