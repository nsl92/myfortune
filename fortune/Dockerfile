FROM node:latest

# Set envrionment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000

# create the directory and cd into in
WORKDIR ${APP_ROOT}

# files will be copied into /app
# Copy files into the image
ADD main.js .
ADD package.json .
ADD public public
ADD views views

# run some command
RUN npm install

# how an image is provision/run

# what port our container will be exposing
EXPOSE ${APP_PORT}

#add health chceu to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
	CMD curl -f https://localhost:${APP_PORT}/health > /dev/null || exit 1


ENTRYPOINT ["node", "main.js"]
