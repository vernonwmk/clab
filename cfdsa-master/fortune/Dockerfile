#docker build
FROM node:latest

#environment variables
ENV APP_PORT=5000 APP_DIR=/fortune

#cd into directory
WORKDIR ${APP_DIR}

#copy files
ADD main.js .
ADD package.json .
#copy dir
ADD public public
ADD views views

#install libraries from package.json
RUN npm install

#docker run
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=60s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

ENTRYPOINT [ "node", "main.js" ]

