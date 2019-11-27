FROM node:latest

ENV APP_ROOT=/app APP_PORT=3000 DB_HOST=localhost DB_PORT=3306 DB_USER=root DB_PASSWORD=changeit
#ENV MYSQL_ROOT_PASSWORD=changeit MYSQL_DATABASE=northwind 

#create APP_ROOT
WORKDIR ${APP_ROOT}

#copy files into the image
ADD main.js .
ADD package.json .
ADD config config
ADD public public
ADD views views

# install the dependencies
RUN npm install

#ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
#ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

EXPOSE ${APP_PORT}
HEALTHCHECK --interval=60s --timeout=5s --retries=3 \
        CMD curl -f https://localhost:${APP_PORT}/health > /dev/null || exit 1

ENTRYPOINT ["node", "main.js"]


