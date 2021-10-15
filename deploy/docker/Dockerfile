# Docker image for the primary terria map application server
FROM node

RUN apt-get update && apt-get install -y gdal-bin

RUN mkdir -p /usr/src/app && mkdir -p /etc/config/client
WORKDIR /usr/src/app/component
COPY . /usr/src/app

RUN sed -i 's!http://localhost:5000!https://api.dtpoc.knowit.no!g' wwwroot/init/ByPythonServer.json
# COPY ./packages /usr/src/app/node_modules
# RUN rm wwwroot/config.json && ln -s /etc/config/client/config.json wwwroot/config.json

EXPOSE 3001

CMD [ "node", "./node_modules/terriajs-server/lib/app.js", "--config-file", "devserverconfig.json" ]
